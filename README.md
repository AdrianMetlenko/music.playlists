# Playlist System (Clean & Structured)

This system provides deterministic rules for assigning tracks to playlists.

## Usage
- Feed `playlist_system.md` and `playlists.md` to any AI model.
- The AI will assign the correct playlist consistently using the **Master Flow**.
- **Crucial:** Instruct the AI to use the **Track Title**, **Artist**, and **Album** to identify the track's true genre/vibe. Ignore any potentially incorrect metadata genre tags.
- AI Prompt: "You are a deterministic music classifier. Use these rules to assign tracks to playlists. Follow the Master Flow (Step 1 -> Step 2 -> Step 3) and NEVER skip a step. Step 1 (Functional/Folk) is a HARD STOP. Use Title, Artist, and Album to identify the track's true vibe. **WARNING:** Ignore 'Russian Chanson' or 'Pop' genre tags - they are often incorrect. If a track has folk instruments/motifs, it MUST be Folk. If it's mainstream and emotional but lacks theatrical vibrato, it is Pop: Retro. Don't give explanations - just return the songs grouped by assigned playlist (Title - Artist)"

## Core Principles
1. **One song → one playlist** (No overlaps).
2. **Listen Experience First:** Classify by how the track feels/functions, not just metadata.
3. **Execution Priority:** Follow the Master Flow (Functional/Folk > Genre > Pop).