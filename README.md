# HârnWorld Introductory Adventure: A Shower of Silver
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-adv-sos)](https://github.com/toastygm/hm-adv-sos/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-adv-sos&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-adv-sos)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-adv-sos/releases/latest&color=green)](https://github.com/toastygm/hm-adv-sos/releases/latest)

![Characters](assets/images/characters.jpg)

This module provides the adventure "A Shower of Silver", an introductory murder-mystery
adventure for the [HârnWorld](https://columbiagames.com/harnworld/)
fantasy setting, located around Jedes keep in the kingdom of Kaldor. However, this
adventure could be located in any fantasy setting or location with minimal adaptations.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic, with the exception of Actors.
Detailed descriptions of the actors has been provided in journal entries to facilitate
conversion to other game systems.

# Credits

This module is made possible by the hard work of Neil Thompson and other HârnWorld fans, and is provided at no
cost. This work is an adaptation of the adventure [A Shower of Silver](https://www.lythia.com/adventures/a-shower-of-silver/) available at
the HârnWorld fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Neil Thompson

**Contributors:** Matthias Janßen, Andy Gibson, Daniel Bell, and Allan Prewett

**Artists:** Richard Luscheck and Juha Makkonnen

**Playtest Referees:** Neil Thompson, Matthias Janßen, Andy Gibson, and Allan Prewett

**Playtesters:** Dave (no relation to Dan) Bell, Neil F (this character sheet is wrong!) Hepple, Robert L (George) Sanders, Dave Wilkinson, Andy Wouldham, Jörn Schmidt, Durk Vellema, Alexander Riedel, Hanna Fedderwitz, Ron Dill, Rob Duff, Michael Edmonds, J Patrick MacDonald, Jonathan Nicholas, Ken Snellings, Richard Black, Aaron Hay, Leigh Heron, David Hoey, and Jarick Prewett

**Adapted to Foundry VTT:** Tom Rodriguez

Thanks to Grant Dalgleish for permission to use the official ‘Sir Shernath Mirdarne’ illustration from the ‘Kaldor Kingdom Module’

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)", a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.



# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached
