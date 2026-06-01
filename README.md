# tortoise-deploy-patches

[![Lint status][badge-lint-status]][badge-lint-status-url]

This repository contains patches for [Tortoise-WoW][tortoise-wow] that are
applied when building the Docker images for [tortoise-deploy][tortoise-deploy].

The patches are strictly for:

- Correcting problems that would cause build failures, runtime crashes, or
  database corruption.
- Making Docker-specific adjustments that would not be appropriate to include
  upstream.

At no point will a patch be added that changes the behavior of the server or
otherwise alters its functionality.

Once a patch is no longer needed, it will be removed from this repository.
Therefore, there may be times when this repository contains no patches at all.

## Layout

Tortoise-WoW is built from two branches. Patches are organized so that the same
source can be shared across the resulting builds while still allowing
build-specific adjustments:

- `all/*.patch` is applied to every build.
- `stable/*.patch` is applied only to the `stable` build (the `main` branch).
- `unstable/*.patch` is applied only to the `unstable` build (the `1181dev`
  branch).

The build-specific directories are optional; create them only when an actual
patch needs a home.

## A note on licensing (`GPL-2.0-or-later` vs `AGPL-3.0-or-later`)

A patch is a derivative work of the file it modifies, so each patch here is
licensed to match the license of its target file, never relicensed.

Tortoise-WoW's repository-level `LICENSE` claims `AGPL-3.0-or-later`, but its
individual source files carry MaNGOS-lineage `GPL-2.0-or-later` headers (the
project is a fork of VMaNGOS, itself descended from MaNGOS). That root
`AGPL-3.0-or-later` choice can validly cover only Tortoise-WoW's own original
files; the inherited MaNGOS-lineage files remain `GPL-2.0-or-later` (the _or
later_ clause is what permits redistributing them within a v3-family combined
work).

Accordingly, a patch that modifies a MaNGOS-lineage file (such as
`CMakeLists.txt`) is `GPL-2.0-or-later`, and a patch that modifies a
Tortoise-WoW-original file would be `AGPL-3.0-or-later`. This is decided per
file. Every patch currently in this repository targets MaNGOS-lineage files and
is therefore `GPL-2.0-or-later`.

## Licenses

- [`GPL-2.0-or-later`][license-gpl-2.0-or-later] (Patches, matching
  Tortoise-WoW source)
- [`AGPL-3.0-or-later`][license-agpl-3.0-or-later] (Workflow files)
- [`CC-BY-SA-4.0`][license-cc-by-sa-4.0] (Documentation)
- [`CC0-1.0`][license-cc0-1.0] (Configuration files)

This project follows the [REUSE specification][reuse-spec].

[badge-lint-status]: https://github.com/mserajnik/tortoise-deploy-patches/actions/workflows/lint.yaml/badge.svg
[badge-lint-status-url]: https://github.com/mserajnik/tortoise-deploy-patches/actions/workflows/lint.yaml
[tortoise-wow]: https://github.com/Penqle/tortoise-wow
[tortoise-deploy]: https://github.com/mserajnik/tortoise-deploy
[license-agpl-3.0-or-later]: LICENSES/AGPL-3.0-or-later.txt
[license-gpl-2.0-or-later]: LICENSES/GPL-2.0-or-later.txt
[license-cc-by-sa-4.0]: LICENSES/CC-BY-SA-4.0.txt
[license-cc0-1.0]: LICENSES/CC0-1.0.txt
[reuse-spec]: https://reuse.software/spec/
