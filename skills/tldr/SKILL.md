---
name: tldr
description: Re-render the preceding information as a visual/structural "TL;DR" instead of prose. Use when the user invokes `/tldr` or asks for a "tldr", "tl;dr", "high-bandwidth", "visual", "dense", or "viz-first" reply. Routes around the ~50 bits/sec language bottleneck by using ASCII diagrams, bar charts, tables, decision trees, and spatial layout — leveraging the visual cortex's ~10M bits/sec input channel. Apply to the *immediately preceding* answer or content under discussion, re-rendering it in visual form. Triggers include "/tldr", "tldr this", "make this visual", "viz this", "highest-bandwidth way", "render this dense".
---

# tldr

Re-render information using visual/structural layout instead of prose. Based on the cognitive research that conscious processing caps at ~10–50 bits/sec for language but the visual system feeds ~10M bits/sec — so spatial layout, diagrams, and structural compression beat paragraphs for the same idea.

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
5. **One callout, at the end.** A single bold line that fuses the insight. Not a "summary" section. Not bullet points restating what's above.
6. **Match the user's language.** If they wrote in Chinese, respond in Chinese (but the visuals are language-neutral, so they cost almost nothing to translate).

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

1. **Identify the source content.** Usually the user means "the previous answer" or "the info we were just discussing." If ambiguous, ask in one line.
2. **Extract the 3–6 load-bearing facts.** Everything else is filler.
3. **Pick a primitive per fact** using the matching table above.
4. **Stack them top-to-bottom in order of importance** — heaviest insight first, supporting detail below.
5. **Write the one callout line at the end.** This is the only sentence allowed to do synthesis work.

## Example transformation

**Before** (~120 words, ~50 bits/sec channel):

> Reading and listening hit roughly the same bottleneck because the conscious mind only processes about 10 to 50 bits per second. Reading averages around 240 to 260 words per minute and listening peaks around 275 words per minute when sped up. The visual system can take in millions of bits per second of raw input, which is why diagrams and visualizations can communicate so much more efficiently than the same information rendered as prose. So the real lever is not switching from text to audio but matching the modality to the content type.

**After** (~3 sec to grasp):

```
   带宽对比
   ════════
   视觉原始输入   ████████████████████████   10M bits/s
   阅读           ▌                          50 bits/s
   听力           ▌                          39 bits/s
                                             ↑ 同一个天花板

   → 改通道（文字→语音）几乎没用；改模态（语言→视觉）才有用
```

## Notes on rendering

- ASCII box characters: `┌ ┐ └ ┘ ─ │ ├ ┤ ┬ ┴ ┼`
- Bars: `█ ▓ ▒ ░ ▌ ▎ ▏` (full → empty)
- Arrows: `→ ← ↑ ↓ ↔ ↕ ↗ ↘ ─→ ══>`
- Bullets when unavoidable: `● ○ ◆ ◇ ★`
- Keep line width ≤ ~70 chars so it renders cleanly in terminal + Obsidian + web chat.
- Markdown tables render in all three contexts; ASCII tables render everywhere but are bulkier — prefer markdown tables unless alignment matters.
