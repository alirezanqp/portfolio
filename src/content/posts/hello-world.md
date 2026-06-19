---
title: "Getting Started with Hexagonal Architecture in Node.js"
description: "A practical guide to implementing ports and adapters pattern for building maintainable, testable backend services."
date: 2024-08-01
tags: ["architecture", "node.js", "ddd"]
---

Hexagonal Architecture (also known as Ports and Adapters) is a design pattern that aims to decouple the core business logic of an application from the external world — databases, APIs, message queues, and UI.

## The Core Idea

Instead of letting your domain logic depend on infrastructure details, you invert the dependency. Your business logic defines **ports** (interfaces), and **adapters** implement those ports for specific technologies.

```typescript
// Port — defined by the domain
export interface UserRepository {
  findById(id: string): Promise<User | null>;
  save(user: User): Promise<void>;
}

// Adapter — infrastructure implementation
export class PostgresUserRepository implements UserRepository {
  async findById(id: string): Promise<User | null> {
    // actual postgres logic here
  }
  async save(user: User): Promise<void> {
    // actual postgres logic here
  }
}
```

This way your domain logic stays clean, testable, and completely independent of the database engine you choose.

## Why It Matters

When I joined Nobati, the codebase was tightly coupled — database calls lived inside service classes, and swapping any infrastructure required touching core logic. After migrating to Hexagonal Architecture:

- Unit tests ran **10x faster** (no database needed)
- New adapters (e.g., switching from MySQL to PostgreSQL) took hours, not days
- Onboarding new engineers became easier since the domain logic was readable in isolation

## Getting Started

Define your domain entities and ports first. Write use cases that depend only on ports. Then wire adapters at the composition root. That's the essence of it.
