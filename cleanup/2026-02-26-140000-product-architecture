### [Blending Product Thinking with Architecture](https://confoo.ca/en/2026/session/blending-product-thinking-with-architecture-1)

**Core idea**: architecture doesn't exist in a vacuum — it must fit its product context, and evolve as the product evolves.

> Start with the problem, not the solution.

---

#### Strategic Domain-Driven Design (DDD)

1. Map the **product workflow** from a user perspective — identify each step in the usage flow
2. Find the **significant events** in that flow
3. List high-level **commands** (actions) and **events**
4. Use those to identify and draw **domain boundaries** — which naturally map to team boundaries

- Intentional coupling between domains *can* be the right call
- Watch for words that have **multiple definitions** across domains — a sign of a boundary
- Use **Model Exploration Whirlpool** for deeper domain modeling
- **Reporting** is not "fetch all data" — it targets specific cases and data shapes; treat it as its own concern

---

#### C4 Model

Describe architecture at four levels of zoom:

| Level | Name | What it shows |
|---|---|---|
| C1 | **Context** | Product in its environment — users, external systems |
| C2 | **Container** | High-level modules — web app, DB, API, mobile app |
| C3 | **Component** | Internals of a container — specific components and their responsibilities |
| C4 | **Class** | Code-level detail |

- Watch out for **dependency loops** between components

---

#### Context Mapping

- Map relationships and dependencies between domains
- Identify domains that need to **evolve faster** than others and consciously design for that flexibility

---

#### Architecture Decision Records (ADRs)

- Document architecture choices with **timestamp**, **context**, and **consequences**
- Explicitly capture the **tradeoffs** made
- The team making the decision should be the one writing the record

https://c4model.com/