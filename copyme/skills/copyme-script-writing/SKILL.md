---
name: copyme-script-writing
description: Write a script for a talking video (YouTube, Shorts, TikTok, Reels, LinkedIn, a course, a podcast intro) and save it to CopyMe, the teleprompter. Use when the user asks for a script, a video, a hook, a Short version of something, a translation of a script, or anything they will read on camera or on the CopyMe prompter.
---

# Writing a CopyMe script

The person will read this aloud on CopyMe's prompter, often with voice follow scrolling as they speak. Write for the ear and the mouth, not the page.

## Before writing

1. **Their voice.** Call `get_my_style`. If it has samples, write the way they write: their sentence length, their words, their openings and sign-offs. If it is empty, call `list_scripts` with `status: ["recorded", "published"]` and read the one or two longest with `get_script` (each row's `words` and `starts` show which are worth reading). Never copy their lines; match how they sound.
2. **The length.** CopyMe counts 150 spoken words a minute. Aim for the target:

   | Length | Spoken words |
   | - | - |
   | 15 s | about 35 |
   | 30 s | about 75 |
   | 45 s | about 110 |
   | 60 s | about 150 |
   | 3 min | about 450 |
   | 8 min | about 1,200 |

   Only what is said counts (`==highlighted notes==` included): `##` headings, production notes (`[B-ROLL: ...]` lines) and the marks `{pause}`, `{breath}`, `^^` don't. If the user gave no length, use the platform's usual one from `references/formats.md` and say what you chose.
3. **Ask only what you can't infer.** A topic is enough to start. Don't interview the user before a first draft.

## How the words should sound

- Short sentences, one idea each. Most under 15 words; none over 25.
- Contractions and plain words: "you'll", "use", "start", not "you will", "utilize", "commence".
- The first line is the hook: the payoff, a tension, or a surprising claim, said in under 3 seconds of speech. No "Hey guys, welcome back" unless their style samples open that way.
- One beat per paragraph. A new paragraph wherever they'd take a breath or the picture would change.
- Headings are never said, so the audience never hears them. The line after a heading must work without it: after `## Step 2: Lighting`, not "This one matters most" but "The second thing is lighting, and it matters most."
- Say numbers, symbols and links the way they're spoken: "copyme dot cc", "twenty percent", "three to five". Avoid "e.g.", "/", "&" and URLs in spoken lines.
- No stage directions inside spoken lines. Put them on their own line as a production note.
- End with one clear ask (subscribe, comment, link), not three.

## CopyMe script markup

Save bodies in CopyMe script markup (the connector's instructions describe it in full; `references/markup.md` has examples). Use it lightly:

- `## Section` labels for longer videos (Hook, Story, Steps, Ending), for the speaker to find their place. Not read aloud.
- `[B-ROLL: ...]`, `[ON-SCREEN: ...]`, `[SFX: ...]`, `[SHOT: ...]` on their own line when the user makes edited videos. Not read aloud.
- `^^word^^` on at most one or two words a section, where the emphasis changes the meaning.
- `{pause}` before a reveal or after a big line; `{breath}` in a long sentence that can't be split.
- `{Name|how to say it}` for names and words the speaker might trip on.
- `@Name: line` for two-person scripts.

## Hitting the length

Pass the requested length as `target_seconds` to `create_script` and `edit_script`: the result says how many words over or under it is. If it's more than about 10% off, fix it in one rewrite (`edit_script` with the whole `body`), adding or cutting roughly the number of words it names.

## Saving

- If the result lists `similar_existing`, tell the user (it may be the same video) and offer to archive one.
- If the user asked to save it (or to "put it in CopyMe"), call `create_script` with a short title, the body, and what you know: `status` (`in-progress`, the default, for a script; `idea` for a rough one), `platforms`, `publish_date`, `tags`. Reuse tags they already have (the `library.tags` overview from `list_scripts`) before inventing new ones.
- If they didn't, show the draft and offer to save it.
- A script in another language: set `language` so voice follow listens in it. Translate section labels and notes too, and keep the markup tokens (`{pause}`, `^^word^^`, `[B-ROLL: ...]`) as they are. If their exact variant isn't in the list (Latin American Spanish, say), pick the closest and tell them which you set.
- A new version of an existing script (a Short cut, a translation, a LinkedIn version): set `made_from` with the source script's id.
- After saving, give the prompter link (`read_url`) so they can start reading right away.
- If a script was saved by mistake, archive it (`organize_scripts` with `archived: true`); it can be restored.

If saving fails because the account has no plan, say so plainly and share the link the tool gave. Reading their scripts still works.
