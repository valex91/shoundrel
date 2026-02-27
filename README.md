# Scoundrel

> A single-player roguelike card game — playable entirely in your terminal.

Based on the original [Scoundrel](http://www.stfj.net/art/2011/Scoundrel.pdf) by Zach Gage & Kurt Bieg.
Built in pure Bash with a custom TUI engine. No dependencies.

```
  ____  _                           _          _
 / ___|| |__   ___  _   _ _ __   __| |_ __ ___| |
 \___ \| '_ \ / _ \| | | | '_ \ / _` | '__/ _ \ |
  ___) | | | | (_) | |_| | | | | (_| | | |  __/ |
 |____/|_| |_|\___/ \__,_|_| |_|\__,_|_|  \___|_|
```

---

## Requirements

- **Bash 4.3+** (macOS ships with 3.2 — install via `brew install bash`)
- A terminal at least **80×24**
- UTF-8 support

## Running

```bash
./shoundrel
```

---

## How to Play

| Key | Action |
|-----|--------|
| `a` / `d` | Navigate cards |
| `e` | Pick selected card |
| `n` | Skip room |
| `p` | Start game (from menu) |

### Cards

| Suit | Type | Effect |
|------|------|--------|
| ♠ ♣ | Monster | Take damage equal to value |
| ♦ | Weapon | Equip on pickup, replaces previous |
| ♥ | Potion | Heal by value (max 20, once per turn) |

### Combat

- **Barehanded** — take full monster damage
- **With weapon** — damage = monster value − weapon value (min 0)
- Once a weapon is used, it can only fight monsters **weaker** than the last one it killed

### Room

- Each room has 4 cards — pick 3, the last carries over to the next room
- You may skip a room (cards go to the bottom of the deck)
- You cannot skip two rooms in a row

### Win / Lose

- **Lose** — HP reaches 0
- **Win** — clear the entire dungeon

---

## Project Structure

```
shoundrel        # entry point & game loop
lib/
  tui            # terminal control, cursor, drawing primitives
  draw           # positioned drawing utilities
  cards          # deck creation, card rendering
  array          # array utilities (splice, findIndex, longestMember)
  utils          # math helpers, error handling, version checks
```

---

## Notes

This project was built as a learning exercise in bash scripting — TUI rendering, state management, and game logic without any external tools or libraries.
