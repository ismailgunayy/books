# Understanding Distributed Systems by Roberto Vitillo

> In Progress

<!-- toc -->

### Table of Contents

1. [Introduction](#1-introduction)\
1.1 [Communication](#11-communication)\
1.2 [Coordination](#12-coordination)\
1.3 [Scalability](#13-scalability)\
1.4 [Resiliency](#14-resiliency)\
1.5 [Maintainability](#15-maintainability)\
1.6 [Anatomy of a distributed system](#16-anatomy-of-a-distributed-system)
<!--
[Part I - Communication](#part-i---communication)


2. [Reliable links](#2-reliable-links)\
   2.1 [Reliability](#21-reliability)\
   2.2 [Connection lifecycle](#22-connection-lifecycle)\
   2.3 [Flow control](#23-flow-control)\
   2.4 [Congestion control](#24-congestion-control)\
   2.5 [Custom protocols](#25-custom-protocols)
3. [Secure links](#3-secure-links)\
   3.1 [Encryption](#31-encryption)\
   3.2 [Authentication](#32-authentication)\
   3.3 [Integrity](#33-integrity)\
   3.4 [Handshake](#34-handshake)
4. [Discovery](#4-discovery)
5. [APIs](#5-apis)\
   5.1 [HTTP](#51-http)\
   5.2 [Resources](#52-resources)\
   5.3 [Request methods](#53-request-methods)\
   5.4 [Response status codes](#54-response-status-codes)\
   5.5 [OpenAPI](#55-openapi)\
   5.6 [Evolution](#56-evolution)\
   5.7 [Idempotency](#57-idempotency)

[Part II - Coordination](#part-ii---coordination)

6. [System models](#6-system-models)
7. [Failure detection](#7-failure-detection)
8. [Time](#8-time)\
   8.1 [Physical clocks](#81-physical-clocks)\
   8.2 [Logical clocks](#82-logical-clocks)\
   8.3 [Vector clocks](#83-vector-clocks)
9. [Leader election](#9-leader-election)\
   9.1 [Raft leader election](#91-raft-leader-election)\
   9.2 [Practical considerations](#92-practical-considerations)
10. [Replication](#10-replication)\
    10.1 [State machine replication](#101-state-machine-replication)\
    10.2 [Consensus](#102-consensus)\
    10.3 [Consistency models](#103-consistency-models)\
    10.4 [Chain replication](#104-chain-replication)
11. [Coordination avoidance](#11-coordination-avoidance)\
    11.1 [Broadcast protocols](#111-broadcast-protocols)\
    11.2 [Conflict-free replicated data types](#112-conflict-free-replicated-data-types)\
    11.3 [Dynamo-style data stores](#113-dynamo-style-data-stores)\
    11.4 [The CALM theorem](#114-the-calm-theorem)\
    11.5 [Causal consistency](#115-causal-consistency)\
    11.6 [Practical considerations](#116-practical-considerations)
12. [Transactions](#12-transactions)\
    12.1 [ACID](#121-acid)\
    12.2 [Isolation](#122-isolation)\
    12.3 [Atomicity](#123-atomicity)\
    12.4 [NewSQL](#124-newsql)
13. [Asynchronous transactions](#13-asynchronous-transactions)\
    13.1 [Outbox pattern](#131-outbox-pattern)\
    13.2 [Sagas](#132-sagas)\
    13.3 [Isolation](#133-isolation)

[Part III - Scalability](#part-iii---scalability)

14. [HTTP caching](#14-http-caching)\
    14.1 [Reverse proxies](#141-reverse-proxies)
15. [Content delivery networks](#15-content-delivery-networks)\
    15.1 [Overlay network](#151-overlay-network)\
    15.2 [Caching](#152-caching)
16. [Partitioning](#16-partitioning)\
    16.1 [Range partitioning](#161-range-partitioning)\
    16.2 [Hash partitioning](#162-hash-partitioning)
17. [File storage](#17-file-storage)\
    17.1 [Blob storage architecture](#171-blob-storage-architecture)
18. [Network load balancing](#18-network-load-balancing)\
    18.1 [DNS load balancing](#181-dns-load-balancing)\
    18.2 [Transport layer load balancing](#182-transport-layer-load-balancing)\
    18.3 [Application layer load balancing](#183-application-layer-load-balancing)
19. [Data storage](#19-data-storage)\
    19.1 [Replication](#191-replication)\
    19.2 [Partitioning](#192-partitioning)\
    19.3 [NoSQL](#193-nosql)
20. [Caching](#20-caching)\
    20.1 [Policies](#201-policies)\
    20.2 [Local cache](#202-local-cache)\
    20.3 [External cache](#203-external-cache)
21. [Microservices](#21-microservices)\
    21.1 [Caveats](#211-caveats)\
    21.2 [API gateway](#212-api-gateway)
22. [Control planes and data planes](#22-control-planes-and-data-planes)\
    22.1 [Scale imbalance](#221-scale-imbalance)\
    22.2 [Control theory](#222-control-theory)
23. [Messaging](#23-messaging)\
    23.1 [Guarantees](#231-guarantees)\
    23.2 [Exactly-once processing](#232-exactly-once-processing)\
    23.3 [Failures](#233-failures)\
    23.4 [Backlogs](#234-backlogs)\
    23.5 [Fault isolation](#235-fault-isolation)

[Part IV - Resiliency](#part-iv---resiliency)

24. [Common failure causes](#24-common-failure-causes)\
    24.1 [Hardware faults](#241-hardware-faults)\
    24.2 [Incorrect error handling](#242-incorrect-error-handling)\
    24.3 [Configuration changes](#243-configuration-changes)\
    24.4 [Single points of failure](#244-single-points-of-failure)\
    24.5 [Network faults](#245-network-faults)\
    24.6 [Resource leaks](#246-resource-leaks)\
    24.7 [Load pressure](#247-load-pressure)\
    24.8 [Cascading failures](#248-cascading-failures)\
    24.9 [Managing risk](#249-managing-risk)
25. [Redundancy](#25-redundancy)\
    25.1 [Correlation](#251-correlation)
26. [Fault isolation](#26-fault-isolation)\
    26.1 [Shuffle sharding](#261-shuffle-sharding)\
    26.2 [Cellular architecture](#262-cellular-architecture)
27. [Downstream resiliency](#27-downstream-resiliency)\
    27.1 [Timeout](#271-timeout)\
    27.2 [Retry](#272-retry)\
    27.3 [Circuit breaker](#273-circuit-breaker)
28. [Upstream resiliency](#28-upstream-resiliency)\
    28.1 [Load shedding](#281-load-shedding)\
    28.2 [Load leveling](#282-load-leveling)\
    28.3 [Rate-limiting](#283-rate-limiting)\
    28.4 [Constant work](#284-constant-work)

[Part V - Maintainability](#part-v---maintainability)

29. [Testing](#29-testing)\
    29.1 [Scope](#291-scope)\
    29.2 [Size](#292-size)\
    29.3 [Practical considerations](#293-practical-considerations)\
    29.4 [Formal verification](#294-formal-verification)
30. [Continuous delivery and deployment](#30-continuous-delivery-and-deployment)\
    30.1 [Review and build](#301-review-and-build)\
    30.2 [Pre-production](#302-pre-production)\
    30.3 [Production](#303-production)\
    30.4 [Rollbacks](#304-rollbacks)
31. [Monitoring](#31-monitoring)\
    31.1 [Metrics](#311-metrics)\
    31.2 [Service-level indicators](#312-service-level-indicators)\
    31.3 [Service-level objectives](#313-service-level-objectives)\
    31.4 [Alerts](#314-alerts)\
    31.5 [Dashboards](#315-dashboards)\
    31.6 [Being on call](#316-being-on-call)
32. [Observability](#32-observability)\
    32.1 [Logs](#321-logs)\
    32.2 [Traces](#322-traces)\
    32.3 [Putting it all together](#323-putting-it-all-together)
33. [Manageability](#33-manageability)
34. [Final words](#34-final-words) -->

<!-- tocstop -->

---

### 1. Introduction

> "A distributed system is one in which the failure of a computer you didn't even know existed can render your own computer unusable."
>
> \- Leslie Lamport

A distributed system is a group of nodes working together by communicating to achieve some task. A node could be a physical device, or a software process.

The main reasons why we build distributed systems are:

- **Need for resiliency**, the system should have high availability. _Example_: Dropbox keeps your data across multiple nodes so that failure of a single node doesn't cause data loss.
- **Need for load handling**, the system should be scalable for bigger workloads. _Example_: Google handles ~150,000 requests per second.
- **Physical limitations**, some systems should provide data in a very short time as a product requirement. _Example_: Netflix should have a CDN server close to you, so that it can stream without issues.

The book covers the fundamental challenges of designing, building and operating distributed systems.

#### 1.1 Communication

The first challenge is caused by the need for nodes to communicate with each other.

How is this communication represented on physical wires? What happens in case of an outage, or a faulty network component? How do the communication protocols guarantee that the data will be delivered correctly, and no middleman will spy on it?

**Readings:**

- [The Law of Leaky Abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/)

**Log**: When things are on track, we don't need to know about how a communication protocol works, because it's just another abstraction for us. However, abstractions leak, and we will need to understand how this communication works if things go off the rails (at least a high-level understanding).

#### 1.2 Coordination

Another hard challenge in distributed systems is coordinating the individual nodes of the system to agree on a shared state and the order of events, so that they can work together. This is challenging because there is no shared memory, the network is unreliable, and nodes can fail at any time.

**Log**: At this point, I've thought about distributed locks, e.g. through Redis, and whether it could solve a part of these coordination issues, namely race conditions. Then I noticed that Redis is just another node in the system, and is just as prone to failure as other nodes.

#### 1.3 Scalability

Another challenge is to make these systems scalable, meaning they should operate without issues as the load increases. Two common techniques to scale:

- _Scaling up_, aka _vertical scaling_: adding more resources to the machine. Obviously, it has physical limits.
- _Scaling out_, aka _horizontal scaling_: adding more machines (instances).

#### 1.4 Resiliency

Another big challenge is keeping the system _available_, which is often described with nines (e.g. _99.99%_). It's the ratio of the amount of time the application can serve requests to the total time measured.

$$
\text{Availability} = \frac{\text{Uptime}}{\text{Uptime} + \text{Downtime}} = \frac{\text{Successful responses}}{\text{Valid requests}}
$$

**Log**: When people talk about a resilient system, I imagine that the system is so well-designed that it doesn't have failures, but that's just wrong. Resiliency is the strength of a system to continue to do its job even when failures happen. Because failures will happen.

**Readings**:

- [AWS Well-Architected Framework, Reliability Pillar, Availability](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/availability.html)

#### 1.5 Maintainability

It mainly talks about how a system should be easy to modify and operate, how to release safely (tests, monitors, etc.)

**Log**: I noticed that in my day-to-day work, I sometimes forget that software systems are living things. It's much more than writing code to solve a problem. It's more like teaching someone to do things, but also continuing to take care of them.

#### 1.6 Anatomy of a distributed system

The book states we'll mainly be concerned with backend applications implementing some kind of business service.

**Readings**:

- [Ports and Adapters Architecture](https://wiki.c2.com/?PortsAndAdaptersArchitecture)
- [Dependency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)

---

<!--
## Part I - Communication

### 2. Reliable links

#### 2.1 Reliability

#### 2.2 Connection lifecycle

#### 2.3 Flow control

#### 2.4 Congestion control

#### 2.5 Custom protocols

---

### 3. Secure links

#### 3.1 Encryption

#### 3.2 Authentication

#### 3.3 Integrity

#### 3.4 Handshake

---

### 4. Discovery

---

### 5. APIs

#### 5.1 HTTP

#### 5.2 Resources

#### 5.3 Request methods

#### 5.4 Response status codes

#### 5.5 OpenAPI

#### 5.6 Evolution

#### 5.7 Idempotency

---

## Part II - Coordination

### 6. System models

---

### 7. Failure detection

---

### 8. Time

#### 8.1 Physical clocks

#### 8.2 Logical clocks

#### 8.3 Vector clocks

---

### 9. Leader election

#### 9.1 Raft leader election

#### 9.2 Practical considerations

---

### 10. Replication

#### 10.1 State machine replication

#### 10.2 Consensus

#### 10.3 Consistency models

#### 10.4 Chain replication

---

### 11. Coordination avoidance

#### 11.1 Broadcast protocols

#### 11.2 Conflict-free replicated data types

#### 11.3 Dynamo-style data stores

#### 11.4 The CALM theorem

#### 11.5 Causal consistency

#### 11.6 Practical considerations

---

### 12. Transactions

#### 12.1 ACID

#### 12.2 Isolation

#### 12.3 Atomicity

#### 12.4 NewSQL

---

### 13. Asynchronous transactions

#### 13.1 Outbox pattern

#### 13.2 Sagas

#### 13.3 Isolation

---

## Part III - Scalability

### 14. HTTP caching

#### 14.1 Reverse proxies

---

### 15. Content delivery networks

#### 15.1 Overlay network

#### 15.2 Caching

---

### 16. Partitioning

#### 16.1 Range partitioning

#### 16.2 Hash partitioning

---

### 17. File storage

#### 17.1 Blob storage architecture

---

### 18. Network load balancing

#### 18.1 DNS load balancing

#### 18.2 Transport layer load balancing

#### 18.3 Application layer load balancing

---

### 19. Data storage

#### 19.1 Replication

#### 19.2 Partitioning

#### 19.3 NoSQL

---

### 20. Caching

#### 20.1 Policies

#### 20.2 Local cache

#### 20.3 External cache

---

### 21. Microservices

#### 21.1 Caveats

#### 21.2 API gateway

---

### 22. Control planes and data planes

#### 22.1 Scale imbalance

#### 22.2 Control theory

---

### 23. Messaging

#### 23.1 Guarantees

#### 23.2 Exactly-once processing

#### 23.3 Failures

#### 23.4 Backlogs

#### 23.5 Fault isolation

---

## Part IV - Resiliency

### 24. Common failure causes

#### 24.1 Hardware faults

#### 24.2 Incorrect error handling

#### 24.3 Configuration changes

#### 24.4 Single points of failure

#### 24.5 Network faults

#### 24.6 Resource leaks

#### 24.7 Load pressure

#### 24.8 Cascading failures

#### 24.9 Managing risk

---

### 25. Redundancy

#### 25.1 Correlation

---

### 26. Fault isolation

#### 26.1 Shuffle sharding

#### 26.2 Cellular architecture

---

### 27. Downstream resiliency

#### 27.1 Timeout

#### 27.2 Retry

#### 27.3 Circuit breaker

---

### 28. Upstream resiliency

#### 28.1 Load shedding

#### 28.2 Load leveling

#### 28.3 Rate-limiting

#### 28.4 Constant work

---

## Part V - Maintainability

### 29. Testing

#### 29.1 Scope

#### 29.2 Size

#### 29.3 Practical considerations

#### 29.4 Formal verification

---

### 30. Continuous delivery and deployment

#### 30.1 Review and build

#### 30.2 Pre-production

#### 30.3 Production

#### 30.4 Rollbacks

---

### 31. Monitoring

#### 31.1 Metrics

#### 31.2 Service-level indicators

#### 31.3 Service-level objectives

#### 31.4 Alerts

#### 31.5 Dashboards

#### 31.6 Being on call

---

### 32. Observability

#### 32.1 Logs

#### 32.2 Traces

#### 32.3 Putting it all together

---

### 33. Manageability

---

### 34. Final words -->
