# CodeRelay

![ci](https://github.com/ddevalco/coderelay/actions/workflows/ci.yml/badge.svg)

Control your local AI coding agents on your Mac from your iPhone, securely over Tailscale.

CodeRelay runs locally (Mac), stores data locally (SQLite), and is designed to stay tailnet-only (no public tunnels required).

## What you can do with it

- Start a task from your phone and watch it run in real time
- Upload images/files to supported providers (for vision, screenshots, logs, etc.)
- Approve or reject tool actions when a provider supports interactive approvals
- Manage pairing + tokens from the Admin UI (`/admin`)
- Diagnose and repair common “blank app / disconnected” issues with the CLI

## Highlights

- Mobile-first web UI (great on iPhone, also works on desktop browsers)
- Multi-provider support (Codex, OpenCode, GitHub Copilot ACP, Claude)
- Local-first persistence (SQLite event history + uploads)
- Optional interactive approvals for tool calls (provider-dependent)
- CLI + Admin UI for install/update, pairing, tokens, and diagnostics

## How it stays private

- The server binds locally on your Mac (`127.0.0.1`)
- `tailscale serve` publishes it only inside your tailnet (HTTPS/WSS)
- Access is protected by an Access Token + per-device pairing tokens

## Quickstart (macOS + iPhone)

### 1) Install on your Mac

```bash
curl -fsSL https://raw.githubusercontent.com/ddevalco/coderelay/main/scripts/install-local.sh | bash
```

### 2) Expose to your tailnet (Mac)

```bash
tailscale up
tailscale serve --bg http://127.0.0.1:8790
```

### 3) Pair your iPhone

- On your Mac, open `http://127.0.0.1:8790/admin`
- Sign in with your Access Token (print it with `~/.coderelay/bin/coderelay token`)
- Scan the pairing QR on your iPhone

If something feels stuck, run:

```bash
~/.coderelay/bin/coderelay ensure
```

## Documentation

Start here: [`docs/README.md`](docs/README.md)

- Install: [`docs/INSTALL.md`](docs/INSTALL.md)
- Admin UI: [`docs/ADMIN.md`](docs/ADMIN.md)
- Config & settings: [`docs/CONFIG.md`](docs/CONFIG.md)
- Providers: [`docs/PROVIDERS.md`](docs/PROVIDERS.md)
- Troubleshooting: [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md)
- Security model: [`docs/SECURITY.md`](docs/SECURITY.md)

## Demo

[![CodeRelay demo](https://img.youtube.com/vi/kmH0hEY6Y7o/hqdefault.jpg)](https://www.youtube.com/watch?v=kmH0hEY6Y7o)

## Contributing

- Read: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Issues: <https://github.com/ddevalco/coderelay/issues>
- Backlog (Project 2): <https://github.com/users/ddevalco/projects/2>

## Attribution

See [`docs/ATTRIBUTION.md`](docs/ATTRIBUTION.md).
