# Playlist Assignment System

This document defines the deterministic logic for assigning any track to exactly one playlist.

## MASTER FLOW (Execution Priority)

Follow these steps in order. Stop at the first match.

### 1. Functional & Folk Origin Check (Highest Priority)
Check if the track's primary purpose is functional, holiday, or of specific cultural origin:
- **Kids music?** → `Children: English` or `Children: Russian`.
- **Liturgical/Orthodox Chant?** → `Orthodox` (assign specific service sub-category).
- **Christmas-themed?** → `Christmas` (Unless it's Orthodox Nativity, which stays in `Orthodox`).
- **Slavic/Caucasian Folk origin?** → `Folk` (assign specific sub-category based on **lyrics, cultural origin, and traditional themes**).
    - **Choral?** → `Folk: Choir`.
    - **Cossack?** → `Folk: Cossack`.
    - **High energy/Dance (including modern remixes/mixes)?** → `Folk: Dance`.
    - **Emotional/Story focus?** → `Folk: Ballad / Reflective`.
    - **Upbeat but not for dancing?** → `Folk: Upbeat (Non-Dance)`.

### 2. Other Genre/Form Check (The "Vibe" and "Build")
If not Functional or Folk, assign based on what dominates the track:

- **Is it Latin/Spanish/Flamenco?** → `Flamenco / Latin`.
- **Is it beat-driven/vocal-rhythmic?** → `Hip-Hop / Rap`.
- **Is it band-led (guitars/drums/organic)?** → `Alternative / Indie / Rock`.
- **Is it intimate/solo voice + minimal instrument?** → `Singer/Songwriter`.
- **Is it vocal-led but expressive/orchestral/ballad?** → `Chanson / Ballads` (Specific to the "Urban Romance" or "Theatrical/Dramatic" tradition; not for general mainstream pop ballads).
- **Is it purely electronic/production-first (and NO folk/traditional elements)?**
    - Club/Festival energy? → `Dance / EDM`.
    - Listening/Atmospheric focus? → `Electronic`.
- **Is it Instrumental/Atmospheric?**
    - Musician-focused/Improvisation? → `Jazz / Instrumental`.
    - Background/Textures? → `Ambient / New Age`.
    - Orchestral/Cinematic/Classical? → `Classical / Crossover`.

### 4. Mainstream/Pop Check
If the track doesn't fit any Genre above but is mainstream/commercial pop, assign it to one of these:
- **Has an EDM "drop" or heavy synth?** → `Pop: EDM`.
- **Minimal, alternative, or "stripped" feel?** → `Pop: Modern`.
- **Early-2000s glossy/polished production?** → `Pop: Y2K`.
- **Live feel, traditional pop, or mainstream emotional ballads?** → `Pop: Retro`.
- **Does it fit none of the above?** → `Pop: Retro`.

---

## CORE RULES (Deterministic Logic)

1. **One Track, One Playlist:** No overlaps. If a track fits two, use the Master Flow priority (Functional/Folk > Genre > Pop).
2. **Identity Over Metadata (The Metadata Trap):** Do NOT rely on provided genre tags (e.g., "Russian Chanson", "Pop"). Use the **Track Title**, **Artist**, and **Album** along with the actual sound/vibe to determine the category. **Crucial:** In many cases, "Russian Chanson" is used as a generic, incorrect label for anything in Russian that isn't hard rock; do NOT use this label as evidence for `Chanson / Ballads`. 
3. **Step-by-Step Execution (Step 1 is a Hard Stop):** The Master Flow is not a list of options; it is a sequence of mandatory checks. Step 1 (Functional & Folk) MUST be exhausted before moving to Step 2. If a track has Slavic/Caucasian cultural motifs (traditional instruments, village/historical/folk themes), it is `Folk` (Step 1), even if it sounds like polished pop or is labeled as "Chanson".
4. **Folk/Functional Determination is Superior:** Identifying if a track is Slavic/Caucasian Folk (based on lyrics/origin) or a Functional track takes priority over checking other genres (e.g., a track with folk origins/instruments is `Folk`, not `Chanson` or `Pop`).
5. **Pop is the fallback:** 'Pop' categories are only used if a track is mainstream and does NOT fit into any specific Genre or Folk category. This includes emotional, vocal-led mainstream ballads that lack the specific theatrical or "urban romance" markers of `Chanson / Ballads`.
6. **Folk is Slavic/Caucasian Only:** Non-Slavic/Caucasian folk (e.g., Irish) goes to `Alternative / Indie / Rock` or `Singer/Songwriter` depending on the build. Includes modern remixes of folk tracks (e.g., 'Fiesta Mix' styles).
7. **Singer/Songwriter vs Chanson vs Pop:**
    - `Singer/Songwriter` = Raw, intimate, usually just one person and their instrument; author-led.
    - `Chanson / Ballads` = Polished but deeply theatrical, dramatic, or rooted in the "urban romance" style; often features a heavy vibrato or storytelling delivery. If a track is just an emotional mainstream song, it is `Pop: Retro`.
    - `Pop: Retro` = Mainstream emotional ballads with polished production and a melodic "live" or traditional feel; lacking the specific theatrical/romance markers of Chanson.
8. **Electronic vs Dance / EDM:**
    - `Dance / EDM` = High intensity, high BPM, meant for movement.
    - `Electronic` = Synthesisers used for a listening experience.
9. **Orthodox Overrides Everything:** If it's a church service track, it's `Orthodox`, regardless of whether it's Christmas or contains Folk elements.

---

## PLAYLIST REGISTRY
See `playlists.md` for the full list of valid playlist names.
