# Playlist System (Clean & Structured)

This system provides deterministic rules for assigning tracks to playlists.

## Usage
- Feed `playlist_system.md` and `playlists.md` to any AI model.
- The AI will assign the correct playlist consistently using the **Master Flow**.
- **Crucial:** Instruct the AI to use the **Track Title**, **Artist**, and **Album** to identify the track's true genre/vibe. Ignore any potentially incorrect metadata genre tags.
- AI Prompt: "Use these rules to define playlists. Use Title, Artist, and Album to identify the track's true vibe. Ignore any provided genre tags that conflict with these rules. Don't give explanations - just return the songs grouped by assigned playlist (Title - Artist)"

## Core Principles
1. **One song → one playlist** (No overlaps).
2. **Listen Experience First:** Classify by how the track feels/functions, not just metadata.
3. **Execution Priority:** Follow the Master Flow (Functional > Genre > Pop).