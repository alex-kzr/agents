---
name: async-patterns
description: Rust async programming patterns with Tokio: concurrent tasks, channels (mpsc/broadcast/oneshot/watch), error handling, graceful shutdown, async traits, streams, and resource management. Use when implementing async Rust code, designing concurrent systems, or debugging async/await behavior.
---

# Rust Async Patterns

Production patterns for async Rust programming with Tokio. Read [`references/details.md`](references/details.md) for full worked examples.

## Patterns at a Glance

| Pattern | Tools | When |
|---|---|---|
| Concurrent tasks | `JoinSet`, `buffer_unordered`, `select!` | Run multiple futures in parallel |
| Channels | `mpsc`, `broadcast`, `oneshot`, `watch` | Communicate between tasks |
| Error handling | `thiserror`, `anyhow`, `timeout` | Propagate and wrap async errors |
| Graceful shutdown | `CancellationToken`, broadcast channel | Stop tasks cleanly on signal |
| Async traits | `async_trait` | Define async interface contracts |
| Streams | `async_stream`, `StreamExt` | Process sequences of async values |
| Resource management | `RwLock`, `Semaphore`, RAII guard | Shared state and connection pools |

## Dependencies

```toml
[dependencies]
tokio = { version = "1", features = ["full"] }
futures = "0.3"
async-stream = "0.3"
async-trait = "0.1"
tokio-util = { version = "0.7", features = ["sync"] }
anyhow = "1.0"
thiserror = "1.0"
tracing = "0.1"
```

## Quick Reference

```rust
// Concurrent tasks with JoinSet
let mut set = JoinSet::new();
set.spawn(async move { fetch_data(&url).await });
while let Some(res) = set.join_next().await { /* handle */ }

// Bounded concurrency
stream::iter(items).map(|x| async move { process(x).await }).buffer_unordered(10).collect().await;

// Graceful shutdown
let token = CancellationToken::new();
tokio::select! { _ = token.cancelled() => break, _ = do_work() => {} }
signal::ctrl_c().await?; token.cancel();
```

## Detailed Examples

See [`references/details.md`](references/details.md) for complete worked patterns covering all 7 pattern categories above.
