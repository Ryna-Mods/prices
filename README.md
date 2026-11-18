# Prices by Ryna

A mod of [Ryna](https://github.com/Ryna-Mods/ryna) for World of Warcraft: Forever. Puts what a vendor pays for an item, which vendor sells it, and what the auction house asks, on every
item tooltip, away from vendors too.

- **Vendor prices** from the game's own item data, on any tooltip.
- **Auction prices**: one snapshot of the auction house per visit, never anything about a seller.
- **Everyone's pooled prices**, when you use the Ryna app: they come down with each sync into Ryna
  Core's `Data/vendors.lua` and `Data/auctions.lua`, which the game reads at login or `/reload`.
- `/ryna prices` for its settings.

Nothing in chat, nothing done for you.

## Installing

Prices needs **Ryna Core** (the folder `Ryna_Core`). Get both one of these ways:

- **With the Ryna app** ([download](https://github.com/MaddisonM79/ryna_agent/releases/latest)),
  which installs them and keeps them up to date.
- **The bundle**: every Ryna addon in one zip, from
  [Ryna-Mods/ryna](https://github.com/Ryna-Mods/ryna/releases/latest).
- **By hand**: this repository's releases hold `Ryna_Prices-<version>.zip`; unzip it into
  `Interface/AddOns` beside `Ryna_Core`.

## Working on it

`Ryna_Prices/` is the addon. Its tests (`test/`) run it against a fake client and the real core
addon, the oldest one Prices claims to work with ([`core.json`](core.json)), which
`node scripts/core.mjs` fetches into `.core/`.

```bash
scripts/check.sh
```

That is everything CI runs: luacheck, the strings (`tools/strings.mjs`: every string the code uses
is in `Locales/enUS.lua` and in each locale's template) and the tests. It needs Lua (5.1 is what the
game runs), [luacheck](https://github.com/lunarmodules/luacheck) and Node.

The core API level Prices needs is `## X-Ryna-API` in [`Ryna_Prices.toc`](Ryna_Prices/Ryna_Prices.toc);
its version is `## Version` there, and nowhere else. A release is a signed tag `vX.Y.Z` that matches
it; the bundle then names that release in its `bundle.json`
([how](https://github.com/Ryna-Mods/ryna/blob/main/RELEASING.md)).

## Where it came from

Prices was written in [MaddisonM79/ryna_agent](https://github.com/MaddisonM79/ryna_agent)
(`mods/wow/prices`), and its history up to 0.5.0 is there. Bugs and requests go to
[ryna_agent's issues](https://github.com/MaddisonM79/ryna_agent/issues).

## Licence

MIT.
