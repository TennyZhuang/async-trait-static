# Async trait methods for `no_std`

Features like `async-trait`, avoid using `Box` and `dyn`.

This crate is ready for `#![no_std]` when [PR69033](https://github.com/rust-lang/rust/pull/69033) merged.

Thanks to crate [async-trait](https://github.com/dtolnay/async-trait), some code from these.

## Features
- [X] basic function `async fn` for trait.
- [ ] support default Implementations.
- [ ] test more feature support.

## Usage

Please enable feature `type_alias_impl_trait`;

```rust
#![feature(type_alias_impl_trait)]

use async_trait_static::async_trait;

async fn hello() -> u8 {
    1
}

#[async_trait]
trait AsyncFnTrait {
    async fn run(&self);
}

struct AsyncStruct;

#[async_trait]
impl AsyncFnTrait for AsyncStruct {
    async fn run(&self) {
        hello().await;
    }
}

```

