# BirdDesk

**Poultry management for farmOS — Android app, offline-first**

BirdDesk is a single-file Android app for managing flocks, logging egg collection, feed, health events, and mortality — synced to a [farmOS](https://farmos.org) instance. Built for daily use in the coop, on older Android hardware, with no internet required to log.

Part of the [FarmDesk suite](https://github.com/ltlfarm).

---

## Features

- Bird roster grouped by species (Chicken, Duck, Goose, Other) with tag, name, breed, sex, and flock
- Flock manager with configurable nest boxes per flock
- Egg collection screen — log counts per nest box, with today/week/month totals on the dashboard
- Health logging: weight, medication, observation, procedure, hatch
- Feed logging per flock
- Mortality logging
- Full history with filter chips (All / Eggs / Health / Feed / Death)
- Syncs to farmOS JSON:API — birds as animal assets, logs as farmOS activity logs
- Offline-first: all entries queue locally, pushed only when you tap Sync
- No hardcoded farm data — works with any farmOS instance

---

## Requirements

- farmOS 2.x with JSON:API enabled
- OAuth2 credentials with `farm_manager` scope
- Android 6+ (tested on Samsung Galaxy devices)

---

## Installation

Download the latest APK from [Releases](https://github.com/ltlfarm/birddesk/releases) and sideload it onto your device.

---

## Setup

1. Open the app and tap **Sync → Settings**
2. Enter your farmOS URL, username, and password
3. Tap **Fetch Birds** to import your existing flock from farmOS
4. Configure flocks and nest boxes in **Sync → Flock Manager**
5. Start logging

---

## farmOS Integration Notes

- Birds sync as `asset--animal` with species stored in the `animal_type` term
- All logs use Unix integer timestamps as required by farmOS
- `farm_manager` OAuth scope required — `farm_worker` scope returns no logs for non-owners
- Repeated failed login attempts will trigger a `flood_user_blocked` lockout on farmOS; wait 15–30 minutes without attempts to clear it

---

## Repository

`github.com/ltlfarm/birddesk`

APK builds automatically via GitHub Actions on every push to `main`.
