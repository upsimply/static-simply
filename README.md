# static-simply

The starter a static site built with AI on upsimply begins from: one HTML page,
Tailwind CSS and Alpine.js.

- `site/` is the site. It is copied into the site's document root as the first
  commit of the site's own version history, and the AI builder edits it from
  there. Nothing outside `site/` reaches a site.
- `site/src/app.css` is the Tailwind entry point. The server compiles it to
  `site/assets/app.css` with the Tailwind CLI after every change, so that file
  is never committed or edited by hand.
- `site/assets/alpine.min.js` is Alpine.js 3.17.5, vendored so the site loads
  no script from another host.
- `VERSION` is the release's version.

## Working on it locally

```sh
npx @tailwindcss/cli@4.3.5 -i site/src/app.css -o site/assets/app.css --watch
```

## Releasing

1. Bump `VERSION` and commit.
2. `git tag v1.2.3 && git push origin v1.2.3`

The Release workflow builds the stylesheet once as a check, packages the
repository as `static-simply-v1.2.3.tar.gz` with its SHA-256 and a build
provenance attestation, and publishes the release. The panel gives new sites
the newest release as soon as it is published.
