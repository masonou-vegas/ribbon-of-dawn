# Ribbon of Dawn

An original pseudo-3D rail shooter for the **Sega Genesis / Mega Drive**,
in the style of *Panorama Cotton* — built with SGDK on stock console
hardware, with no scaling or rotation chip. The perspective floor,
scaling sprites, and raster steering are all done with the plain VDP
tile and scroll hardware the machine actually has.

> This repository contains the playable ROM only. Download `rom.bin`
> and run it in a Genesis/Mega Drive emulator, on a flashcart, or on a
> MiSTer.

## The story

Miyu, a maid-café worker, is given angel wings by a magical ribbon and
sent to fight the yokai invasion — and the Daitengu, whose eternal
night has fallen over the land. Accompanied by the Ribbon itself, she
flies from the open sky down through a Tokyo highway, through a torii
gate into the swirling Cloud Road dimension, on to Mt. Fuji, and
finally to a night shrine for the showdown with the Daitengu.

## How the 3D works

The Mega Drive cannot scale or rotate sprites, so the perspective is
baked in ahead of time:

- Every floor pixel is inverse-projected to world coordinates offline,
  giving converging checkerboard lines and correctly accelerating
  stripes toward the bottom of the screen for free.
- Forward motion is animated with phase tilemaps drawn from a single
  shared tile library, so the floor scrolls in sub-tile steps instead
  of jumping 8 pixels at a time.
- Turns are a per-scanline horizontal scroll effect, weighted by
  depth, so the bottom of the floor shears far more than the horizon.
- Enemies, scenery, and bullets live in the same world coordinates as
  the floor and grow through pre-scaled sprite sizes as they approach.

## The game

- **3 stages, 3 bosses, 3 mid-bosses**
  - **Stage 1:** sky opening → descent to a Tokyo highway → torii gate
    → the Cloud Road dimension → the Cloud Road boss
  - **Stage 2:** the flight to Mt. Fuji → the Tengu Maid
  - **Stage 3:** the night shrine → the Daitengu, and the end of the
    eternal night
- **Branching routes:** gate posts in Stages 2 and 3 send you down a
  different sub-route (with its own waves and lighting) depending on
  which side of the screen you fly through — then the routes rejoin
  for the boss.
- **Weapon progression:** kills earn XP and level your shot up
  (levels 1–5: more bullets in flight, faster fire). Taking a hit
  drains XP and can knock you back down a level.
- **Elemental magic:** defeated enemies drop crystals. Fly into one to
  stock that element's magic, or shoot it first to cycle its element.
  Fire is a sweeping column attack, Water is a wider, harder-hitting
  one, and Wind is a shield bubble that eats a hit for you.
- **The Ribbon companion** trails Miyu, orbits her while you hold the
  fire button, and empowers a magic cast made while it orbits.
- **Speed control:** three flight speeds — fly fast for a bigger
  stage-clear bonus, and banked score converts into extra lives.
- **Tea Time:** after every boss, catch the falling crystals for
  points… or catch none of them for the secret bonus.
- **Destructible scenery, road hazards, boss phase changes,** a
  NORMAL/HARD difficulty option, stage select, and up to 10 lives
  shown as little Miyu faces.
- Original YM2612 + PSG soundtrack and sound effects.

## Controls

| Input | Effect |
|---|---|
| Left / Right | Steer (the floor shears; Miyu drifts) |
| Up / Down | Move Miyu up / down |
| C (hold) | Auto-fire (the Ribbon orbits you while held) |
| A | Cast the selected magic (Fire / Water / Wind) |
| B | Cycle the selected magic element |
| Start | Cycle flight speed: SLOW → CRUISE → FAST |

## Running it

- **Emulator:** open `rom.bin` in any Genesis/Mega Drive emulator
  (BlastEm, Genesis Plus GX, Kega Fusion, RetroArch…).
- **Real hardware:** copy `rom.bin` to a flashcart (EverDrive etc.)
  or run it on a MiSTer. NTSC, 60 fps.

## ROM details

| | |
|---|---|
| File | `rom.bin` |
| Size | 640 KB (655,360 bytes) |
| SHA-256 | `7B28BEB416709593DB8D4C826EDC1DB90E0DF28E22313C706DD8585335A2427D` |
| Platform | Sega Genesis / Mega Drive |
| Players | 1 |

## Credits

Game design, code, art, and music created for this project with SGDK
(the Sega Genesis Development Kit). An original work in tribute to —
not affiliated with — the *Cotton* series.
