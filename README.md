# QR Studio

Live demo: https://itsadityakr.github.io/qr-studio/

This repository holds the generated production build of QR Studio and nothing
else. Every file here is compiled output: a static `index.html` and a folder of
hashed, minified JavaScript and CSS. The entire contents are regenerated and
overwritten whenever a new build is deployed, so any change made directly in this
repository is temporary and will disappear on the next deploy. The application
source is maintained separately at
[itsadityakr/qr-studio-code](https://github.com/itsadityakr/qr-studio-code).

## What this repository is

- The deploy target for GitHub Pages. The contents of this repository are what a
  visitor to the live demo actually downloads and runs.
- A snapshot of one specific build. The hashed filenames under `assets/` change
  from build to build, which is what allows the site to be cached aggressively
  and still update reliably.
- An archive of what was shipped. The commit history is a record of past
  deployments rather than a record of development work.

## What this repository is not

- **Not the source code.** There is no application source, no configuration, and
  no dependency manifest here. The files under `assets/` are minified build
  artifacts and are not intended to be read or edited by hand.
- **Not the issue tracker for the application.** Bugs in the tool itself, feature
  requests, and questions about behaviour belong in the source repository, where
  they can actually be fixed.
- **Not a place to send pull requests.** A pull request against this repository
  would modify build output, and that output is replaced wholesale on the next
  deploy. Changes must be made in the source and then rebuilt.

Contributors should work in
[itsadityakr/qr-studio-code](https://github.com/itsadityakr/qr-studio-code).

## About the app

QR Studio is a QR code generator that runs entirely in the browser. You provide
the content to encode and the tool produces a QR code from it, with control over
colours and a set of templates for starting from a ready-made look rather than
configuring everything from scratch. The finished code can be exported as a PNG
image for use elsewhere.

The application is a single-page build that mounts into a `<div id="root">`
element in `index.html`. It loads no external scripts or stylesheets at runtime,
so everything it needs is contained in the files in this repository.

## Contents

```
.
├── index.html                     Build entry point
├── assets/
│   ├── index-C6ONk-Lt.js          Minified application bundle (hashed filename)
│   └── index-CZSasPuG.css         Minified stylesheet (hashed filename)
├── vite.svg                       Favicon referenced by index.html
├── LICENSE
└── README.md
```

The hashed portion of each filename under `assets/` is generated at build time
and will differ in future deploys. Treat the names above as accurate for the
current build only; `index.html` is always the authoritative reference for which
asset files are in use.

## Known issue with this build

The `<title>` in `index.html` still reads `qr-generator`, the project's earlier
name, so the browser tab and bookmarks for the live site show that instead of
"QR Studio". This cannot be fixed here in any lasting way, because `index.html`
is regenerated on every deploy. The title needs to be corrected in the source
repository before the next build is published.

## Deployment

This repository is published with GitHub Pages, which serves the files at the
repository root exactly as they are, with no server-side processing or build step
of its own.

The workflow is: development happens in the source repository, a production build
is produced there, and the resulting output directory is copied into this
repository and committed. Publishing a new version therefore means replacing the
files here with a fresh build rather than editing them.

No CI configuration or automation workflow is committed in this repository, so
the exact publishing mechanism is defined outside of it. Refer to the source
repository for the build and release process.

## Reporting an issue

Please open issues in the source repository:

https://github.com/itsadityakr/qr-studio-code/issues

Issues opened against this repository cannot be fixed here, since the fix has to
land in the source and be rebuilt. When reporting a problem with the live site,
it helps to include the browser and version, the steps to reproduce, the input
you were encoding, and any errors shown in the browser console.

## License

Released under the MIT License. See [LICENSE](LICENSE).

Copyright (c) 2025 Aditya Kumar.
