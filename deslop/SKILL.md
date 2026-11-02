---
name: deslop
description: Detect and remove AI design slop from generated UI. Use whenever you create or edit UI code (CSS, HTML, JSX/TSX, Vue, Astro, Svelte): run the deslop scanner before declaring UI work done, fix or justify every finding, and apply the anti-slop principles when writing new interface code.
---

# Deslop

AI-generated UI has a recognisable house style: Inter on everything, a purple-to-blue gradient hero, pillowy cards floating on giant soft shadows, glassmorphism, emoji bullets, an un-themed shadcn kit, and copy that says "Supercharge your workflow — seamlessly." Users can smell it instantly, and it makes every product look like the same product. Deslop is the checkpoint that stops it shipping: a zero-dependency scanner with 48 rules, including the first rule pack for RTL (Urdu/Arabic) interfaces.

The full project lives at https://github.com/iRehmanAhmad/deslop and a free live URL checker is at https://deslop-checker.rehmanahmad.com.

## When to Use This Skill

- After creating or editing any UI file (CSS, HTML, JSX/TSX, Vue, Astro, Svelte), before telling the user the work is complete
- When generating a landing page, dashboard, or component from scratch and you want it to avoid the generic AI look
- When reviewing AI-generated frontend code for default-framework tells (un-themed shadcn/Tailwind kits, the cream + serif default)
- When building or fixing Urdu/Arabic (RTL) interfaces, where the usual design checkers do not look

## What This Skill Does

1. **Scans the changed code**: Runs the deslop CLI over the files you touched and reports every finding with a file and line.
2. **Enforces the gate**: FAIL findings (Inter as the only font, purple-to-blue gradients, lorem ipsum left in the UI) must be fixed; warnings are fixed or justified in one line each.
3. **Guides new UI**: Applies anti-slop principles while writing fresh interface code, so the defaults never appear in the first place.
4. **Checks RTL**: Flags RTL-specific problems such as Latin display fonts on Arabic script, physical CSS properties that break mirroring, and missing `dir="rtl"`.

## How to Use

### Basic Usage

Clone the scanner once, then run it over the area you changed before declaring UI work done:

```
Clone https://github.com/iRehmanAhmad/deslop, then run:
node bin/deslop.js ./src
```

Then fix every FAIL finding, fix or justify every warning, and report the scan result with your summary ("deslop: 0 fail").

### Advanced Usage

```
node bin/deslop.js ./src --format json
```

Use the JSON output to process findings programmatically, or paste a published page URL into the free checker at https://deslop-checker.rehmanahmad.com for a Slop Score with plain-language fixes.

## Example

**User**: "Build a landing page for my invoicing tool."

**Output**:
```
Page built. Before calling it done I ran deslop over the new files:
- FAIL fixed: purple-to-blue gradient hero -> solid ink background with a real product screenshot
- FAIL fixed: Inter as the only font -> Fraunces display + Inter text pairing
- WARN fixed: "Get Started" button copy -> "Create your first invoice"
- WARN justified: rounded-full kept on the pricing toggle (established design-system pattern)
deslop: 0 fail
```

## Tips

- A project's own design tokens and documented conventions outrank generic rules: if the brand genuinely is a violet gradient, the finding gets a justification, not a redesign.
- The point is to catch *unchosen* defaults — the patterns an agent reaches for when it is not thinking — not to flatten deliberate design decisions.
- The full rule list, with the reasoning and fix for each rule, lives in `docs/RULES.md` in the deslop repository.

## Common Use Cases

- Gating AI-generated landing pages and marketing sites before they ship
- Cleaning up vibe-coded prototypes so they stop looking like every other AI-built site
- Reviewing generated dashboards and admin panels for un-themed component-kit defaults
- Auditing Urdu/Arabic interfaces for RTL mistakes other tools miss
