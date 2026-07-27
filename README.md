# Apps for CommandDeck

The store CommandDeck reads. Everything here is static: `catalog.json` is the
index and the packages sit beside it under `packages/`.

Point CommandDeck at this repository in the Store view - the repository URL is
enough, the client works out the raw path to `catalog.json` itself.

## Layout

    catalog.json                     the index clients fetch
    packages/<id>/<version>/         one folder per published version
      <id>-<version>.cdpkg           the package
      icon.png / preview.png         extracted for the store card

## Publishing

Never edit `catalog.json` by hand - it is generated from the packages, so an
edited index drifts from the files it describes and clients fail the checksum.
Run CommandDeck's `scripts/store-repo.ps1` instead; it rebuilds everything,
regenerates the index, commits and pushes.

## Submissions

Open a pull request adding your package under `packages/`. The index is
regenerated on merge, so you do not need to touch `catalog.json`.
