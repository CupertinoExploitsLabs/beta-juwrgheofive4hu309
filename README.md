# NOCTURNE 0.2 — Enhanced SwiftUI Source

NOCTURNE is an iOS research dashboard with an imported, source-derived dossier for the supplied `CVE-2026-112477-main.zip`.

## What's improved
- Refined dark interface with Overview, Research, Device, and About tabs.
- Research dossier summarizes the supplied README and technical analysis.
- Clear distinction between author-reported observations and independently verified facts.
- Device record form is manual and local UI state only.
- Xcode project and GitHub Actions workflow for an unsigned IPA build.
- Source inventory and provenance notes.

## Imported source archive
The supplied ZIP contained:
- `README.md`
- `docs/ANALYSIS.md`
- `LICENSE`
- `entry_isurf_uaf.m`

The README references `build.sh` and `src/entry_isurf_uaf.m`, but the ZIP actually places `entry_isurf_uaf.m` at its root and does not contain `build.sh`.

## Safety and scope
The uploaded Objective-C file is a kernel use-after-free proof-of-concept. It is **not** embedded, compiled, or executed in NOCTURNE. The archive describes kernel heap grooming and a stale-entry trigger; this package intentionally preserves only high-level research notes and provenance, not the operational trigger or exploit implementation. No kernel access, privilege escalation, persistence, or security bypass is implemented.

The vulnerability claims and device-testing claims are those of the uploaded archive's author and have not been independently verified.

## Build
1. Upload the contents of this folder to the root of a GitHub repository.
2. Open **Actions**.
3. Select **Build NOCTURNE unsigned IPA**.
4. Choose **Run workflow**.
5. Download the `Nocturne-unsigned-ipa` artifact after success.

The output is an **unsigned** IPA. It is not installable as-is; signing requires a valid Apple signing identity and provisioning profile. The workflow has not been run or verified in this environment.
