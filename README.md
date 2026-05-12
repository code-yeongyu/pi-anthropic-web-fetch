# pi-anthropic-web-fetch

[![ci](https://github.com/code-yeongyu/pi-anthropic-web-fetch/actions/workflows/ci.yml/badge.svg)](https://github.com/code-yeongyu/pi-anthropic-web-fetch/actions/workflows/ci.yml) [![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

Anthropic native web fetch extension for the [pi coding agent](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent).

This package is the standalone extraction of senpi's former builtin `anthropic-web-fetch` extension.

## Behavior

The extension does not register a new tool. It intercepts Anthropic requests before they are sent and ensures a native `web_fetch_*` tool is present for `anthropic-messages` payloads.

| Case | Result |
|------|--------|
| API is `anthropic-messages` and no native `web_fetch_*` tool exists | injects `{ type: "web_fetch_20260309", name: "web_fetch" }` |
| Existing native `web_fetch_*` tool exists | preserves it (no duplication) |
| Function variants named `webfetch` or `web_fetch` are present | strips function variants and keeps native variant |
| Non-Anthropic API payload | leaves payload unchanged |

Set `PI_ANTHROPIC_WEB_FETCH_MAX_USES` (positive integer) to include `max_uses` on injected native web-fetch tools.

It also appends a system-prompt section for Anthropic sessions indicating native `web_fetch` availability.

## Installation

The package targets the [`pi`](https://github.com/badlogic/pi-mono/tree/main/packages/coding-agent) coding agent. Pi loads extensions from `~/.pi/agent/extensions/`, project `.pi/extensions/`, or via the `--extension` / `-e` CLI flag.

```bash
# From npm (once published)
pi install npm:pi-anthropic-web-fetch

# From git
pi install git:github.com/code-yeongyu/pi-anthropic-web-fetch

# Manual placement
git clone https://github.com/code-yeongyu/pi-anthropic-web-fetch ~/.pi/agent/extensions/pi-anthropic-web-fetch
cd ~/.pi/agent/extensions/pi-anthropic-web-fetch && npm install

# Dev / one-shot test
pi -e /path/to/pi-anthropic-web-fetch/src/index.ts
```

After installation, restart pi or run `/reload` inside an interactive session.

## Development

```bash
npm install
npm test
npm run typecheck
npm run check
pi -e ./src/index.ts
```

The test suite uses vitest. TypeScript is strict, Node-only, and uses ESM imports with `.js` suffixes.

## Origin

Ported from `packages/coding-agent/src/core/extensions/builtin/anthropic-web-fetch/index.ts` in `code-yeongyu/senpi-mono`.

## License

[MIT](LICENSE).
