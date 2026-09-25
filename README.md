# Peter's Putt-Putt Pandemonium

A 2D side-view mini-golf game set around Quahog, starring Peter Griffin. Everything is in one file, `index.html`: HTML5 Canvas, plain JavaScript and Web Audio, with no libraries and no assets.

> **Personal fan project only.** Family Guy and its characters belong to Fox. Don't sell this or post it publicly.

## How to run

1. Download or clone this repo.
2. Double-click `index.html`, or drag it into Chrome, Firefox, Edge or Safari.

That's all. You don't need a server or a build step. (If you'd rather serve it, `python3 -m http.server` works too. Then open `http://localhost:8000`.)

## How to play

| Action | Control |
|---|---|
| Aim & power | Click (or touch) anywhere, **drag backward**, release to swing |
| Beer Boost / Stewie's Gadget / Brian's Advice | `1` / `2` / `3`, or click the buttons |
| Pause | `P` / `Esc` / the **II** button |
| Mute | `M` |
| Advance screens | Click / `Space` |

- **Beer Boost** gives your next shot 45% more power, then Peter burps.
- **Stewie's Gadget** rewinds your last shot and refunds its strokes, including a water penalty.
- **Brian's Advice** does nothing at all. That's the joke.
- More power-ups float around some holes. Hit them with the ball to collect them.
- Water costs a penalty stroke. At par + 6, Peter gives up and moves to the next hole.

## Holes

| # | Hole | Par | New hazard |
|---|---|---|---|
| 1 | Spooner Street | 2 | Just grass |
| 2 | The Griffin House | 2 | Hills |
| 3 | The Drunken Clam | 3 | Ramp + sand trap |
| 4 | Quahog Harbor | 3 | Water |
| 5 | Pawtucket Brewery | 3 | Moving keg |
| 6 | Quagmire's Front Lawn | 3 | Windmill |
| 7 | Brewery Vat Room | 4 | Island hopping over beer vats |
| 8 | Drunken Clam Back Alley | 4 | Windmill + water + sand |
| 9 | Spooner Street Showdown | 5 | Everything |
| ? | **Secret: The Chicken Fight** | 3 | A giant, hopping, ball-kicking chicken |

**Unlocking the bonus hole:** finish the 9 holes at par + 6 or better, or type `chicken` on the title screen.

## Features

- Drag-to-shoot with an aim preview, a power meter and a stroke counter
- Ball physics: gravity, bouncing, rolling friction, heavy sand drag, and pushes from moving kegs and windmill blades
- Peter reacts to every shot. Bad shots get excuses and good shots get over-the-top celebrations.
- Random cutaway gags after bad shots (six scenes)
- Title screen, pause menu, hole-complete screens and a final scorecard
- Synthesized sound effects for swings, hits, bounces, splashes, sand, cheering, burps and chicken squawks
- Best round, best score per hole and the bonus unlock are saved in `localStorage`

## Code layout (`index.html`)

The script is split into numbered sections:

1. Constants & canvas setup
2. Save data (`localStorage`)
3. Sound (Web Audio synth)
4. Dialogue: Peter's lines, Brian's advice, cutaway captions
5. Hole definitions (data only, so they're easy to edit or add to)
6. Game state
7. Level loading
8. Physics (circle vs. line-segment collision)
9. Shots, rules and power-ups
10. Particles, speech and floating text
11. Update loop
12–16. Drawing: helpers, characters, backgrounds, course, HUD and screens
17–19. Main draw, input and main loop

To add a hole, append an object to `HOLES` with a `ground` polyline, a `cup`, and any `sand`, `water`, `movers`, `windmills` or `pickups`.
