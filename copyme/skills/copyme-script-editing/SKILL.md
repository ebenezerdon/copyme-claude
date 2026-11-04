---
name: copyme-script-editing
description: Improve, shorten, tighten, fix or rewrite a script that is already in CopyMe. Use when the user asks to polish a script, sharpen a hook, cut a script to a length, make it easier to say, fix a line, or change a script they saved in CopyMe.
---

# Editing a CopyMe script

1. **Find it.** If you already have its id from this conversation, skip this. Otherwise `list_scripts` with `query` set to one or two distinctive words (every word must appear in the title, text or tags; title matches come first). The user's words may not be the script's ("coffee shop" for a script titled "Café"), so try a synonym if the first search finds nothing. If nothing matches, try fewer or different words once, then ask the user rather than guessing. If several match, ask which one.
2. **Read it** with `get_script`. The body comes back in CopyMe script markup; keep that markup when you change it.
3. **Decide what to change.** Look for, in this order:
   - A hook that takes more than one sentence to get going.
   - A line after a heading that only makes sense if the heading were heard ("This one matters most" after `## Step 2: Lighting`). Headings are never said; the spoken line has to name the point itself.
   - Sentences over 25 words, or with two ideas.
   - Words that are hard to say together, numbers or symbols written for the eye.
   - Repeats, filler openings ("So basically", "In this video I'm going to").
   - An ending with more than one ask.
   - Length against the target (150 spoken words a minute).
4. **Show before saving** when the change is more than a few lines: the lines before and after, and the new length. Small fixes the user asked for directly can be saved at once.
5. **Save with `edit_script`.**
   - A few changes: pass `edits`, each `find` copied exactly from the body `get_script` returned, long enough to appear once. To add a note or paragraph, find the paragraph before it and replace it with itself, a blank line, and the new block.
   - A rewrite of most of it, or cutting it to a length: pass the whole new `body`, written to the target word count (150 spoken words a minute), and check the returned `reading_time`.
   - Paragraphs you don't touch keep their formatting in CopyMe, so prefer `edits` over a whole new body.
6. **Tell them what changed** in a line or two and the new reading time. `undo_last_edit` steps back one change at a time (up to 10); each result says what it undid and what the next step would undo, so you can walk back to a version the user describes ("the 60-second one").
7. Title, status, tags and dates change with `organize_scripts`, not `edit_script` (which also takes a new title).

If `edit_script` says the script changed in CopyMe meanwhile (it was open in the editor), read it again and redo the edit on the new text.
