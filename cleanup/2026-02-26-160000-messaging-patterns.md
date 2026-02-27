### [Messaging Patterns to Transform Your Cloud Architecture](https://confoo.ca/en/2026/session/messaging-patterns-to-transform-your-cloud-architecture)

**Message brokers** provide queue management and storage. **Idempotency is critical** — processing a duplicate message must not cause side effects.

---

#### Patterns

**Point-to-Point**
- 1 producer → 1 consumer
- Pros: delivery guarantee, simplicity, reliability, load balancing
- Cons: single point of failure, message ordering challenges, scalability overhead

---

**Pub/Sub**
- Publishers send to topics; multiple subscribers listen
- The broker manages topics and subscriptions
- Pros: decoupling, multiple consumers, scalability, flexibility

---

**Competing Consumers**
- Multiple consumers read from the same queue concurrently
- Broker distributes messages across consumers
- Cons: message ordering not guaranteed, coordination complexity

---

**Message Filtering**
- Consumers selectively receive messages based on criteria
- A **message router** (not the consumer) decides routing
- Cons: added complexity, overhead, scalability considerations

---

**Dead Letter Queue (DLQ)**
- Captures unprocessable or expired messages
- Don't forget to **actually monitor and process them**

---

**Sequential Convoy**
- Ensures related messages are processed **in order**
- Components: message queue + order key + sequential processor (broker-enforced)
- Pros: data integrity, consistency
- Cons: reduced throughput, added latency and complexity

---

**Request/Reply**
- Requester sends a message and waits for a reply — enables synchronous-style communication over async messaging
- The request message includes the **response queue name**
- Pros: simplifies workflows, reliable, provides control & coordination
- Cons: scalability issues, latency, single point of failure

---

**Scatter-Gather**
- Request is sent to multiple recipients in parallel; responses are aggregated
- Flow: requester → scatter (fan-out) → each recipient processes → gather queue → aggregator returns result
- Pros: parallelism, resilience
- Cons: complexity, aggregation latency

---

**Saga**
- Breaks a distributed transaction into smaller, independent steps
- A **saga coordinator** sends steps sequentially:
  1. Step consumer processes and sends ACK
  2. Each ACK triggers the next step from the coordinator
  3. On failure / missing ACK → execute **compensating transaction**
- Key challenge: **defining the compensating logic** for every step
