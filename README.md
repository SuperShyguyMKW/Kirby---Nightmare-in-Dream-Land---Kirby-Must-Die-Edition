# Kirby - Nightmare in Dream Land - Kirby Must Die Edition
Author: SuperShyguy MKW

Base ROM:
- Kirby: Nightmare in Dream Land
- Region: USA
- Platform: Game Boy Advance

Patch format:
- BPS

Distribution note:
- you can distribute the .bps patch, but give me credit.
- Users must apply the patch to their own clean copy of the game.

==================================================
GENERAL GOAL
==================================================

This hack creates a harder version of Kirby: Nightmare in Dream Land.

Main changes:
- Kirby receives much more damage (3 points per hit).
- Bosses have increased HP.
- Regular enemies are unchanged.
- Sub-bosses were left unchanged

==================================================
KIRBY DAMAGE MODIFICATION
==================================================

Goal:
- Make Kirby lose 3 health points per normal hit instead of 1.

Kirby health system:
- Full HP: 48 decimal / 30 hex
- 1 health point: 8 decimal / 08 hex
- Original damage: 8 decimal / 08 hex
- Modified damage: 24 decimal / 18 hex

RAM address used during research:
- Kirby HP: 02005588

Observed original behavior:
- Full HP: 30 hex
- After one normal hit: 28 hex
- This means Kirby originally lost 08 hex / 8 decimal damage.

ROM offset:
- 0001AC54

Original bytes:
- 00 7A

Modified bytes:
- 18 20

Technical explanation:
- 00 7A originally reads damage from the enemy data.
- 18 20 changes the routine to use fixed 24 damage.
- The following instruction converts it into negative damage.
- Kirby now loses 24 internal HP per hit.

Expected result:
- Full HP: 30 hex
- After one normal hit: 18 hex
- Kirby loses 3 health points per hit.

==================================================
BOSS HP CHANGES
==================================================

Whispy Woods:
- Original HP: 60 decimal / 3C hex
- Modified HP: 120 decimal / 78 hex
- ROM offset: 0074C158
- Original bytes: 3C 00
- Modified bytes: 78 00

Paint Roller:
- Original HP: 60 decimal / 3C hex
- Modified HP: 120 decimal / 78 hex
- ROM offset: 0074B2DC
- Original bytes: 3C 00
- Modified bytes: 78 00

Mr. Shine / Luna:
- Original HP: 30 decimal / 1E hex
- Modified HP: 90 decimal / 5A hex
- ROM offset: 00748790
- Original bytes: 1E 00
- Modified bytes: 5A 00

Mr. Bright / Sol:
- Original HP: 30 decimal / 1E hex
- Modified HP: 90 decimal / 5A hex
- ROM offset: 007487BC
- Original bytes: 1E 00
- Modified bytes: 5A 00

Kracko:
- Original HP: 60 decimal / 3C hex
- Modified HP: 150 decimal / 96 hex
- ROM offset: 00749540
- Original bytes: 3C 00
- Modified bytes: 96 00

Heavy Mole:
- Original HP: 60 decimal / 3C hex
- Modified HP: 120 decimal / 78 hex
- ROM offset: 0074B308
- Original bytes: 3C 00
- Modified bytes: 78 00

Meta Knight:
- Original HP: 60 decimal / 3C hex
- Modified HP: 120 decimal / 78 hex
- ROM offset: 00749514
- Original bytes: 3C 00
- Modified bytes: 78 00

King Dedede:
- Original HP: 100 decimal / 64 hex
- Modified HP: 150 decimal / 96 hex
- ROM offset: 00748764
- Original bytes: 64 00
- Modified bytes: 96 00

Nightmare Orb:
- Original HP: 60 decimal / 3C hex
- Modified HP: 70 decimal / 46 hex
- ROM offset: 0074B334
- Original bytes: 3C 00
- Modified bytes: 46 00

Nightmare:
- Original HP: 60 decimal / 3C hex
- Modified HP: 77 decimal / 4D hex
- ROM offset: 0074956C
- Original bytes: 3C 00
- Modified bytes: 4D 00

==================================================
IMPORTANT NOTES
==================================================

Mr. Shine and Mr. Bright:

- This fight works differently because both bosses share the boss bar.
- Each one originally had 30 HP.
- They were first tested with doubled HP, but the final decision was to triple both to 90 HP.
- Final values:
  - Moon: 1E 00 -> 5A 00
  - Sun: 1E 00 -> 5A 00

Kracko:
- Kracko was increased more than most bosses.
- Final HP is 150 instead of 120.

Heavy Mole:
- Heavy Mole was kept at 120 HP.
- Increasing it too much would make the fight too long.

King Dedede:
- Dedede was increased to 150 HP.
- This keeps the fight harder without making it excessive.

Nightmare:
- Nightmare Orb and Nightmare HP were only slightly increased.
- This keeps the final battle harder but still fair.

Sub-bosses:
- Sub-bosses were left unchanged.
- They have several variants and are already reasonably balanced.

==================================================
FINAL PATCH SUMMARY
==================================================

Kirby damage:
0001AC54: 00 7A -> 18 20

Boss HP:
- 0074C158: 3C 00 -> 78 00   Whispy Woods
- 0074B2DC: 3C 00 -> 78 00   Paint Roller
- 00748790: 1E 00 -> 5A 00   Mr. Shine / Moon
- 007487BC: 1E 00 -> 5A 00   Mr. Bright / Sun
- 00749540: 3C 00 -> 96 00   Kracko
- 0074B308: 3C 00 -> 78 00   Heavy Mole
- 00749514: 3C 00 -> 78 00   Meta Knight
- 00748764: 64 00 -> 96 00   King Dedede / DDD
- 0074B334: 3C 00 -> 46 00   Nightmare Orb
- 0074956C: 3C 00 -> 4D 00   Nightmare

==================================================
VERSION NOTE
==================================================

This version is designed as a hard mode challenge for experienced players.

Normal mode becomes much harder because Kirby takes heavy damage.
Extra mode and Meta Knightmare become especially punishing, since the player can die in 1 hit.

