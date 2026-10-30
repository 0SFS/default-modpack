# Default modpack

The mods every 0SFS flight starts with. Everything the simulator flies is a mod,
and this modpack is the list the flight installs by default:

| Mod | Kind | Brings in |
| --- | --- | --- |
| [C172](https://github.com/0SFS/C172) | aircraft | IO320 engine, rotating-prop |
| [SF-50](https://github.com/0SFS/SF-50) | aircraft | FJ33 engine |
| [F-35B](https://github.com/0SFS/F-35B) | aircraft | F135 engine, external tank, AIM-120, GBU-12, GBU-32, AIM-9X, ASRAAM, Paveway IV, GAU-22 pod |
| [DJI-Mini2](https://github.com/0SFS/DJI-Mini2) | aircraft | DJI-Quadcopter, Quadcopter, multirotor, rotating-prop, camera-gimbal, DJI-FC7303, drone-camera |
| [DJI-Air-2S](https://github.com/0SFS/DJI-Air-2S) | aircraft | DJI-Quadcopter, Quadcopter, multirotor, rotating-prop, camera-gimbal, DJI-FC3411, drone-camera |
| [camera-preview](https://github.com/0SFS/camera-preview) | plugin | |

A modpack is a mod of kind `modpack`: its `public/0sfs-mod.json` lists mods in
`dependencies` and carries nothing else. Each listed mod brings its own
dependencies, so the pack names only the top of each tree. The order of the
aircraft is the order of the aircraft gallery.

## Kinds

| Kind | What it contributes |
| --- | --- |
| `aircraft` | An aircraft family, its variants, flight profiles and payload stations |
| `engine` | An engine and its sound |
| `component` | A part other mods share: a propeller, a gimbal, a camera, a flight model |
| `payload` | One store or external tank |
| `plugin` | A feature, such as the camera preview |
| `modpack` | A list of mods to install together |

## In the flight

[fly](https://github.com/0SFS/fly) links this package and every mod it brings in.
Its `scripts/link-packs.mjs` serves their files and writes their manifests into
`src/flight/mods/bundledMods.ts`, and the flight installs the pack before it
reads the aircraft selection. Nothing is fetched from GitHub for them, and the
pack's mods cannot be removed. The Mods tab shows the pack as the root of the
installed tree.

To change what the flight ships, edit `dependencies` here, add any new mod as a
`file:` dependency in fly's `package.json`, then run `npm install` and `node
scripts/link-packs.mjs` in fly. `npm run dev`, `build` and `test` also run
`link-packs`.

```sh
npm run validate
```

Topics: `0sfs-mod` and `0sfs-modpack-mod`. [Modding guide](https://github.com/0SFS/docs/blob/main/modding.md) describes discovery and installation.

## Community

- [Code of conduct](https://github.com/0SFS/.github/blob/main/CODE_OF_CONDUCT.md)
- [Contributing](https://github.com/0SFS/.github/blob/main/CONTRIBUTING.md)
- [License](LICENSE)
- [Security](https://github.com/0SFS/.github/blob/main/SECURITY.md)
