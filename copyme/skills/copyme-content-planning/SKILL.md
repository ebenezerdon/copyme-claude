---
name: copyme-content-planning
description: Plan, schedule or organize videos in the CopyMe library. Use when the user asks for a content calendar, what to film next, to schedule scripts, to brainstorm or save video ideas, to move scripts along (recorded, published), to tag or tidy their library, or what is planned for a week.
---

# Planning in CopyMe

CopyMe scripts move through four statuses: `idea` (worth making some day), `in-progress` (written, not recorded yet; every new script starts here), `recorded` (ready to publish), `published`. Each can have a planned `publish_date` (YYYY-MM-DD), `platforms`, `tags` and a published link.

## See where things stand

Call `list_scripts` without filters: its `library` block counts scripts by status and lists the tags in use, and `today` is the server's date. For a week or month, pass `scheduled_from` and `scheduled_to`. Rows show `created` and `updated` days, the first words (`starts`), and `past_publish_date` when a planned day has gone by unpublished; call those out. Report briefly: what's scheduled, what's overdue, what's ready to record, how many ideas are waiting.

## Plan a stretch of videos

1. Look at what's already scheduled and at `in-progress` and `idea` scripts first; plan with what they have before inventing new topics.
2. Propose the plan as a short table: date, title, platform, status, and what's missing (needs writing, needs recording).
3. Ask before changing anything, unless the user already told you to go ahead. Then apply it in **one** `organize_scripts` call (up to 50 changes), not one call per script; its result shows each script after the change, so there's no need to list again.
   - Keep dates scripts already have unless the user asked to move them (asking to schedule a set of scripts on new days counts).
   - Avoid two videos on one day unless the user wants that.
   - Leave out empty scripts and ones that aren't videos (a live speech), and say so. Offer a real title for an "Untitled script" (`organize_scripts` takes `title`).
4. Topics that don't exist yet: save them with `save_ideas` (titles plus a line of angle or hook in `notes`), then schedule them.
5. Use today's date from the conversation. If the user's week or time zone is unclear, ask once.

## Brainstorm ideas

Give each idea a specific title a viewer would click, not a category ("I filmed at 5 a.m. for 30 days", not "Morning routine"). Add the angle or first line in `notes`. Offer to save them; save with `save_ideas` in one call. Its result names existing scripts with a similar title (`similar_existing`): mention those so the user doesn't end up with two of the same video.

## Keep the library tidy

- After a shoot, move what they recorded to `recorded`; after posting, `published` with `published_url`. A video posted without a CopyMe script can still be logged: `create_script` with `status: "published"`, its `published_url`, and no body.
- There's no overdue field: `past_publish_date` is worked out from the date. To deal with overdue scripts, list them and reschedule or move their status; don't invent tags for it.
- "Old" ideas: judge by `created`, not `updated`. Never archive on a guess; list the candidates and let the user choose.
- Use the tags they already use (from `library.tags`) before making new ones.
- Archive (`archived: true`) instead of deleting; archived scripts can be restored.
