# tldr

A Claude Code / agent skill that re-renders the preceding answer as a visual, structural TL;DR — ASCII diagrams, bar charts, tables, decision trees — instead of prose.

[![skills.sh](https://skills.sh/b/gaojude/tldr-skill)](https://skills.sh/gaojude/tldr-skill)

## Why

```
   带宽对比 / Bandwidth comparison
   ════════════════════════════════
   视觉原始输入 / Visual input  ████████████████████████  10M bits/s
   阅读 / Reading               ▌                          ~50 bits/s
   听力 / Listening             ▌                          ~39 bits/s

   → Prose competes for the ~50 bits/s language channel.
     Spatial layout uses the ~10M bits/s visual channel.
```

Conscious processing caps at ~10–50 bits/sec for language but the visual system feeds millions of bits/sec. A diagram, table, or arrow flow that takes 3 seconds to read can carry the same load-bearing facts as a 200-word paragraph.

## Install

```bash
npx skills add gaojude/tldr-skill
```

Or with explicit targeting:

```bash
# Global install for Claude Code
npx skills add gaojude/tldr-skill --skill tldr -g -a claude-code
```

## Use

After install, in any agent session:

```
/tldr
```

Or trigger naturally: "tldr this", "make this visual", "viz this", "render this dense".

The skill applies to the *immediately preceding* answer — it re-renders that content using:

```
1. BAR CHART     for magnitudes
2. BOX           for grouping
3. TABLE         for cross-comparison
4. ARROWS/FLOW   for sequence/causation
5. TREE/SPLIT    for hierarchy/decisions
```

…plus one final bold callout line that fuses the insight.

## Compatibility

Works with any agent that consumes the `SKILL.md` format: Claude Code, Codex, Cursor, OpenCode, and more.

## License

MIT
