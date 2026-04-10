# Repository Guidelines

## Project Structure & Module Organization
`habitctl` is a small Rust CLI application built as a single binary crate. Core code lives in [`src/main.rs`](/home/xing/code/rust865047/habitctl/src/main.rs); there are no internal library crates or feature modules yet. Package metadata and dependencies are defined in [`Cargo.toml`](/home/xing/code/rust865047/habitctl/Cargo.toml). User-facing behavior and usage examples belong in [`README.md`](/home/xing/code/rust865047/habitctl/README.md). Build artifacts are produced under `target/` and should not be edited manually.

## Build, Test, and Development Commands
Use Cargo for all local development:

- `cargo build` builds the debug binary for quick iteration.
- `cargo build --release` produces `target/release/habitctl`.
- `cargo run --` runs the CLI locally, for example `cargo run -- log`.
- `cargo test` runs the test suite; add unit tests before changing behavior.
- `cargo fmt` formats Rust code with standard style.
- `cargo clippy -- -D warnings` checks for common mistakes and keeps the crate warning-free.

## Coding Style & Naming Conventions
Follow standard Rust formatting with 4-space indentation and `cargo fmt`. Prefer small helper functions over growing `main()` further. Use `snake_case` for functions and local variables, `CamelCase` for structs and enums, and clear verb-based names for commands or state transitions. Keep file names hyphen-free only when Cargo requires them; otherwise prefer hyphens in repo-level filenames. Avoid adding dependencies unless they materially simplify the CLI.

## Testing Guidelines
This repository currently has no dedicated `tests/` directory, so start with inline unit tests or add integration tests under `tests/` as the codebase grows. Name tests for observable behavior, for example `parses_habit_file_comments` or `computes_score_without_skips`. Run `cargo test` before submitting changes. For CLI changes, also verify a representative command manually, such as `cargo run -- todo`.

## Commit & Pull Request Guidelines
Use imperative Git subjects in the local house style: `EMOJI (scope): Short imperative subject`, for example `🐛 (ask): Fix day offset parsing`. Keep subjects under 72 characters. Prefer focused commits and explain non-trivial changes with `-m` body paragraphs instead of escaped `\n`.

Pull requests should state purpose, sample commands, expected vs. actual behavior, and any external tool requirements. Include before/after output snippets when CLI behavior changes.
