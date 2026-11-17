# iBaila Product Baseline

**Source checked:** official iBaila product page, privacy page, and update history.  
**Checked on:** 2026-11-17  
**Classification:** Official product statements; not independent runtime verification.

## Product surface

The official product page currently describes iBaila for macOS 14.2+ and Windows 10/11. Its advertised music sources are Apple Music, Spotify, YouTube Music, SoundCloud, Amazon Music, and user-added local folders.

Advertised features:

- Ambient edge lighting whose palette comes from album artwork and whose movement responds to music; pause/quiet behavior fades or stops the effect.
- A desktop music interface with album cover-flow, a compact player bar, search, playlists/queue behavior, and provider-specific playback handoff.
- Synchronized lyrics, including alternate lyric versions and multiple presentation styles.
- Moving desktop wallpaper based on available moving artwork or music videos.
- Dock icon / Windows tray icon visual feedback.
- Per-display lighting controls, display selection, full-screen behavior, and lower-power modes.

The product page currently advertises a one-time $9.99 purchase for one computer. Pricing and feature packaging can change; treat this as a dated observation, not a permanent assumption.

## Privacy statements

The official privacy page (last updated September 25, 2026) states that:

- Audio is analyzed in memory to drive lighting and is not recorded, stored, or sent.
- The microphone is not used.
- Track metadata and artwork are read from supported music services.
- Browser tab titles are read locally to identify music-playing tabs.
- Track title and artist may be sent to public music services to retrieve lyrics, artwork, album lists, search results, and moving artwork.
- Settings and a short recently-played list remain on the computer.

These are vendor statements. The actual implementation and network behavior remain to be independently observed. Do not present these statements as verified technical facts until tests support them.

## Update-history clues

The official update history provides useful test cases. Recent entries visible on the checked date include:

- **1.14.2 (Nov 12):** Windows audio restoration after shutdown while sound effects were enabled.
- **1.14.1 (Nov 12):** Windows support for app-specific audio channels, including SteelSeries Sonar and similar setups.
- **1.13.1 (Nov 10):** Windows live-wallpaper edge coverage and real display resolution reporting.
- **1.13 (Nov 4):** additional lyric animation pack, reduced lyric GPU use, lower Windows memory use, and main-display selection.
- **1.12.2 (Oct 31):** Spotify Microsoft Store install and non-English Windows username fixes.
- **1.11 (Oct 24):** stickers, sound effects, equalizer, pitch/reverb controls, and lower resource use.
- **1.10 (Oct 22):** Amazon Music browser integration.
- **1.9 (Oct 13):** queue, lyrics search/alternates, and karaoke-style highlighting.
- **1.5 (Oct 10):** browser playback support for YouTube Music, SoundCloud, and Spotify.

Use these entries to design reproducible experiments. A release note tells us what behavior the vendor says changed; it does not reveal the code path or prove the fix in every environment.

## Investigation implications

1. Separate **audio acquisition** from **audio analysis**. The privacy statement suggests in-memory analysis, while update 1.14.1 implies Windows app-specific channel handling matters.
2. Treat app audio capture/routing as a major unknown. Test default output, per-app routing, virtual devices, headsets, and audio-device changes.
3. Treat browser integrations and native music-app integrations as different adapter classes.
4. Test metadata/artwork lookup independently from audio-derived beat/energy analysis.
5. Measure resource usage while playing, paused, hidden, on battery, and in low-power mode.
6. Treat lyrics, moving artwork, and provider search as network-dependent features with distinct privacy and reliability implications.

## Source URLs

- Product: https://aestheticmac.com/ibaila
- Privacy: https://aestheticmac.com/ibaila/privacy
- Update history: https://aestheticmac.com/ibaila/whats-new

## Unknowns — do not guess

- Exact Windows audio capture API and whether capture is per-process, per-session, or via another routing layer.
- Beat/energy feature extraction and smoothing algorithms.
- Color extraction and palette transition logic.
- Lighting renderer and display/window composition technique.
- Browser extension messaging and provider-specific adapter internals.
- Lyrics matching, timing correction, and provider fallback logic.
- Wallpaper/video rendering pipeline and resource lifecycle.
