# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.1] - 2026-09-24

### Changed

- Migrate peer dependencies from `@mariozechner/pi-*` to `@earendil-works/pi-*` scope.
- Refresh devDependencies to latest stable versions:
  - `@biomejs/biome`: 2.5.14
  - `vitest`: 5.0.1
  - `@types/node`: 26.6.2
  - `@typescript/native-preview`: 7.0.0-dev.20260707.2
  - Pin all versions to exact (remove caret ranges).
- Add `@earendil-works/pi-ai` and `@earendil-works/pi-coding-agent` 0.87.1 as exact devDependencies.
- Update Node.js engine requirement from >=20.0.0 to >=22.19.0.
- Add GitHub Actions CI workflow with Bun 1.4.2 support, multi-OS matrix (ubuntu-latest, macos-latest), and Node versions 22, 24.
- Update installation documentation to reflect git-based distribution.
- Update development instructions to use `bun` as the default package manager.

### Fixed

- Test mocks now correctly return unsubscribe function for ExtensionAPI.on() to satisfy type constraints.
- Biome configuration migrated to current format (preset-based).

## [0.1.0] - 2026-05-07

### Added

- Initial pi coding-agent extension that mirrors senpi builtin `anthropic-web-fetch` and injects Anthropic native `web_fetch_*` tools when appropriate.

[Unreleased]: https://github.com/code-yeongyu/pi-anthropic-web-fetch/compare/v0.1.1...HEAD
[0.1.1]: https://github.com/code-yeongyu/pi-anthropic-web-fetch/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/code-yeongyu/pi-anthropic-web-fetch/releases/tag/v0.1.0
