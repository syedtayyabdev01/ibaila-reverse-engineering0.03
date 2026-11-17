# Investigation Plan

## 1. Scope and rules

Target: iBaila — https://aestheticmac.com/ibaila  
Analysis toolkit: REA — https://github.com/morluto/rea  
Working platform: Windows 10 (user-reported); confirm exact runtime and tool versions before execution.

This project documents observable behavior and authorized artifacts. It does not assume that a website description reveals the underlying implementation.

## 2. Publicly described feature inventory

The official iBaila product page describes:

| Area | Publicly described behavior | Investigation status |
|---|---|---|
| Ambient lighting | Edge lighting follows music; colors are derived from album artwork; motion reacts to beats | Product-page claim; not locally reproduced |
| Music providers | Apple Music, Spotify, YouTube Music, SoundCloud, Amazon Music, and local folders | Product-page claim; provider-by-provider validation pending |
| Playback UI | Desktop player with artwork, player controls, search, and cover-flow presentation | Product-page claim; inspection pending |
| Lyrics | Synchronized lyrics | Product-page claim; inspection pending |
| Wallpaper | Animated wallpaper using artwork/music-video visuals | Product-page claim; inspection pending |
| Desktop integration | macOS menu bar; Windows system tray; Dock/tray icon behavior | Product-page claim; platform validation pending |
| Displays and power | Per-display lighting and battery/low-power optimizations | Product-page claim; measurement pending |
| Audio handling | Product page says no microphone is used and that music-app audio is authorized | Product-page claim; exact capture/routing mechanism unknown |

The official update history is a useful source for feature chronology and regression clues. Record the date and exact release note for each finding rather than treating release notes as proof of internal architecture.

## 3. Work stages

### Stage A — Baseline and source preservation

- Record product page, update-history page, access date, and screenshots.
- Record OS version, CPU/GPU, display count, audio devices, and power mode.
- Obtain installer only from the official vendor distribution channel, if available.
- Record installer filename, version, publisher/signature, and SHA-256.
- Do not execute unknown binaries until provenance and safety are assessed.

### Stage B — Website observation with REA

- Read the current REA browser-observation guide.
- Check REA readiness and browser/CDP requirements.
- Use a dedicated test browser profile with no personal accounts.
- Approve only the exact official iBaila origin.
- Capture page structure, script inventory, assets, and relevant network requests.
- Sanitize HAR files before committing; remove cookies, authorization headers, tokens, and personal identifiers.

### Stage C — Desktop artifact inspection

- Identify whether the authorized build is Electron, native, .NET, or another framework.
- If JavaScript/Electron, extract files without bypassing protections and run REA's static application analysis.
- Inventory package metadata, entry points, modules, imports, IPC boundaries, native add-ons, and source maps.
- If native code is present, use only legally obtained analysis tools and authorized binaries.
- Distinguish static evidence from runtime observations.

### Stage D — Behavioral experiments

For each experiment, record: hypothesis, setup, steps, expected result, actual result, evidence file, and conclusion.

1. Start/pause/resume/seek and observe lighting transitions.
2. Change tracks and compare dominant artwork colors.
3. Compare quiet passages, transients, and beat-heavy audio.
4. Switch music providers and record provider-specific differences.
5. Test local audio separately from browser-based playback.
6. Test multi-monitor placement and per-display settings.
7. Measure CPU/GPU usage and battery impact over a fixed interval.
8. Disconnect/reconnect audio devices and observe recovery.

Do not capture or store copyrighted audio; use short, lawful test material or synthetic signals where possible.

### Stage E — Independent implementation

Only after evidence review, define an original architecture with separable modules:

- provider adapters
- playback/session state
- authorized audio input or loopback capture
- audio feature extraction
- artwork/color analysis
- lighting renderer and display mapping
- lyrics/provider adapter
- wallpaper renderer
- desktop shell and settings
- diagnostics, permissions, and privacy controls

Do not copy iBaila code, visual assets, logos, or distinctive branding. Recreate general functionality with original code and assets.

## 4. Evidence record template

For every finding, use:

- ID:
- Date/time and timezone:
- Source/build/version:
- OS and hardware:
- Action or experiment:
- Observation:
- Evidence path:
- Confidence: high / medium / low
- Classification: verified / observed / hypothesis / unknown
- Limitations and next test:

## 5. Immediate blockers / unknowns

- No iBaila installer or application artifact has been supplied or verified in this workspace.
- No local REA installation/readiness check has been run yet.
- Website inspection and browser observation have not yet been performed.
- Exact audio capture mechanism, beat-analysis algorithm, artwork extraction path, and lighting protocol remain unknown.
