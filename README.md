# Playlist System (Clean & Structured)

This system provides deterministic rules for assigning tracks to playlists.

## Usage
- Feed `playlist_system.md` and `playlists.md` to any AI model.
- The AI will assign the correct playlist consistently using the **Master Flow**.
- AI Prompt: "Use these rules to define playlists. Don't give explanations - just return the songs grouped by assigned playlist (Title - Artist)"

## Core Principles
1. **One song → one playlist** (No overlaps).
2. **Listen Experience First:** Classify by how the track feels/functions, not just metadata.
3. **Execution Priority:** Follow the Master Flow (Functional > Genre > Pop).