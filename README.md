<div align="center">

# HEXA TXADMIN RECIPE

### One-click deployment recipe for a Hexa Framework server

A txAdmin recipe that provisions a RedM server already wired up with [`hexa_core`](https://github.com/hexa-development/hexa_core) and the rest of the Hexa stack.

<br>

[![Documentation](https://img.shields.io/badge/Documentation-Hexa_Docs-B45309?style=for-the-badge)](https://hexa-development.github.io/hexa-docs/)
[![RedM](https://img.shields.io/badge/Platform-RedM-8B0000?style=for-the-badge)](https://redm.net/)
[![txAdmin](https://img.shields.io/badge/txAdmin-Recipe-2D8CF0?style=for-the-badge)](https://txadm.in/)
[![Status](https://img.shields.io/badge/Status-Work_in_progress-6B7280?style=for-the-badge)](#status)

<br>

**Deployment · Recipe · Hexa Core · txAdmin**

</div>

---

<a id="status"></a>

## Status

> ⚠ **Work in progress — not ready to deploy.**
> `hexacore.yaml` is currently a placeholder. Until it is filled in, install the Hexa stack manually by following the installation guide in [`hexa-docs`](https://github.com/hexa-development/hexa-docs).

This repository is published early so the recipe URL stays stable once the recipe itself lands.

---

## About

[txAdmin](https://txadm.in/) can build a server from a **recipe** — a YAML file listing the resources to download, the database to create, and the config to write. This repository holds the recipe for a **Hexa Framework** RedM server.

The goal is that a new server owner picks the Hexa recipe in txAdmin's deployer and ends up with a running server, rather than cloning several repositories and wiring up `resources.cfg` and the database by hand.

```text
txAdmin deployer
       │
       ▼
┌───────────────────┐
│   hexacore.yaml   │  ← this repository
└─────────┬─────────┘
          │
          ▼
   hexa_core + hexa_inventory + hexa_progbar
   database schema · resources.cfg · server.cfg
```

---

## Planned contents

| File | Purpose |
| :--- | :--- |
| `hexacore.yaml` | The txAdmin recipe — resource downloads, database setup, generated config |

The recipe is intended to cover:

- Downloading [`hexa_core`](https://github.com/hexa-development/hexa_core) and its dependencies
- Downloading the Hexa resources — [`hexa_inventory`](https://github.com/hexa-development/hexa_inventory), [`hexa_progbar`](https://github.com/hexa-development/hexa_progbar)
- Optionally downloading [`hexa-bridge`](https://github.com/hexa-development/hexa-bridge) for servers migrating from RSG or VORP
- Importing the database schema
- Writing a `resources.cfg` with the correct start order

---

## Installing Hexa in the meantime

Until the recipe is ready, follow the manual installation steps:

### [Open Hexa Documentation →](https://hexa-development.github.io/hexa-docs/)

### [เอกสารภาษาไทย →](https://hexa-development.github.io/hexa-docs/th/)

---

## Hexa Ecosystem

This repository is the deployment entry point for the Hexa Framework stack. Each part is its own repository.

| Project | Description |
| :--- | :--- |
| [`hexa_core`](https://github.com/hexa-development/hexa_core) | Core framework — players, jobs, items, economy, status, callbacks, permissions |
| [`hexa_inventory`](https://github.com/hexa-development/hexa_inventory) | Persistent grid inventory — stashes, shops, ground drops, secure trading |
| [`hexa_progbar`](https://github.com/hexa-development/hexa_progbar) | Screen-fixed progress bar — drop-in for `ox_lib` `progressBar` |
| [`hexa-bridge`](https://github.com/hexa-development/hexa-bridge) | Compatibility layer for supported RSG and VORP resources |
| [`hexa-docs`](https://github.com/hexa-development/hexa-docs) | Official documentation and API reference (VitePress) |
| [`rdr2-unpack`](https://github.com/hexa-development/rdr2-unpack) | Read a local RDR2 install into open formats — GLB, PNG, `.ymap` JSON |
| **`txAdmin`** | txAdmin deployment recipe for a Hexa server <br> *(this repository)* |

Full API reference and installation guides live in [`hexa-docs`](https://github.com/hexa-development/hexa-docs) → [hexa-development.github.io/hexa-docs](https://hexa-development.github.io/hexa-docs/)

---

<div align="center">

### From empty box to running server.

**Built for Hexa Framework**

<br>

[Documentation](https://hexa-development.github.io/hexa-docs/) ·
[เอกสารภาษาไทย](https://hexa-development.github.io/hexa-docs/th/) ·
[hexa_core](https://github.com/hexa-development/hexa_core) ·
[hexa_inventory](https://github.com/hexa-development/hexa_inventory) ·
[hexa_progbar](https://github.com/hexa-development/hexa_progbar) ·
[hexa-bridge](https://github.com/hexa-development/hexa-bridge) ·
[Organization](https://github.com/hexa-development)

</div>
