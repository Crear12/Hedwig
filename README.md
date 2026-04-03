# Hedwig

![ci](https://github.com/Crear12/Hedwig/actions/workflows/ci.yml/badge.svg)

Hedwig is a customized CodeRelay deployment for controlling local AI coding agents on your Mac from your iPhone, securely over Tailscale.

The app runs locally on macOS, stores data locally in SQLite, and is designed to stay tailnet-only with no public tunnel requirement. The visible product branding is `Hedwig`, while the bundled local CLI/install paths still use `coderelay`.

## What's Customized In Hedwig

- Hedwig branding across the web app, share sheets, notifications, and install manifest
- Gryffindor-inspired scarlet and triple-yellow visual theme for the main interface
- HarryP display typography on branded page chrome while conversation text stays readable in the standard UI font
- `Extra High` reasoning option added to the composer and settings presets
- Improved markdown rendering for conversation readability, including clearer bullets, spacing, and block structure
- Push notification support for Home Screen / push-capable browser contexts, plus away-mode blocked-turn alerts

## What You Can Do With It

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
- Optional push notifications with blocked-turn alerts when the browser/device supports them

## How It Stays Private

- The server binds locally on your Mac (`127.0.0.1`)
- `tailscale serve` publishes it only inside your tailnet (HTTPS/WSS)
- Access is protected by an Access Token + per-device pairing tokens

## Quickstart (macOS + iPhone)

### 1) Install on your Mac

```bash
curl -fsSL https://raw.githubusercontent.com/ddevalco/coderelay/main/scripts/install-local.sh | bash
```

If you are installing from this fork, swap the URL to:

```bash
curl -fsSL https://raw.githubusercontent.com/Crear12/Hedwig/main/scripts/install-local.sh | bash
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

To enable iPhone push notifications, open the HTTPS Tailscale URL on iPhone and add Hedwig to the Home Screen before enabling notifications in Settings.

If something feels stuck, run:

```bash
~/.coderelay/bin/coderelay ensure
```

## Notes

- The user-facing app name is `Hedwig`.
- The local service directory, binary, and install scripts still use `coderelay` paths for now.
- Browser push requires a push-capable context. On iOS that means the Home Screen app, not a normal Safari tab.

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
- Issues: <https://github.com/Crear12/Hedwig/issues>
- Upstream project: <https://github.com/ddevalco/CodeRelay>

## Attribution

See [`docs/ATTRIBUTION.md`](docs/ATTRIBUTION.md).
