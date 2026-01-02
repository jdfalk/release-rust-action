<!-- file: README.md -->
<!-- version: 1.0.0 -->
<!-- guid: 4f8b2e9a-5d3c-6e2a-9f7d-2c4e5a1b8d6f -->

# Release Rust Crate Action

Build and publish Rust crates to crates.io with automated testing and linting.

## Features

- 🦀 Rust stable/nightly support
- 📦 crates.io publishing
- ✅ Automated testing
- 🔍 Clippy linting
- 📝 Format checking
- 🎯 Feature flag support

## Usage

```yaml
- uses: jdfalk/release-rust-action@v1
  with:
    crate-token: ${{ secrets.CRATES_IO_TOKEN }}
```

## Inputs

| Input           | Description     | Required | Default        |
| --------------- | --------------- | -------- | -------------- |
| `rust-version`  | Rust version    | No       | `stable`       |
| `manifest-path` | Cargo.toml path | No       | `./Cargo.toml` |
| `crate-token`   | crates.io token | Yes      | -              |
| `run-tests`     | Run tests       | No       | `true`         |
| `run-clippy`    | Run clippy      | No       | `true`         |
| `check-format`  | Check format    | No       | `true`         |
| `dry-run`       | Dry run         | No       | `false`        |
| `features`      | Features        | No       | -              |
| `all-features`  | All features    | No       | `false`        |

## License

MIT
