In a distributed computer system, you can only support two of the following guarantees:

1. **Consistency,** 
2. **Availability,**
3. **Partition Tolerance**

_Networks aren't reliable, so most distributed systems must tolerate network failures. 
Therefore, you'll need to support partition tolerance._

This mean you need to make a choice between consistency and availability when a network partition occurs.
#### Consistency
Every read request receives the most recent write or an error when consistency can't be guaranteed. A service that is consistent operates fully or not at all. (Atomic!)

Data is always the same across the cluster, so you can read/write from/to any node and get the same data.

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ff6cda484-672c-4009-9cda-69a8e36e95a3_1166x932.png)

>In a consistent distributed system, if you write data to node A, a read operation from node B will immediately reflect the write operation on node A.
#### Availability
Every request (read or write) receives a non-error response, even when nodes are down or unavailable. 

Availability means the ability to access the cluster even if a node in the cluster goes down.

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4d8ccf80-2bee-4ff6-8cc4-005a418da7ae_1188x868.png)

>This means that the system remains **operational** and **responsive**, even if the response from some of the nodes don’t reflect most up-to-date data.
#### Partition Tolerance
Partition Tolerance means that the **system continues to function despite network partitions** where nodes cannot communicate with each other.

Partition tolerance means that the cluster continues to function even if there is a "partition" (communication break) between two nodes (both nodes are up, but can't communicate).

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F73a83347-71c5-4d8f-9487-ff41b5bc1333_844x858.png)

> A **network partition** occurs when a network failure causes a distributed system to split into two or more groups of nodes that cannot communicate with each other.

## Tradeoffs

No distributed system is safe from network failures, thus network partitioning generally must be tolerated. In the presence of a network partition, one must choose between consistency or availability.

Consider if you have two nodes, X and Y, in a master-master setup. Now, there is a break between network communication between X and Y, so they can't sync updates. 

At this point you can either:
1. Allow the nodes to get out of sync (giving up consistency)
2. Consider the cluster to be "down" (giving up availability)

![220px-CAP_Theorem_Venn_Diagram.png](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c6/CAP_Theorem_Venn_Diagram.png/220px-CAP_Theorem_Venn_Diagram.png)
#### CP - Consistency and Partition Tolerance

When choosing consistency over availability, the system will return an error if data cannot be guaranteed to be consistent between all nodes due to network partitioning.

CP is a good choice if your business needs require atomic reads and writes.

>**Banking systems** typically prioritize **consistency over availability** since data accuracy is more critical than availability during network issues.
#### AP - Availability and Partition Tolerance

When choosing availability over consistency, the system will always return a response, but with potentially inconsistent data. 

A workload that prioritizes availability will process the query and try to return the most recent available version of the information on any node. It cannot guarantee the data is up to date due to network partitioning. Writes might take some time to propagate when the partition is resolved.

Nodes remain online even if they can't communicate with each other and will sync data once the partition is resolved, but you aren't guaranteed that all nodes will have the same data (either during or after the partition)

AP is a good choice if the business needs to allow for [eventual consistency](https://github.localhost/#eventual-consistency) or when the system needs to continue working despite external errors.

>**Amazon's** shopping cart system is designed to always accept items, prioritizing availability.
## Databases and CAP

Database systems designed with traditional [ACID](https://en.wikipedia.org/wiki/ACID "ACID") guarantees in mind such as [RDBMS](https://en.wikipedia.org/wiki/Relational_database_management_system "Relational database management system") choose [consistency](https://en.wikipedia.org/wiki/Consistency_(database_systems) "Consistency (database systems)") over availability.

whereas systems designed around the [BASE](https://en.wikipedia.org/wiki/Eventual_consistency "Eventual consistency") philosophy, common in the [NoSQL](https://en.wikipedia.org/wiki/NoSQL "NoSQL") movement for example, choose availability over consistency.

In other words, newer NoSQL systems are trying to focus on Availability while traditional ACID databases had a higher focus on Consistency.

## Proof

# Brewer’s CAP Theorem

The following diagram shows two nodes in a network, N1 and N2. They both share a piece of data V, which has a value V<sub>0</sub>. 

- N1 is running an algorithm called A, and N2 is running a similar algorithm called B.
- Both A and B are considered to be safe, bug free, predictable.
- In this experiment, **A writes** new values of V and **B reads** values of V.

![intro](https://www.julianbrowne.com/article/brewers-cap-theorem/assets/images/intro.webp)

As an example, when a customer orders a copy of War and Peace from an online book store, N1 uses A to decrement the stock (V<sub>0</sub>) by one. 

When the other customer wants to check on the number of War and Peace copies left, N2 uses B to read the current stock (V<sub>0</sub>).

In an idealistic scenario, where we have both consistency and availability, this is what happens: 

1. A client writes a new value to V, which we’ll call V<sub>1</sub>. 
2. A message (M) passes N1's newly updated V<sub>1</sub> values to N2, which updates the copy of N2's V from V<sub>0</sub> to V<sub>1</sub>. 
3. A read by B of V will return V<sub>1</sub>.

![scenario 1](https://www.julianbrowne.com/article/brewers-cap-theorem/assets/images/scenario-1.webp)

If the network partitions (that is message M from N1 to N2 are not delivered), then N2 contains an inconsistent value of V when step (3) occurs.

![scenario 2](https://www.julianbrowne.com/article/brewers-cap-theorem/assets/images/scenario-2.webp)

If we scaled this system out to even a few hundred transactions, you can see that there are major synchronization issues. 

If M is an asynchronous message, then N1 has no way of knowing whether N2 gets the message. Even with guaranteed delivery of M, N1 has no way of knowing if a message is delayed by a partition event or something failing in N2. 

Making M synchronous doesn’t help because that treats the write by A on N1 and the update event from N1 to N2 as an atomic operation, which would cause latency issues, meaning our service is not highly available. 

So what CAP tells us is that if we want A and B to be highly available (i.e. working with minimal latency) and we want our nodes N1 to Nn (where n could be hundreds or even thousands) to remain tolerant of network partitions (lost messages, undeliverable messages, hardware outages, process failures) then _sometimes_ we are going to get cases where some nodes think that V is V0 (one copy of War and Peace in stock) and other nodes will think that V is V1 (no copies of War and Peace in stock).

This is the case where we would sacrifice availability for consistency.

Let’s quickly analyze this from a transactional perspective.

![transactional view](https://www.julianbrowne.com/article/brewers-cap-theorem/assets/images/tx-view.webp)

If we have a transaction (i.e. unit of work based around the persistent data item V) called α, then α1 could be the write operation from before and α2 could be the read. 

On a local system this would easily be handled by a database with some simple locking, isolating any attempt to read in α2 until α1 completes safely. In the distributed model though, with nodes N1 and N2 to worry about, the intermediate synchronising message has also to complete. 

Unless we can control _when_ α2 happens, we can _never_ guarantee it will see the same data values α1 writes. All methods to add control (blocking, isolation, centralised management, etc) will impact either partition tolerance or the availability of α1 (A) and/or α2 (B).

#### Read More:

https://www.julianbrowne.com/article/brewers-cap-theorem/