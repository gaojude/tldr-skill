# tldr

A Claude Code / agent skill that re-renders the immediately preceding answer as a visual, structural TL;DR — ASCII diagrams, bar charts, tables, decision trees — instead of prose.

[![skills.sh](https://skills.sh/b/gaojude/tldr-skill)](https://skills.sh/gaojude/tldr-skill)

## Why

```
   Bandwidth ceiling
   ═════════════════
   Visual cortex      ████████████████████████   ~10,000,000 bits/s
   Language channel   ▌                          ~10–50 bits/s
                                                 ↑ same ceiling whether
                                                   you read or listen
```

Conscious processing of language tops out around 10–50 bits/sec (Zheng & Meister, *Neuron* 2024) — that's the ceiling reading and listening share. The retina transmits on the order of 10⁷ bits/sec into the visual cortex (Koch et al. 2006). A diagram, table, or arrow flow that takes 3 seconds to read can carry the load of a 200-word paragraph because spatial layout routes around the language channel entirely.

## Install

```bash
npx skills add gaojude/tldr-skill
```

Or scoped:

```bash
# Install globally for Claude Code
npx skills add gaojude/tldr-skill -g -a claude-code
```

## Use

After install, in any agent session:

```
/tldr
```

Or trigger naturally: "tldr this", "make this visual", "viz this", "highest-bandwidth way", "render this dense".

The skill applies to the immediately preceding answer, re-rendering it using:

```
1. BAR CHART     for magnitudes
2. BOX           for grouping
3. TABLE         for cross-comparison
4. ARROWS/FLOW   for sequence/causation
5. TREE/SPLIT    for hierarchy/decisions
```

…plus one final callout line that fuses the insight.

## Example

**Before** (~120 words of prose):

> Reading and listening hit roughly the same bottleneck because the conscious mind only processes about 10 to 50 bits per second. Reading averages around 240 to 260 words per minute and listening peaks around 275 words per minute when sped up. The visual system can take in millions of bits per second of raw input, which is why diagrams can communicate so much more efficiently than the same information rendered as prose. So the real lever is not switching from text to audio but matching the modality to the content type.

**After** (~3 seconds to grasp):

```
   Bandwidth comparison
   ════════════════════
   Visual raw input    ████████████████████████   ~10M bits/s
   Reading             ▌                          ~50 bits/s
   Listening           ▌                          ~39 bits/s
                                                  ↑ same language ceiling

   → Switching channels (text → speech) barely helps.
     Switching modality (language → visual) does.
```

## Compatibility

Install via the `skills` CLI for Claude Code, Codex, Cursor, OpenCode, and 50+ other agents. Output is plain text + ASCII, so rendering quality depends on the host's monospace handling — terminals (Claude Code, Codex) look best.

## License

MIT
