---
name: rust-router
description: |-
  CRITICAL: Use for ALL Rust questions including errors, design, and coding.
  HIGHEST PRIORITY for: 比较, 对比, compare, vs, versus, 区别, difference, 最佳实践, best practice,
  tokio vs, async-std vs, 比较 tokio, 比较 async,
  Triggers on: Rust, cargo, rustc, crate, Cargo.toml,
  意图分析, 问题分析, 语义分析, analyze intent, question analysis,
  compile error, borrow error, lifetime error, ownership error, type error, trait error,
  value moved, cannot borrow, does not live long enough, mismatched types, not satisfied,
  E0382, E0597, E0277, E0308, E0499, E0502, E0596,
  async, await, Send, Sync, tokio, concurrency, error handling,
  编译错误, compile error, 所有权, ownership, 借用, borrow, 生命周期, lifetime, 类型错误, type error,
  异步, async, 并发, concurrency, 错误处理, error handling,
  问题, problem, question, 怎么用, how to use, 如何, how to, 为什么, why,
  什么是, what is, 帮我写, help me write, 实现, implement, 解释, explain
globs: ["**/Cargo.toml", "**/*.rs"]
---

---

# Rust Question Router

> **Version:** 2.0.0 | **Last Updated:** 2025-01-22
>
> **v2.0:** Context optimized - detailed examples moved to sub-files

## Meta-Cognition Framework

### Core Principle

**Don't answer directly. Trace through the cognitive layers first.**

```
Layer 3: Domain Constraints (WHY)
├── Business rules, regulatory requirements
├── domain-fintech, domain-web, domain-cli, etc.
└── "Why is it designed this way?"

Layer 2: Design Choices (WHAT)
├── Architecture patterns, DDD concepts
├── m09-m15 skills
└── "What pattern should I use?"

Layer 1: Language Mechanics (HOW)
├── Ownership, borrowing, lifetimes, traits
├── m01-m07 skills
└── "How do I implement this in Rust?"
```

### Routing by Entry Point

| User Signal | Entry Layer | Direction | First Skill |
|-------------|-------------|-----------|-------------|
| E0xxx error | Layer 1 | Trace UP ↑ | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) through [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) |
| Compile error | Layer 1 | Trace UP ↑ | Error table below |
| "How to design..." | Layer 2 | Check L3, then DOWN ↓ | [rust-m09-domain](../rust-m09-domain/SKILL.md) |
| "Building [domain] app" | Layer 3 | Trace DOWN ↓ | domain-* |
| "Best practice..." | Layer 2 | Both directions | [rust-m09-domain](../rust-m09-domain/SKILL.md) through [rust-m15-anti-pattern](../rust-m15-anti-pattern/SKILL.md) |
| Performance issue | Layer 1 → 2 | UP then DOWN | [rust-m10-performance](../rust-m10-performance/SKILL.md) |

### CRITICAL: Dual-Skill Loading

**When domain keywords are present, you MUST load BOTH skills:**

| Domain Keywords | L1 Skill | L3 Skill |
|-----------------|----------|----------|
| Web API, HTTP, axum, handler | [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) | [rust-domain-web](../rust-domain-web/SKILL.md) |
| 交易, 支付, trading, payment | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | [rust-domain-fintech](../rust-domain-fintech/SKILL.md) |
| CLI, terminal, clap | [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) | [rust-domain-cli](../rust-domain-cli/SKILL.md) |
| kubernetes, grpc, microservice | [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) | [rust-domain-cloud-native](../rust-domain-cloud-native/SKILL.md) |
| embedded, no_std, MCU | [rust-m02-resource](../rust-m02-resource/SKILL.md) | [rust-domain-embedded](../rust-domain-embedded/SKILL.md) |

---

## INSTRUCTIONS FOR CLAUDE

### CRITICAL: Negotiation Protocol Trigger

**BEFORE answering, check if negotiation is required:**

| Query Contains | Action |
|----------------|--------|
| "比较", "对比", "compare", "vs", "versus" | **MUST use negotiation** |
| "最佳实践", "best practice" | **MUST use negotiation** |
| Domain + error (e.g., "交易系统 E0382") | **MUST use negotiation** |
| Ambiguous scope (e.g., "tokio 性能") | **SHOULD use negotiation** |

**When negotiation is required, include:**

```markdown
## Negotiation Analysis

**Query Type:** [Comparative | Cross-domain | Synthesis | Ambiguous]
**Negotiation:** Enabled

### Source: [Agent/Skill Name]
**Confidence:** HIGH | MEDIUM | LOW | UNCERTAIN
**Gaps:** [What's missing]

## Synthesized Answer
[Answer]

**Overall Confidence:** [Level]
**Disclosed Gaps:** [Gaps user should know]
```

> **详细协议见:** `patterns/negotiation.md`

---

### Default Project Settings

When creating new Rust projects or Cargo.toml files, ALWAYS use:

```toml
[package]
edition = "2024"  # ALWAYS use latest stable edition
rust-version = "1.85"

[lints.rust]
unsafe_code = "warn"

[lints.clippy]
all = "warn"
pedantic = "warn"
```

---

## Layer 1 Skills (Language Mechanics)

| Pattern | Route To |
|---------|----------|
| move, borrow, lifetime, E0382, E0597 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) |
| Box, Rc, Arc, RefCell, Cell | [rust-m02-resource](../rust-m02-resource/SKILL.md) |
| mut, interior mutability, E0499, E0502, E0596 | [rust-m03-mutability](../rust-m03-mutability/SKILL.md) |
| generic, trait, inline, monomorphization | [rust-m04-zero-cost](../rust-m04-zero-cost/SKILL.md) |
| type state, phantom, newtype | [rust-m05-type-driven](../rust-m05-type-driven/SKILL.md) |
| Result, Error, panic, ?, anyhow, thiserror | [rust-m06-error-handling](../rust-m06-error-handling/SKILL.md) |
| Send, Sync, thread, async, channel | [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) |
| unsafe, FFI, extern, raw pointer, transmute | [rust-unsafe-checker](../rust-unsafe-checker/SKILL.md) |

## Layer 2 Skills (Design Choices)

| Pattern | Route To |
|---------|----------|
| domain model, business logic | [rust-m09-domain](../rust-m09-domain/SKILL.md) |
| performance, optimization, benchmark | [rust-m10-performance](../rust-m10-performance/SKILL.md) |
| integration, interop, bindings | [rust-m11-ecosystem](../rust-m11-ecosystem/SKILL.md) |
| resource lifecycle, RAII, Drop | [rust-m12-lifecycle](../rust-m12-lifecycle/SKILL.md) |
| domain error, recovery strategy | [rust-m13-domain-error](../rust-m13-domain-error/SKILL.md) |
| mental model, how to think | [rust-m14-mental-model](../rust-m14-mental-model/SKILL.md) |
| anti-pattern, common mistake, pitfall | [rust-m15-anti-pattern](../rust-m15-anti-pattern/SKILL.md) |

## Layer 3 Skills (Domain Constraints)

| Domain Keywords | Route To |
|-----------------|----------|
| fintech, trading, decimal, currency | [rust-domain-fintech](../rust-domain-fintech/SKILL.md) |
| ml, tensor, model, inference | [rust-domain-ml](../rust-domain-ml/SKILL.md) |
| kubernetes, docker, grpc, microservice | [rust-domain-cloud-native](../rust-domain-cloud-native/SKILL.md) |
| embedded, sensor, mqtt, iot | [rust-domain-iot](../rust-domain-iot/SKILL.md) |
| web server, HTTP, REST, axum, actix | [rust-domain-web](../rust-domain-web/SKILL.md) |
| CLI, command line, clap, terminal | [rust-domain-cli](../rust-domain-cli/SKILL.md) |
| no_std, microcontroller, firmware | [rust-domain-embedded](../rust-domain-embedded/SKILL.md) |

---

## Error Code Routing

| Error Code | Route To                                             | Common Cause |
|------------|------------------------------------------------------|--------------|
| E0382 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Use of moved value |
| E0597 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Lifetime too short |
| E0506 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Cannot assign to borrowed |
| E0507 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Cannot move out of borrowed |
| E0515 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Return local reference |
| E0716 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Temporary value dropped |
| E0106 | [rust-m01-ownership](../rust-m01-ownership/SKILL.md) | Missing lifetime specifier |
| E0596 | [rust-m03-mutability](../rust-m03-mutability/SKILL.md) | Cannot borrow as mutable |
| E0499 | [rust-m03-mutability](../rust-m03-mutability/SKILL.md) | Multiple mutable borrows |
| E0502 | [rust-m03-mutability](../rust-m03-mutability/SKILL.md) | Borrow conflict |
| E0277 | [rust-m04-zero-cost](../rust-m04-zero-cost/SKILL.md) / [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) | Trait bound not satisfied |
| E0308 | [rust-m04-zero-cost](../rust-m04-zero-cost/SKILL.md) | Type mismatch |
| E0599 | [rust-m04-zero-cost](../rust-m04-zero-cost/SKILL.md) | No method found |
| E0038 | [rust-m04-zero-cost](../rust-m04-zero-cost/SKILL.md) | Trait not object-safe |
| E0433 | [rust-m11-ecosystem](../rust-m11-ecosystem/SKILL.md) | Cannot find crate/module |

---

## Functional Routing Table

| Pattern | Route To | Action |
|---------|----------|--------|
| latest version, what's new | [rust-learner](../rust-learner/SKILL.md) | Use agents |
| API, docs, documentation | **docs-researcher** | Use agent |
| code style, naming, clippy | [rust-coding-guidelines](../rust-coding-guidelines/SKILL.md) | Read skill |
| unsafe code, FFI | [rust-unsafe-checker](../rust-unsafe-checker/SKILL.md) | Read skill |
| code review | **os-checker** | See `integrations/os-checker.md` |

---

## Priority Order

1. **Identify cognitive layer** (L1/L2/L3)
2. **Load entry skill** (m0x/m1x/domain)
3. **Trace through layers** (UP or DOWN)
4. **Cross-reference skills** as indicated in "Trace" sections
5. **Answer with reasoning chain**

### Keyword Conflict Resolution

| Keyword | Resolution |
|---------|------------|
| `unsafe` | [rust-unsafe-checker](../rust-unsafe-checker/SKILL.md) (more specific than rust-m11-ecosystem) |
| `error` | [rust-m06-error-handling](../rust-m06-error-handling/SKILL.md) for general, [rust-m13-domain-error](../rust-m13-domain-error/SKILL.md) for domain-specific |
| `RAII` | [rust-m12-lifecycle](../rust-m12-lifecycle/SKILL.md) for design, [rust-m01-ownership](../rust-m01-ownership/SKILL.md) for implementation |
| `crate` | [rust-learner](../rust-learner/SKILL.md) for version, [rust-m11-ecosystem](../rust-m11-ecosystem/SKILL.md) for integration |
| `tokio` | **tokio-*** for API, [rust-m07-concurrency](../rust-m07-concurrency/SKILL.md) for concepts |

**Priority Hierarchy:**

```
1. Error codes (E0xxx) → Direct lookup, highest priority
2. Negotiation triggers (compare, vs, best practice) → Enable negotiation
3. Domain keywords + error → Load BOTH domain + error skills
4. Specific crate keywords → Route to crate-specific skill if exists
5. General concept keywords → Route to meta-question skill
```

---

## Sub-Files Reference

| File | Content |
|------|---------|
| `patterns/negotiation.md` | Negotiation protocol details |
| `examples/workflow.md` | Workflow examples |
| `integrations/os-checker.md` | OS-Checker integration |
