# Playlist Assignment System

This document defines the deterministic logic for assigning any track to exactly one playlist.

## MASTER FLOW (Execution Priority)

Follow these steps in order. Stop at the first match.

### 1. Functional Check (High Priority)
Check if the track's primary purpose is functional/holiday:
- **Kids music?** → `Children: English` or `Children: Russian`.
- **Liturgical/Orthodox Chant?** → `Orthodox` (assign specific service sub-category).
- **Christmas-themed?** → `Christmas` (Unless it's Orthodox Nativity, which stays in `Orthodox`).

### 2. Genre/Form Check (The "Vibe" and "Build")
If not Functional, assign based on what dominates the track:

- **Is it Slavic Folk?** → `Folk` (Must choose sub-category):
    - Choral? → `Folk: Choir`.
    - Cossack? → `Folk: Cossack`.
    - High energy/Dance? → `Folk: Dance`.
    - Emotional/Story focus? → `Folk: Ballad / Reflective`.
    - Upbeat but not for dancing? → `Folk: Upbeat (Non-Dance)`.
- **Is it Latin/Spanish/Flamenco?** → `Flamenco / Latin`.
- **Is it beat-driven/vocal-rhythmic?** → `Hip-Hop / Rap`.
- **Is it band-led (guitars/drums/organic)?** → `Alternative / Indie / Rock`.
- **Is it intimate/solo voice + minimal instrument?** → `Singer/Songwriter`.
- **Is it vocal-led but expressive/orchestral/ballad?** → `Chanson / Ballads`.
- **Is it purely electronic/production-first?**
    - Club/Festival energy? → `Dance / EDM`.
    - Listening/Atmospheric focus? → `Electronic`.
- **Is it Instrumental/Atmospheric?**
    - Musician-focused/Improvisation? → `Jazz / Instrumental`.
    - Background/Textures? → `Ambient / New Age`.
    - Orchestral/Cinematic/Classical? → `Classical / Crossover`.

### 3. Mainstream/Pop Check
If the track doesn't fit a specific Genre above but is mainstream/commercial pop, assign it to one of these:
- **Has an EDM "drop" or heavy synth?** → `Pop: EDM`.
- **Minimal, alternative, or "stripped" feel?** → `Pop: Modern`.
- **Early-2000s glossy/polished production?** → `Pop: Y2K`.
- **Live feel, traditional pop, or doesn't fit the above?** → `Pop: Retro`.

---

## CORE RULES (Deterministic Logic)

1. **One Track, One Playlist:** No overlaps. If a track fits two, use the Master Flow priority (Functional > Genre > Pop).
2. **Genre takes precedence:** If a track fits a specific Genre (e.g., Slavic Folk, Flamenco, Hip-Hop), it MUST go there even if it sounds like mainstream pop.
3. **Pop is the fallback:** 'Pop' categories are only used if a track is mainstream and does NOT fit into any specific Genre category.
4. **Folk is Slavic Only:** Non-Slavic folk (e.g., Irish) goes to `Alternative / Indie / Rock` or `Singer/Songwriter` depending on the build.
5. **Singer/Songwriter vs Chanson:**
    - `Singer/Songwriter` = Raw, intimate, usually just one person and their instrument.
    - `Chanson / Ballads` = Polished, often orchestral or with a full backing, high emotional drama.
6. **Electronic vs Dance / EDM:**
    - `Dance / EDM` = High intensity, high BPM, meant for movement.
    - `Electronic` = Synthesisers used for a listening experience.
7. **Orthodox Overrides Everything:** If it's a church service track, it's `Orthodox`, regardless of whether it's Christmas or contains Folk elements.

---

## PLAYLIST REGISTRY
See `playlists.md` for the full list of valid playlist names.
