# CopyMe script markup, by example

One block per line, a blank line between blocks. Everything not listed here is spoken text.

```
## Hook

Nobody asks for anything at five in the morning.{pause}

[B-ROLL: Dark kitchen, kettle on]

So that's when I film. ^^One^^ take, no edits after nine.

## The rule

- Lights on the night before
- Script on the prompter before the kettle boils
- Phone in another room

[ON-SCREEN: Try it for a week]

Try it for a week and tell me how it went.
```

| Markup | What it does on the prompter |
| - | - |
| `#`, `##`, `###` | Section label, not read aloud |
| `---` | A pause between sections |
| `- item`, `1. item` | A list |
| `**word**` | Bold |
| `*word*` | Italic |
| `==Look at the lens.==` | A highlighted delivery note |
| `[B-ROLL: ...]`, `[ON-SCREEN: ...]`, `[SFX: ...]`, `[SHOT: ...]` | Production note on its own line, never read aloud, also listed on the script's shot list |
| `^^word^^` | Stress this word |
| `{pause}`, `{breath}` | A beat, a place to breathe |
| `{Nguyen\|win}` | How to say a word, shown small above it |
| `@Ana: line` | A line spoken by Ana in a two-person script |

Write `\[` to start a spoken line with a literal bracket.
