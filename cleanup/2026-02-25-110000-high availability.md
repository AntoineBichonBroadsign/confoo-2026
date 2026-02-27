# [A crash course into high availability for cloud apps](https://confoo.ca/en/2026/session/a-crash-course-into-high-availability-for-cloud-apps)
**High availability**: keep serving despite existing failures — things *will* fail, plan for it.

Different level available :
---


## Redundancy

- **Compute**
  - Relatively easy: load balancers, managed cloud offerings
  - Challenges: keep services stateless; handle versioning during deployments (backward compatibility)

- **Persistence**
  - Main/replica model: primary handles writes, replicas handle reads
  - Or cluster-based replication
  - Most databases and cloud providers offer built-in support
  - Challenges: sharding & redistribution; eventual consistency (read-after-write lag)

---

## Graceful Degradation

- Use when full HA is not practical (3rd-party dependencies, cost constraints)
- Provide a default response or degraded behavior when a component is unavailable

---

## Active-Active

Both infra and app run simultaneously in multiple regions (already hot).

**Patterns:**

| Pattern | Reads | Writes | Complexity | Latency |
|---|---|---|---|---|
| Read local / Write global | From user's region | Single region | Low | Higher on writes |
| Read local / Write partitioned | From user's region | Region based on logic (e.g. user location) | Medium | Lower on writes |
| Read local / Write local | From user's region | Local region | High | Lowest |

- **Write local** requires **conflict resolution** baked into the app from day one — not an afterthought.

**Challenges:**
- Conflict resolution strategy
- Dynamic DNS resolution (auto-redirect on failure)
- App version sync across regions (compatible deploys)
- Data replication cost and consistency
- **Testing**: regularly force failures to validate resilience
- Cloud tools that help: DynamoDB Global Tables, Aurora DSQL

**Costs:**
- Operational: extra traffic, extra compute
- Maintenance: testing schedule
- Development: added application complexity

---

#### Decision Framework

For each component, ask:

- Can this be **async**? (reduces HA requirements)
- Can it **degrade gracefully**?
- How **critical** is it? (what's the cost of downtime?)
- Which **active-active pattern** fits?
- What **conflict resolution** approach is needed?
- What is the **testing schedule** and validation plan?