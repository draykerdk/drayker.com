# drayker.com — Drayker institutional site

The institutional presentation of Drayker: what the organization is, what each part of the system does, and how the whole thing fits together.

Companion to **[drayker.org](https://drayker.org)**, the volunteers portal. Participation lives there — the open-functions board and the volunteer application are not duplicated here, they are handed over to the portal.

The production site is the institutional presentation from the Drayker 2.3
static Design Component. Its design, content structure and animated mark come
from the source package maintained in `drayker.org`; this repository contains
the generated deployment artifact for the `.com` domain.

## `index.html` in this repository is generated

Do not edit it by hand. It is produced from the component in [`draykerdk/drayker.org`](https://github.com/draykerdk/drayker.org):

```bash
# in a checkout of draykerdk/drayker.org
node tools/make-com.js ../drayker.com-site/index.html
```

One component, two sites. The generator selects the `.com` presentation,
points participation links to `https://drayker.org`, and writes the production
metadata for `https://drayker.com`. **Content and component behavior are edited
in `drayker.org/index.html` and regenerated here.**

`support.js` is the generated Design Component runtime and is copied as-is.
`assets/` contains the official logo and icon kit required by the generated
page. `.nojekyll` keeps GitHub Pages from interpreting `{{ … }}` component
bindings as Liquid.

## Production

The site is published at **[drayker.com](https://drayker.com)** through GitHub
Pages from `master` and is indexable. The repository contains:

- `CNAME` with the production custom domain;
- canonical and Open Graph metadata for `https://drayker.com`;
- no staging `noindex` directive;
- institutional navigation without a public contribution hub;
- explicit handoff from participation actions to `drayker.org`.

## Publishing an update

After changing the source component in `drayker.org`:

1. Run `node tools/make-com.js ../drayker.com-site/index.html` from the
   `drayker.org` checkout.
2. Copy `support.js` and the required `assets/` from the same source revision.
3. Run the static checks against the generated `index.html`.
4. Publish through a pull request and verify the custom domain after GitHub
   Pages reports the build as complete.

## Running it locally

```bash
python3 -m http.server 8767
```

From a sibling `drayker.org-site` checkout, validate the generated component:

```bash
node ../drayker.org-site/tools/render-check.js index.html
git diff --check
```

Site content is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); the code is under the license in `LICENSE`.
