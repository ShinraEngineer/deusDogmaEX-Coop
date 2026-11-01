# deusDogmaEX-Coop

Public update feed and downloads for the **Dragon's Dogma 2 co-op** setup (DD2gether modpack)
and its **Shinra Crash Reporter**. The modpack source and the signed build tooling are private;
this repo carries only what clients fetch over the network.

## What's here

- **`error-catalog.json`** — the crash-reporter's error catalog. The reporter pulls this file
  from `main` and replaces its local copy whenever the `version` number here is higher, so new
  error codes and classifications ship as a JSON edit with no new build. *(To push a data
  update: edit this file, bump `version`, commit to `main`.)*
- **Releases** — each tagged `vN` (an integer that only goes up) carries the signed
  `ShinraCrashReporter.exe`, a `reporter-update.json` manifest (with its SHA-256), and the
  matching `error-catalog.json`. The reporter offers an **Install / Postpone** prompt for a
  newer release and verifies the download's SHA-256 **and** its "Shinra CC" Authenticode
  signature before replacing anything.

## Trust

All binaries are Authenticode-signed by **Shinra CC**. The reporter only auto-updates to a build
signed by the same publisher as the running one. The certificate is self-signed, so Windows may
show an unknown-publisher prompt on first run; that is expected.

## Privacy

The crash reporter sends a report **only** on a genuine Dragon's Dogma 2 / DD2gether fault, and
only after you consent (at install time, or per incident). A report contains game logs and basic
system information — no personal files, no account details. A normal quit is never reported.
