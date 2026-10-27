Claude (Anthropic) generated

# ProcBot

**Proc and buff alerts for WoW: Wrath of the Lich King 3.3.5a (Warmane and other 3.3.5a servers).**

ProcBot shows your important procs and missing buffs as four glowing crescent arcs around
your character, plus a row of up to 4 icons above it. It works for every class and spec and
switches rules automatically when you change spec or dual spec.

Version 0.5.0 · Interface 30300 · MIT license

---

## What it shows

**Four arcs in an eye shape around your character**

| Arc | Default use | Example (Enhancement shaman) |
|---|---|---|
| Left | Main proc or stack build-up | Maelstrom Weapon, glows brighter per stack, full at 5 |
| Right | Shield, armor, form, presence or aura missing | Lightning Shield missing |
| Bottom | Weapon enchant missing or a second proc | Windfury / Flametongue missing or swapped |
| Top | Cooldown or another proc | Heroism ready (nobody Sated) |

- Priority is Left > Right > Bottom > Top. If two rules want the same arc, the higher one wins.
- Full procs get a bright core, a glow and shimmering rays. Partial stacks show a faint crescent.
- Missing-buff alerts pulse.

**Icon pop-ups:** up to 4 spell icons in a centered row above your character, always the
same size, for things like missing raid buffs or cooldowns.

Every class and spec comes with a ready-made rule set, and every rule can be moved, recolored,
reordered or turned off.

## Install

1. Download the zip and extract it.
2. Copy the `ProcBot` folder into `World of Warcraft\Interface\AddOns\`.
   The path must be `Interface\AddOns\ProcBot\ProcBot.toc`, not a folder inside a folder.
3. Enable ProcBot on the character select screen (AddOns button).
4. In game, type `/pb test` to see the layout, and `/pb` to open the settings.

## Quick start

1. `/pb` opens the settings window.
2. **Layout** tab: turn on Test mode, then adjust spacing, size and height until it fits your screen.
3. **Colors** tab: pick a color and brightness for each arc.
4. **Rules** tab: your spec is selected and marked with `*`. For each ability choose where it
   shows (Left, Right, Bottom, Top, Icon or Off) from the dropdown. Add up to 3 extra
   abilities per tab with the Extra pickers under the list.
5. Turn Test mode off. By default alerts only show in combat.

## Commands

| Command | Does |
|---|---|
| `/pb` | Open or close the settings window |
| `/pb test` | Show all arcs and 4 dummy icons |
| `/pb unlock` / `/pb lock` | Drag the arcs and icons up or down |
| `/pb enable` / `/pb disable` | Turn ProcBot on or off on all characters |
| `/pb combat` | Toggle "only in combat" (on by default) |
| `/pb spec` | Show the detected class, spec and profile |
| `/pb spec 1` / `2` / `3` | Choose spec by talent tree, left to right |
| `/pb spec pick` | Open the spec picker |
| `/pb reset` | Reset layout and colors (rules are kept) |
| `/pb export` / `/pb import` | Share settings as a text string |

`/procbot` works the same way. If another addon already uses `/pb`, only `/procbot` is registered.

## What to know

- **Spec detection.** ProcBot reads your spec from your talents and remembers it for each
  talent set, so it survives loading screens. If it can't tell (rare, right after login), a
  small window asks which spec you're playing. The Spec button in the settings opens it too.
- **Feral druids** switch between cat and bear rules by your current form.
- **Death knights** pick the presence they want for each spec in the Rules tab
  (default: Frost for Blood, Blood for Frost and Unholy).
- **Healer rules on a tank** (Beacon of Light, Earth Shield, Lifebloom, Grace, Riptide and so on)
  use your **focus target**. Set your tank as focus.
- **Reactive abilities** (Execute, Overpower, Revenge, Kill Shot, Rune Strike) need a hostile target.
- **Spells you haven't learned never fire,** so the default rules are safe on any spec.
- **Hidden automatically** while dead, on a taxi, in a vehicle, or mounted out of combat.
- **Profiles** are per character by default. Copy, rename, reset, or share them in the Profiles tab.
- **Sharing settings:** Export gives you a text string starting with `PB1:`. Paste it into
  Import on another character, account or PC. You can export everything, the layout only,
  or your class rules only.
- **Android / emulators:** if pasting into the game doesn't work, copy
  `WTF\Account\<ACCOUNT>\SavedVariables\ProcBot.lua` between installs instead.
  It holds every profile.

## Known limits

- **Spell IDs.** A few spell IDs were written from memory. On English clients rules also match
  by spell name, so most still work. If a rule never fires (or fires wrongly), please report
  the class, spec and rule name.
- **Non-English clients.** Rules rely on spell IDs only, so a wrong ID won't be caught by the
  name fallback. The "wrong weapon enchant" check reads English words from the weapon tooltip
  (Windfury, Flametongue, Earthliving, Poison, stone); use the "Any imbue" option instead.
- **UI language.** The settings window is in English only.
- **Testing.** Tested most on shaman. Other classes use the same engine but have had less
  play-testing, so their default rules are the most likely to need fixes.
- **One alert per arc and 4 icons max.** When more rules are active, the order in the Rules tab
  decides which ones show.
- **Only in combat by default.** Out-of-combat reminders (for example a missing raid buff
  before the pull) need "Only in combat" turned off for that profile.
- **No sounds** yet, only visuals.
- **Performance.** Each arc is drawn from many small textures. If you notice a drop on a
  low-end device, lower the ray count or turn off "Shimmering rays".
- **Glyph-based rules** (like the Life Tap glyph buff) only appear when the glyph is socketed.

## Reporting bugs

Please include: your class and spec, the rule name from the Rules tab, what you expected and
what happened. The output of `/pb spec` helps too.

## Credits

ProcBot by Radu, written with the help of Claude (Anthropic).
All code and textures are original, and no third-party libraries are used.

Inspired by Blizzard's spell activation overlays from later expansions and by the proc alert
idea from r/wowaddons. Settings window style inspired by HealBot and Shock and Awe;
import/export strings inspired by Dragon UI.

## License

MIT, see `LICENSE`. You can use, change and share ProcBot, as long as the copyright notice
stays with it.
