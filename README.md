# iBaila Reverse Engineering Lab

Independent, evidence-led investigation of the publicly observable behavior and architecture of [iBaila](https://aestheticmac.com/ibaila), using the official [REA toolkit](https://github.com/morluto/rea).

> **Status:** Repository initialized. Product research is documented; local runtime inspection and implementation have not yet been performed.

## Goals

- Map iBaila's user-facing features and supported music sources.
- Observe website behavior, network activity, assets, and desktop-app boundaries where lawful and technically available.
- Separate verified observations from hypotheses.
- Build an original, independently implemented alternative; do not copy proprietary source code, branding, or protected assets.

## Investigation tracks

1. **Product behavior** — player, ambient edge lighting, color extraction, beat response, lyrics, wallpaper, multi-display behavior, power management.
2. **Integrations** — Apple Music, Spotify, YouTube Music, SoundCloud, Amazon Music, and local audio.
3. **Desktop architecture** — identify platform-specific processes, packaging, permissions, audio capture/routing, and UI technologies from authorized artifacts.
4. **Evidence** — screenshots, sanitized HAR files, asset inventories, REA reports, reproduction steps, and confidence levels.
5. **Implementation** — original code, replaceable providers, documented compatibility, and tests.

## REA quick start

REA's current README specifies Node.js 22.x (>=22.23.4), 24.x (>=24.22.1), or 26.12.1+, plus npm.

From a trusted working directory, run:

```powershell
npx rea-agents@latest setup
```

For a one-off JavaScript/Electron artifact analysis:

```powershell
npx -y rea-agents@latest analyze-javascript-application "D:/path/to/extracted/app" --json
```

Use only application files you own or are authorized to inspect. For website observation, follow REA's browser-observation guide and explicitly approve the target origin. Do not upload private tokens, cookies, account data, or unredacted HAR files.

## Repository structure

- `docs/INVESTIGATION_PLAN.md` — staged workflow, evidence rules, and current known facts.
- `evidence/` — sanitized observations and captures (never commit secrets or personal data).
- `reports/` — REA output summaries and architecture notes.
- `src/` — original implementation, once the investigation establishes requirements.

## Evidence labels

- **Verified** — directly observed or supported by an official source, with date and reference.
- **Observed** — reproduced locally, with environment and steps recorded.
- **Hypothesis** — plausible explanation requiring a test.
- **Unknown** — not yet investigated.

## Legal and ethical boundary

This is for lawful research, interoperability, education, and independent implementation. No DRM circumvention, credential extraction, license bypass, unauthorized access, or redistribution of iBaila's proprietary code/assets. Respect REA's license and the licenses/terms of any inspected software.

## First milestone

Complete the feature/integration inventory, then inspect the public website and any authorized installer or application build. Do not claim internal implementation details until supported by evidence.
