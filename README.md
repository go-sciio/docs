# docs

[![docs](https://github.com/go-sciio/docs/actions/workflows/docs.yml/badge.svg)](https://github.com/go-sciio/docs/actions/workflows/docs.yml)
[![License](https://img.shields.io/badge/license-BSD--3--Clause-3E516B?style=flat-square)](LICENSE)

**The go-sciio documentation site**, published at
<https://go-sciio.github.io/docs/>.

go-sciio is **planned** (wave 2 of the [go-scikit roadmap](https://github.com/go-scikit/roadmap),
[PLAN.md](https://github.com/go-scikit/roadmap/blob/main/PLAN.md) and
[STATUS.md](https://github.com/go-scikit/roadmap/blob/main/STATUS.md)): no library
exists yet. The site says what the organisation will cover and what each format
will be validated against, with one page per planned package: `h5`, `mat`,
`netcdf`, `fits`, `npy`, `mtx`, `wav` and `flac`.

A [Hugo](https://gohugo.io/) site with the [tannevaled/hextra](https://github.com/tannevaled/hextra)
fork of the [Hextra](https://github.com/imfing/hextra) theme (pinned to v0.16.0),
built the same way as the [go-bignum documentation](https://github.com/go-bignum/docs),
with go-sciio's branding.

## Versions

`params.libraries` in `hugo.yaml` names the release of each library the pages
describe, or `main` while it has no tag. A version of the documentation is
**the newest minor version among the tagged ones**, or `main` while none is
tagged. No package is released, so the site is version `main`:

| Source | Published under |
| --- | --- |
| branch `main`, with `params.libraries` in `hugo.yaml` | `https://go-sciio.github.io/docs/<MAJOR.MINOR>/`, or `/docs/main/` |
| the newest version (else `main`) | also `https://go-sciio.github.io/docs/latest/` |

`https://go-sciio.github.io/docs/` redirects to `latest/`. Each push to `main`
replaces the directory of the version it describes, and nothing else. When a
package is released, its entry in `params.libraries` becomes its tag, and the
old version's pages stay published beside the new one.

## Layout

| Path | What |
| --- | --- |
| `content/en/` | the pages; `_index.md` is the home, one directory per planned package, `weight` orders the sidebar |
| `i18n/en.yaml` | the site's strings, beside the theme's |
| `hugo.yaml` | `baseURL`, the library versions described, the navbar (version › theme › search › GitHub), the brand mounts |
| `layouts/_partials/custom/version-select.html` | the version selector (reads `versions.json`) |
| `layouts/_partials/custom/content-begin.html` | the outdated-version banner (reads `versions.json`) |
| `layouts/_partials/favicons.html` | the brand's favicons |
| `assets/css/custom.css` | the brand slate as Hextra's primary colour, the table headers |
| `themes/hextra` | submodule: [tannevaled/hextra](https://github.com/tannevaled/hextra), pinned to v0.16.0 |
| `branding` | submodule: [go-sciio/brand](https://github.com/go-sciio/brand) (the mark, its PNGs and ICO) |
| `scripts/publish-version.sh` | puts one build into a `gh-pages` checkout and rewrites `versions.json`, `latest` and the root redirect |

## Working locally

```sh
git clone --recurse-submodules https://github.com/go-sciio/docs.git
cd docs
mkdir -p data && sh themes/hextra/scripts/page-history.sh > data/pagehistory.json
hugo server --baseURL http://localhost:1313/docs/main/
```

then open <http://localhost:1313/docs/main/>. Hugo 0.146 or later; no Python,
no Node.

## Publication

`.github/workflows/docs.yml`:

| Job | When | What |
| --- | --- | --- |
| `build` | pull requests, `main` | builds with `--baseURL …/docs/<version>/`, checks internal links and anchors (lychee, offline), uploads the site |
| `links` | pull requests, `main` | fetches every external URL the pages name |
| `deploy` | `main` | `scripts/publish-version.sh` into `gh-pages` (started empty on the first deploy), then a commit and a push |

GitHub Pages serves the `gh-pages` branch.

## Licence

BSD-3-Clause.
