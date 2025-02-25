There are g**Five Essential Cloud Characteristics** that can be summarized as follows:

## 1. **Resource Pooling/Multi-Tenancy** 

**Overview:**
Multiple tenants are hosted on the same cloud. The provider’s computing resources are pooled to serve multiple customers at the same time using the same hardware by using a multi-tenant model. Shared hardware resources can be distributed, shared, and accessed by many people through virtualization.
#### **Resource Pooling**

**Definition:**
Resource pooling refers to the practice where a cloud provider gathers physical and virtual resources (like storage, processing power, memory, and network bandwidth) into a shared pool. These resources are dynamically allocated to serve multiple customers based on demand.

#### **Multi-Tenancy**

**Definition:**
Multi-tenancy is a cloud architecture model where multiple tenants (customers) share the same underlying infrastructure and resources while maintaining complete isolation from one another.

#### **Key Characteristics**:

**Virtualization**:
Cloud computing services like [AWS](https://aws.amazon.com/what-is/virtualization/) use virtualization to partition physical hardware resources.

Hardware is virtualized, meaning it is divided into smaller virtual units that can be securely assigned to different users.

[[Virtualization]] is a process that allows a computer to **share** its **hardware resources** with **multiple** digitally separated **environments**. 

This ensures that each user feels like they have their own dedicated resources while sharing the underlying hardware.

**Shared Resources**:
Resources like servers, storage, and bandwidth are shared across multiple users.

Users don’t directly own the hardware but access virtual machines that have a slice of the resources.

**Dynamic Allocation**:
Resources are assigned and reassigned based on customer demand.

For example, if one customer needs more processing power, it is temporarily allocated from the pool without affecting other users.

**Location Independence**:
Customers don’t know or control where their resources are physically located.

They may, however, specify broader preferences, like wanting their data to be stored in a specific country or region to comply with regulations.

**Resource Types**:
Examples of pooled resources include:
- **Storage**: Space to store data, like virtual hard drives.
- **Processing**: CPU or computing power for running applications.
- **Memory**: RAM for handling active processes.
- **Network Bandwidth**: Internet speed and capacity for data transfer.
## 2. **On-Demand Self-Service**

**Unilateral Provisioning:**
A consumer can unilaterally provision computing resources with no human interaction with a service provider.

**Self-Service:**
Usage of self-provisioned resources can be automated based on factors like spikes in traffic.

**Examples:**
- Configuring server time and network storage through the Azure portal.

## 3. **Rapid Elasticity**

1. Capabilities can be elastically previsioned and released
2. Storage and computing resources seem infinite (if you can pay for it)
3. Capabilities can automatically grow and shrink with demand.
4. Example

1. During the holiday season for black Friday spikes and special sales during this season there can be a sudden increased demand on the system. Instead of spending budget on additional permanent infrastructure capacity to handle a couple months of high load out of the year, this is a good opportunity to use an elastic solution.

  

1. **Ubiquitous Network Access**

1. Capabilities are available over the network and accessed through standard mechanisms.

1. HTTP
2. TCP/IP

3. Services can be managed, accessed, or provisioned through thick or thin clients.
4. Services can be managed, accessed, or provisioned using mobile devices.
5. Services can be accessed through multiple security mechanisms.
6. Examples:

1. Eileen checks the usage of her cloud hosted website from her iPhone
2. Ravi accesses his data stored in a NoSQL database hosted in the cloud from his surface while traveling at Seatac

  

1. **Measured Service**

1. Cloud systems automatically control and optimize resource use by leveraging a metering capability at some level of abstraction.
2. Users can the ability to track/measure resource use.
3. Cloud provider can charge per usage of resources

1. Pay-as-you-go
2. Pay-per-use

5. Measured usage extends to monitoring as well (not just for payment)
6. Examples

1. Azure charges per minute of VM usage and when VM is deallocated there is no charge
2. Fred can easily monitor the number of hits his website is getting

  

Thick and Thin Clients

[https://www.geeksforgeeks.org/difference-between-thin-clients-and-thick-clients/](https://www.geeksforgeeks.org/difference-between-thin-clients-and-thick-clients/) 

  

Scalability vs. Elasticity

[https://stackoverflow.com/questions/9587919/what-is-the-difference-between-scalability-and-elasticity](https://stackoverflow.com/questions/9587919/what-is-the-difference-between-scalability-and-elasticity) 

  

[https://blog.turbonomic.com/blog/on-technology/cloud-elasticity-vs-cloud-scalability](https://blog.turbonomic.com/blog/on-technology/cloud-elasticity-vs-cloud-scalability)