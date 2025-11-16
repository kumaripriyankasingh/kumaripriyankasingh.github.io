---
layout: techpage
---

# Distributed Transactions in Microservices

A distributed transaction is a transaction that spans multiple services or databases. In a distributed transaction, all services must agree on the outcome of the transaction to ensure consistency. Distributed transactions can be implemented using different protocols, such as the Two-Phase Commit protocol or the Saga pattern.

## Real-World Examples
- E-commerce checkout: When a customer completes a purchase, the transaction typically involves multiple services, such as inventory management, payment processing, and shipping. Coordinating these services requires a distributed transaction protocol.
- Financial transactions: In the financial industry, distributed transactions are used for transferring funds, processing trades, and settling accounts.
- Healthcare systems: In healthcare, distributed transactions can be used to manage patient records, schedule appointments, and process insurance claims.


## Two-Phase Commit

Two-Phase Commit is a classic protocol for implementing distributed transactions. In 2PC, a coordinator node is responsible for coordinating the transaction across multiple nodes. The transaction is divided into two phases:

- Prepare phase: The coordinator node asks all participating nodes if they are ready to commit the transaction. If all nodes respond positively, the coordinator node moves to the second phase. Otherwise, the transaction is aborted.
- Commit phase: The coordinator node sends a commit message to all participating nodes. If all nodes confirm the commit, the transaction is committed. Otherwise, the transaction is aborted.

Two-Phase Commit is commonly used in banking systems where consistency is critical. For example, a bank transfer involves debiting the sender's account and crediting the receiver's account. Both operations must succeed, or the transaction should be rolled back. Two-Phase Commit ensures that both operations are committed, and the system remains consistent.

### Advantages of Two-Phase Commit

- **Consistency:** The Two-Phase Commit protocol guarantees consistency, meaning that the system will always be in a consistent state.
- **Simplicity:** The Two-Phase Commit protocol is relatively simple to implement and understand.

### Disadvantages of Two-Phase Commit

- **Performance:** The Two-Phase Commit protocol is less performant than the Saga pattern since it requires a distributed lock, which can be a bottleneck in high-traffic scenarios.
- **Resilience:** The Two-Phase Commit protocol is less resilient than the Saga pattern since it can't handle partial failures, and the entire transaction is aborted if any node fails.

## Saga Pattern

The Saga pattern is an alternative approach to implementing distributed transactions in a microservices architecture. It breaks down a transaction into a series of smaller, local transactions that can be completed independently by each service. Each local transaction updates the database and publishes an event to notify the next service in the chain. If a local transaction fails, the Saga compensates for the failure by undoing the effects of the previous transactions.

In a Saga, each local transaction is represented by a Step. A Step can be either a regular transaction or a compensating transaction that undoes the effects of the previous transaction. The Saga orchestrator manages the transaction by coordinating the execution of Steps across services.

Saga Pattern is commonly used in e-commerce systems, where a customer places an order that involves multiple services such as inventory, payment, and shipping. Each service updates its database and publishes an event to notify the next service in the chain. If a service fails, the Saga undoes the effects of the previous transactions to ensure consistency.

### Advantages of Saga Pattern

- **Flexibility:** Each service can participate in the transaction independently, making the system more flexible and easier to scale.
- **Resilience:** The Saga pattern is designed to handle partial failures, making the system more resilient.
- **Performance:** The Saga pattern can be more performant than the Two-Phase Commit protocol since it doesn't require a distributed lock.

### Disadvantages of Saga Pattern

- **Complexity:** The Saga pattern introduces additional complexity, requiring more careful design and implementation.
- **Consistency:** The Saga pattern trades consistency for availability, meaning that the system may have temporary inconsistencies during transaction execution.

## Saga vs. Two-Phase Commit: A Comparison

| Criteria     | Saga Pattern | Two-Phase Commit |
|--------------|--------------|------------------|
| Consistency  | Eventual     | Strong           |
| Resilience   | High         | Low              |
| Performance  | High         | Low              |
| Complexity   | High         | Low              |


## Real-World Examples

Let's look at some real-world examples of companies that have used the Saga pattern and the Two-Phase Commit protocol in their microservices architecture.

### Saga Pattern

- **Uber**: Uber uses the Saga pattern for their trip booking service, which involves multiple services such as payment, ride allocation, and driver assignment.
- **Zalando**: Zalando, a fashion e-commerce company, uses the Saga pattern for their order management system, which involves multiple services such as inventory, payment, and shipping.

### Two-Phase Commit

- **Oracle**: Oracle's database system uses the Two-Phase Commit protocol to ensure transactional consistency across multiple databases.
- **Amazon**: Amazon's Simple Queue Service (SQS) uses the Two-Phase Commit protocol to ensure that messages are delivered once and only once.

## Conclusion
Distributed transactions are an essential part of microservices architecture. Both the Saga pattern and the Two-Phase Commit protocol provide solutions to ensure consistency across services. However, they differ in terms of performance, resilience, and complexity.

The Two-Phase Commit protocol guarantees consistency but has some disadvantages, such as performance and resilience issues. On the other hand, the Saga pattern is more flexible, resilient, and performant, but it requires more careful design and implementation.

Choosing between the Saga pattern and the Two-Phase Commit protocol depends on the specific use case and the tradeoffs between consistency, performance, and complexity. As microservices continue to grow in popularity, it's essential to consider the pros and cons of each approach to ensure that the architecture is reliable, scalable, and resilient.



