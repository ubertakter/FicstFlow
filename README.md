# FicstFluids documentation

The player manual for FicstFluids, a Satisfactory mod that replaces the game's fluid mechanics.
It is written in AsciiDoc and built with [Antora](https://antora.org/), in the layout
[docs.ficsit.app](https://docs.ficsit.app) expects. Bug reports for the mod go to this repository's Issues.

## Layout

- `docs/antora.yml`: the component's name and title.
- `docs/modules/ROOT/nav.adoc`: the sidebar.
- `docs/modules/ROOT/pages/`: one `.adoc` file per page.
- `docs/modules/ROOT/images/`: screenshots, referenced as `image::name.png[]`.

## Preview locally

Needs Node.js. Antora finds no pages in a repository with no commits; after the first commit
it builds from the files as they are on disk, committed or not.

```
npm install
npm run build
```

Then open `build/site/index.html`.
