# AGOT Bank Management Insights (CK3 Submod)

This submod adds a safe, low-overhead bank dashboard linked to AGOT banking globals.

## What it does now
- Adds `Open Bank Dashboard` decision
- Supports per-bank selection for shareholders and directors
- Reads real AGOT bank values (caMixed infantry mercenary soldiers inspired by the Second Sons, depicted as a realistic unit card illustration.

A small group of hardened mercenaries with diverse appearances: different ages, ethnicities, and facial features. They wear mismatched, practical medieval gear — a mix of leather armor, chainmail, partial plate pieces, and scavenged equipment from different regions.

Some carry spears, others swords, shields, or short axes. Their gear is worn, patched, and battle-scarred. Clothing shows dust, sweat, dried blood, and travel wear.

Faces are visible and expressive: bearded men, shaved heads, scars, tired eyes, broken noses — experienced soldiers of fortune, not noble warriors.

Their stance is relaxed but ready, like veterans used to constant war. No heroic posing.

Background: subtle and blurred, suggesting a dusty encampment or battlefield in Essos, with muted tones and no strong focus.

Style: ultra-realistic, gritty medieval realism, grounded, no fantasy elements

Lighting: natural light, slightly warm but muted, soft shadows

Color palette: dusty browns, faded reds, dull metal, muted earth tones

Composition: portrait format, character-focused, clean framing for strategy game unit card, Crusader Kings III style

Negative prompt: uniform army, identical soldiers, full plate armor, fantasy armor, glowing effects, bright colors, stylized, cartoon, heroic pose, polished, clean, high fantasypital, loans, defaults, earnings, expenses)
- Renders custom dashboard widget with:
  - bank header and KPI lines
  - monthly trend history (12 snapshots)
  - debtor cards (borrowed/owed/projected gain)
  - manager panel with portrait
  - incoming payments list
- Renders custom policy matrix widget (options/suboptions/impact)
- Shows policy insights with projected gain/loss range
- Restricts policy actions to directors
- Writes policy profile directly to AGOT globals (`RiskLevel`, `InterestLevel`, `DividendLevel`)
- Includes shortcut to AGOT's own management window

## Performance/stability design
- Event-driven flow (no heavy always-on loops)
- No custom multicore/GPU assumptions (CK3 scripts do not support that)
- Additive approach to reduce override conflicts

## Install
1. Place this folder in your CK3 mod directory.
2. Enable AGOT.
3. Enable this submod **after AGOT** in load order.

## Workspace reference
Copied AGOT banking source files are under `AGOT_SOURCE_REFERENCE/` for fast development.
