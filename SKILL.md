---
name: rust
description: Guide for Rust development including code style, testing, building, and quality checks using cargo tools. Apply when working with Rust code, Cargo.toml, or running cargo commands.
user-invocable: true
allowed-tools: Read, Grep, Bash
---

# Rust Development Guide

## Code Style

- Follow standard Rust conventions and idioms
- Use `rustfmt` for code formatting
- Use `clippy` for linting
- Prefer descriptive variable and function names
- Add documentation comments (`///`) for public APIs

## Testing

- Write unit tests in the same file as the code being tested
- Use integration tests in the `tests/` directory for end-to-end functionality
- Run tests with `cargo test`
- Aim for meaningful test coverage of core functionality

## Build Verification

After completing changes to Rust code, run the following checks in order:

1. **Format Check**: `cargo fmt --check`
2. **Lint Check**: `cargo clippy -- -D warnings`
3. **Tests**: `cargo test`
4. **Release Build**: `cargo build --release`
5. **Documentation**: `cargo doc --no-deps --document-private-items`
6. **License Check**: `cargo deny check`
7. **Security Audit**: `cargo audit`

If any check fails, fix the issues before proceeding.

## Security Tools

Projects should use these security tools:

- **cargo-deny**: License and advisory checker. Install with `cargo install cargo-deny`. Configuration in `deny.toml` enforces permissive licenses (MIT, Apache-2.0, BSD) and denies copyleft licenses (GPL, LGPL, AGPL).

- **cargo-audit**: Security vulnerability scanner. Install with `cargo install cargo-audit`. Scans dependencies against the RustSec Advisory Database.

## Dependencies

When adding dependencies:

- Choose well-maintained crates widely used in the Rust ecosystem
- For workspaces, add shared dependencies to `[workspace.dependencies]` in root `Cargo.toml`
- Justify each dependency with a clear use case
