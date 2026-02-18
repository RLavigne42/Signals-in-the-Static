# Episode Extraction Methodology

This document describes the exact pattern used to split the master gameplay transcript into per-episode `Gameplay_XX.txt` files.

## Source and target
- **Source transcript:** `Actual GamePlay of The Disconnected Frontier [Classic Edition] -  e842596b-2afd-42b6-8dad-410e95709060.md`
- **Episode outputs:** `Episode_XX/Gameplay_XX.txt`

## Extraction pattern used in Episodes 01-06
Each episode file is built from three pieces, in this order:

1. **Context overlay from the prior assistant turn**
   - Copy the previous assistant response’s final decision block:
     - `Your Choices`
     - Option lines
     - Closing prompt (`What will you do?` or `Which path do you choose?`)
   - This creates continuity and preserves the option wording that led to the next user choice.

2. **User selection for the current episode**
   - Add:
     - `user`
     - The exact user choice text (name or number).

3. **Assistant response for the current episode**
   - Add:
     - `assistant`
     - The full assistant response that follows that user choice.

## Formatting cleanup rules
To match the existing `Gameplay_XX.txt` style:
- Remove Markdown emphasis markers (`**`).
- Remove heading markers (`###`, `####`).
- Remove list markers (`* ` and numbered list prefixes like `1. `) while keeping line text.
- Unescape punctuation from the markdown export (for example `\-`, `\(`, `\)` → normal punctuation).
- Keep natural line breaks so sections such as `State Machine`, `Approach Hooks`, and `Your Choices` remain readable.

## Episode indexing convention
- Episode `N` corresponds to user/assistant turn pair `N` in the chosen linear playthrough path (starting from `Venture toward the Glowing 80s Arcade`).
- For episode `N`:
  - Overlay comes from assistant turn `N-1`.
  - User and assistant content come from turn `N`.

## Trial extraction applied now
Using this method, episodes **07-10** were extracted into:
- `Episode_07/Gameplay_07.txt`
- `Episode_08/Gameplay_08.txt`
- `Episode_09/Gameplay_09.txt`
- `Episode_10/Gameplay_10.txt`

## Additional batch extraction
Using the same method, the next 25 episodes were extracted as Episodes **11-35** (`Episode_11/Gameplay_11.txt` through `Episode_35/Gameplay_35.txt`).

## Final batch extraction
Using the same method, extraction was completed through the end of the transcript as Episodes **36-86** (`Episode_36/Gameplay_36.txt` through `Episode_86/Gameplay_86.txt`).

