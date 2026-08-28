<div align="center">

<a href="https://github.com/hexa-development">
  <img src="https://raw.githubusercontent.com/hexa-development/.github/main/assets/banner.png" alt="Hexa Development" width="880">
</a>

# HEXA TXADMIN RECIPE

### One-click deployment recipe for a Hexa Framework server

A txAdmin recipe that provisions a RedM server already wired up with [`hexa_core`](https://github.com/hexa-development/hexa_core) and the rest of the Hexa stack.

<br>

[![Documentation](https://img.shields.io/badge/Documentation-Hexa_Docs-B45309?style=for-the-badge)](https://hexa-development.github.io/hexa-docs/)
[![RedM](https://img.shields.io/badge/Platform-RedM-8B0000?style=for-the-badge)](https://redm.net/)
[![txAdmin](https://img.shields.io/badge/txAdmin-Recipe-2D8CF0?style=for-the-badge)](https://txadm.in/)
[![Recipe](https://img.shields.io/badge/Recipe-Ready-16A34A?style=for-the-badge)](#quick-start)

<br>

**Deployment · Recipe · Hexa Core · txAdmin**

</div>

---

<a id="quick-start"></a>

## Quick start

In txAdmin, create a new server, choose **Remote URL** deployment, and paste:

```
https://raw.githubusercontent.com/hexa-development/txAdmin/main/hexacore.yaml
```

txAdmin asks for the database credentials, runs the recipe, and you end up with a
RedM server that boots straight into the Hexa Framework.

---

## About

[txAdmin](https://txadm.in/) can build a server from a **recipe** — a YAML file listing the
resources to download, the database to create, and the config to write. This repository holds
the recipe for a **Hexa Framework** RedM server.

```text
txAdmin deployer
       │
       ▼
┌───────────────────┐
│   hexacore.yaml   │  ← this repository
└─────────┬─────────┘
          │
          ▼
   hexa_core + hexa_progbar + hexa_inventory
   oxmysql · cfx-server-data · server.cfg
```

---

## What the recipe installs

| Resource | Where it lands | Started |
| :--- | :--- | :---: |
| [cfx-server-data](https://github.com/citizenfx/cfx-server-data) | `resources/[cfx-default]` | `mapmanager`, `spawnmanager` only |
| [oxmysql](https://github.com/CommunityOx/oxmysql) | `resources/[standalone]` | ✅ |
| [`hexa_core`](https://github.com/hexa-development/hexa_core) | `resources/[hexa]` | ✅ |
| [`hexa_progbar`](https://github.com/hexa-development/hexa_progbar) | `resources/[hexa]` | ✅ |
| [`hexa_inventory`](https://github.com/hexa-development/hexa_inventory) | `resources/[hexa]` | ✅ |
| [`hexa-bridge`](https://github.com/hexa-development/hexa-bridge) — `rsg-core`, `vorp_core` | `resources/[hexa-bridge]` | ❌ opt in |

The bridges are installed but left commented out in `server.cfg`. Enable one only if you are
migrating existing RSG or VORP scripts, and never alongside the real core of the same name.

### Database

There is no SQL file to import. `hexa_core` creates and migrates its own tables from
`install.sql` on every boot, so the recipe only runs `connect_database` to provision the
database and write the connection string.

---

## Deployment defaults

The recipe rewrites two values in `hexa_core/config/main.lua`. Both shipped defaults suit a
developer machine rather than a fresh server:

| Setting | Shipped | Recipe sets | Why |
| :--- | :--- | :--- | :--- |
| `Config.IdentifierType` | `'steam'` | `'license'` | `steam` refuses every player who did not launch the game through Steam. Every RedM player has a license identifier. |
| `Config.MultiCharacter` | `true` | `false` | `true` disables auto-login and waits for `hexa_multicharacter` to spawn the player. That resource is not part of this recipe, so the player would never spawn. |

Change either back in `resources/[hexa]/hexa_core/config/main.lua` once you have a character
selection resource in place.

---

## Files

| File | Purpose |
| :--- | :--- |
| [`hexacore.yaml`](hexacore.yaml) | The txAdmin recipe |
| [`server.cfg`](server.cfg) | Config template the recipe moves into the server root |
| [`myLogo.png`](myLogo.png) | Server icon, 96×96 as RedM requires, loaded by `load_server_icon` |

`server.cfg` is a normal file, so you can read it before deploying and edit it after. The
recipe fills in `{{serverEndpoints}}`, `{{dbConnectionString}}`, `{{svLicense}}`,
`{{maxClients}}` and `{{serverName}}` as the last step.

---

## After deploying

1. **Grant yourself admin** — copy your license identifier from txAdmin → Players, then
   uncomment the two `add_principal` lines at the bottom of `server.cfg`.
2. **Set the locale** — `setr locale` and `setr hexa_inventory:locale` both accept `en` or `th`.
3. **Read the docs** — everything the framework exposes is documented below.

---

## Installing by hand instead

The recipe is a convenience, not a requirement. To install the stack manually — or to
understand what the recipe is doing — follow the installation guide:

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
| **`txAdmin`** | One-click txAdmin recipe that deploys the whole Hexa stack <br> *(this repository)* |

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
