The easiest way to sabotage your chances of getting an offer in your system design interview is to fail to deliver a working system. This issue isn't (always) that you need to work twice as fast — many time you just need to focus on the right things.

By structuring your interview in this way, you'll stay focused on the bits that are most important to your interviewer.

Here's the framework:
![Recommended system design interview structure](https://d248djf5mc6iku.cloudfront.net/excalidraw/b73b53db7aed219a53e6a505b23db1e1)

## [[Requirements]] (~5 minutes)

The goal of the requirements section is to get a clear understanding of the system that you are being asked to design. To do this, we suggest you break your requirements into two sections.

### 1) Functional Requirements

**First Things First**
Functional Requirements should be the first thing you discuss with your interviewer.

**Users should be able to...**
Functional requirements are your "Users/Clients should be able to..." statements. 
These are the **core features** of your system and should be.

**Clarification & Assumptions**
Oftentimes this is a back and fourth with your interviewer, where you need to ask questions. 
Ask targeted questions as if you were talking to a client, customer, or product manager to arrive at a prioritized list of core features.

- "does the system need to do X?", 
- "do I need to account for Y?", 
- "what would happen if Z?"

Sometimes, you will need to make assumptions about different parts of the system.

**Example: Twitter**
If you were designing a system like Twitter, you might have the following functional requirements:
- Users should be able to post tweets
- Users should be able to follow other users
- Users should be able to see tweets from users they follow

A cache meanwhile might have requirements like:
- Clients should be able to insert items
- Clients should be able to set expirations
- Clients should be able to read items

>[!Keep your requirements targeted!] 
>The main objective in the remaining part of the interview is to develop a system that meets the requirements you've identified -- so it's crucial to be strategic in your prioritization. 
>
>Many of these systems have hundreds of features, but it's your job to identify and prioritize the ***top 3***. 
>
>Having a long list of requirements will hurt you more than it will help you and many top FAANGs directly evaluate you on your ability to focus on what matters.

### 2) Non-functional Requirements

**The system should be able to...**
Non-functional requirements are statements about the system qualities that are important to your users. These can be phrased as "The system should be able to..." or "The system should be..." statements.

**Context & Quantifiability**
It's important that non-functional requirements are 
1. put in the **context of the system**
2. **quantified** (when possible)

For example, "the system should be low latency" is obvious and not very meaningful—nearly all systems should be low latency. "The system should have low latency search, < 500ms," is much more useful as it identifies the part of the system that most needs to be low latency and provides a target.

**Example:**
For example, if you were designing a system like Twitter, you might have the following non-functional requirements:
- The system should be highly availability, prioritizing availability over consistency
- The system should be able to scale to support 100M+ DAUs
- The system should be low latency, rendering feeds in under 200ms

**Checklist**
Coming up with non-functional requirements can be challenging, especially if you're not familiar with the domain. Here is a checklist of things to consider that might help you identify the most important non-functional requirements for your system. 
You'll want to identify the top ***3-5*** that are most relevant to your system.

1. **CAP Theorem**: Should your system prioritize consistency or availability? 
   **Note, partition tolerance is a given in distributed systems.**

2. **Environment Constraints**: Are there any constraints on the environment in which your system will run? For example, are you running on a mobile device with limited battery life? Running on devices with limited memory or limited bandwidth (e.g. streaming video on 3G)?

3. **Scalability**: All systems need to scale, but does this system have unique scaling requirements? For example, does it have bursty traffic at a specific time of day? Are there events, like holidays, that will cause a significant increase in traffic? Also consider the read vs write ratio here. Does your system need to scale reads or writes more?

4. **Latency**: How quickly does the system need to respond to user requests? Specifically consider any requests that require meaningful computation. For example, low latency search when designing Yelp.

5. **Durability**: How important is it that the data in your system is not lost? For example, a social network might be able to tolerate some data loss, but a banking system cannot.
   
6. **Security**: How secure does the system need to be? Consider data protection, access control, and compliance with regulations.

7. **Fault Tolerance**: How well does the system need to handle failures? Consider redundancy, failover, and recovery mechanisms.

8. **Compliance**: Are there legal or regulatory requirements the system needs to meet? Consider industry standards, data protection laws, and other regulations.

## Core Entities (~2 minutes)

Next you should take a moment to identify and list the core entities of you system. 

These are the core entities that 
1. your **API** will exchange (request -> response)
2. your system will persist in a **Data Model**

This helps you to 
- define terms
- understand the data central to your design
- create a foundation to build on

**Start Small**
In the actual interview, this is as simple as jotting down a bulleted list and explaining this is your first draft to the interviewer.

Why not list the entire data model at this point? Because you don't know what you don't know. As you design your system, you'll discover new entities and relationships that you didn't anticipate. 

**Iterate with High Level Design**
By starting with a small list, you can quickly iterate and add to it as you go. Once you get into the high level design and have a clearer sense of exactly what state needs to update upon each request you can start to build out the list of relevant columns/fields for each entity.

**Identify Entities**
A couple useful questions to ask yourself to help identify core entities:
- **Actors:**
  Who are the actors in the system? Are they **overlapping**?
- **Nouns:**
  What are the nouns or resources necessary to satisfy the **functional requirements**?

**Example**
For our Twitter example, our core entities are rather simple:
- User
- Tweet
- Follow