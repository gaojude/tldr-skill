---
name: tldr
description: Re-render the immediately preceding answer as a visual/structural "TL;DR" instead of prose. Use when the user invokes `/tldr` or asks for a "tldr", "tl;dr", "high-bandwidth", "visual", "dense", or "viz-first" reply. Routes around the ~10–50 bits/sec language channel by using ASCII diagrams, bar charts, tables, decision trees, and spatial layout — leveraging the visual cortex's much higher raw input bandwidth (~10^7 bits/sec). Apply to the immediately preceding answer or content under discussion, re-rendering it in visual form. Triggers include "/tldr", "tldr this", "make this visual", "viz this", "highest-bandwidth way", "render this dense".
---

# tldr

Re-render information using visual/structural layout instead of prose. Based on the cognitive research that conscious processing of language caps at ~10–50 bits/sec (Zheng & Meister, *Neuron* 2024) while the retina transmits ~10^7 bits/sec to the visual cortex (Koch et al. 2006) — so spatial layout, diagrams, and structural compression beat paragraphs for the same idea.

## Core principle

> **One glance ≥ one paragraph.** If a reader has to read sentences to reconstruct a relationship, the relationship belongs in a diagram.

## The five primitives (use these, not prose)

```
1. BAR CHART        ──  for magnitudes / comparisons of one quantity
   X  ████████████████  big
   Y  ███░░░░░░░░░░░░░  small

2. BOX                  ──  for grouping / containment / "this belongs to that"
   ┌─ category ──────────┐
   │  item   item   item │
   └─────────────────────┘

3. TABLE / GRID         ──  for cross-comparison on 2+ axes
   | option | speed | risk |
   |--------|-------|------|

4. ARROWS / FLOW        ──  for sequence, transformation, causation
   input ─→ step ─→ step ─→ output

5. TREE / SPLIT         ──  for hierarchy or branching decisions
                root
               /    \
            left    right
```

## Rules of engagement

1. **Lead with the single most compressed artifact.** First thing on screen must convey the core in <3 seconds. Usually a labeled bar chart or a 2x2.
2. **Prose is a caption, not the content.** Every visual gets at most 1–2 sentences of context. If you need a paragraph, your visual failed.
3. **Match modality to content type:**
   - quantities → bar chart
   - comparisons → table
   - relationships → boxes with lines
   - sequences/causation → arrows
   - hierarchies/decisions → trees
   - code → fenced code block (already visual)
4. **Use spatial alignment to encode meaning.** Same column = same dimension. Same indent = same level. Adjacency = relatedness. Don't waste pixels.
5. **One callout, at the end.** A single line that fuses the insight. Not a "summary" section. Not bullet points restating what's above.
6. **Match the user's language for labels and prose.** If they wrote in Chinese, write labels in Chinese; if English, English. The *structural primitives* (bars, boxes, arrows) are language-neutral and translate cheaply — but the words inside them are not.

## Anti-patterns (do not do these)

```
✗  Long prose paragraphs explaining what a list could show
✗  "Introduction" / "Background" / "Conclusion" headers
✗  Bulleted lists of full sentences (still prose, just chopped up)
✗  Repeating the same idea in different words
✗  Markdown headers nested 3+ deep — use boxes instead
✗  TL;DR followed by 800 words that restate the TL;DR
✗  Ending with "Let me know if..." / "Hope this helps" / pleasantries
```

## How to apply

When invoked:

1. **Identify the source content.** Usually the immediately preceding answer or the content the user is referring to. If ambiguous, ask in one line.
2. **Extract the 3–6 load-bearing facts.** Everything else is filler.
3. **Pick a primitive per fact** using the matching table above.
4. **Stack them top-to-bottom in order of importance** — heaviest insight first, supporting detail below.
5. **Write the one callout line at the end.** This is the only sentence allowed to do synthesis work.

## Example transformation

**Before** (~120 words, language-channel rate):

> Reading and listening hit roughly the same bottleneck because the conscious mind only processes about 10 to 50 bits per second. Reading averages around 240 to 260 words per minute and listening peaks around 275 words per minute when sped up. The visual system can take in millions of bits per second of raw input, which is why diagrams and visualizations can communicate so much more efficiently than the same information rendered as prose. So the real lever is not switching from text to audio but matching the modality to the content type.

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

## Notes on rendering

- ASCII box characters: `┌ ┐ └ ┘ ─ │ ├ ┤ ┬ ┴ ┼`
- Bars: `█ ▓ ▒ ░ ▌ ▎ ▏` (full → empty)
- Arrows: `→ ← ↑ ↓ ↔ ↕ ↗ ↘ ─→ ══>`
- Bullets when unavoidable: `● ○ ◆ ◇ ★`
- Keep visible line width ≤ ~70 chars so it renders cleanly in terminal + Obsidian + web chat. (YAML frontmatter strings can exceed this; only the rendered body counts.)
- Markdown tables render in all three contexts; ASCII tables render everywhere but are bulkier — prefer markdown tables unless alignment matters.
