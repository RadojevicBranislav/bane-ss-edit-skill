---
name: kodovi-edit
description: Edit Bane's vertical talking-head tutorials that introduce numbered AI commands and show supplied phone-screen input/result demos, with word-by-word captions, music, SFX, and a profile CTA. Use when the user asks for a kodovi edit or to match the teste / 3k v1 command-demo style.
---

# Kodovi edit

Turn a spoken tutorial into a clear sequence of numbered commands and their on-screen results. Respect the user's latest instructions and chosen editor. For Remotion, follow the relevant Remotion skills; for HyperFrames, start with `/hyperframes`. Use the supplied reference for pacing and layout, then adapt to the actual speech and assets rather than copying timestamps.

## Prepare the edit

1. Inspect the source footage, reference video, phone recordings, profile image, and audio. Identify each command's spoken introduction, input demo, result demo, and return to the speaker. Use the number of commands actually present.
2. Transcribe the speech and correct command names and Serbian diacritics by listening. Build word-level timestamps from the real delivery.
3. Keep the talking-head voice and footage continuous unless the user requests cuts. Put demonstrations, titles, captions, music, and effects on separate editable layers.

## Visual sequence

- Open with a short, bold hook in yellow `#FFDC00`, with a dark outline and enough contrast against the footage. Keep it within the vertical safe area.
- At each spoken command, show a concise numbered title. The reference uses a black rounded pill with white uppercase text. Time its entrance to the spoken phrase and leave enough time to read it.
- Show the supplied phone recording after the introduction: first the input or prompt, then the completed output. Use the meaningful part of each clip; skip loading, ghosted, or unreadable frames. A phone demo may fill the frame when the current user permits it to cover the speaker's face. Otherwise, preserve face clearance.
- Return to the speaker between commands so the next introduction is clear. Do not force equal durations on demonstrations with different amounts of content.
- End with the supplied profile screenshot above the speaker's head, preserving its aspect ratio and readable account details. Place it around the actual head position and gestures.
- When adding a standalone icon or logo, use the repo convention: a white rounded square card, black uppercase name centered at the top, colored icon centered below, original aspect ratio, clear of the face. A user's design for the current video takes precedence.

## Captions and sound

- Default to one spoken word at a time. Set captions in bold uppercase yellow `#FFDC00` with a dark outline, near the lower center. Correct the transcript manually, avoid overlapping word intervals, and make every word visible for at least one output frame. Reposition captions if a phone recording has important controls or text underneath.
- Keep speech intelligible. Mix supplied music quietly under the voice and check the loudest passages. Fade the music at the ends when needed.
- Add restrained, consistent clicks or pops at title and demonstration entrances, not on every caption word. Check SFX against the voice at normal playback volume.

## Smoothness and delivery

- Probe each phone recording's nominal and average frame rates. Screen captures can be variable frame rate even when they report 60 or 120 fps.
- Trim to the useful source interval at native speed. Prepare placed clips at the composition's constant frame rate (normally 30 fps), with exact timeline frame counts and a compatible codec such as H.264/yuv420p. Do not speed a clip up and then force it back to 30 fps if the result repeats frames or judders. Keep original media available for later changes.
- Give video sequences enough premount time for seeking and decoding. Review the last frame before and first frame after every speaker/demo and input/result boundary, then play every transition at full speed with sound. Check for held frames, flash frames, caption gaps, and audio clicks.
- Run the chosen editor's validation checks and preview the hook, every demonstration, and the ending. Leave an editable project and preview; render or export when requested.
