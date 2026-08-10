# drayker.com — Drayker institutional site

The institutional presentation of Drayker: what the organization is, what each part of the system does, and how the whole thing fits together.

Companion to **[drayker.org](https://drayker.org)**, the volunteers portal. Participation lives there — the open-functions board and volunteer flow are not duplicated here. This site contains the institutional case for each of the twenty components/concepts and the public funding and partnership route.

## `index.html` in this repository is generated

Do not edit it by hand. It is produced from the component in [`draykerdk/drayker.org`](https://github.com/draykerdk/drayker.org):

```bash
# in a checkout of draykerdk/drayker.org
node tools/make-com.js ../drayker.com-site/index.html
```

One component, two sites. The generator changes the `SITE` build constant, the cross-site link and the document head; it can also add a staging `noindex` when explicitly enabled. **Content for these pages is edited in `drayker.org/index.html`** and regenerated here.

`support.js` is the generated Design Component runtime and is also copied as-is. `.nojekyll` keeps GitHub Pages from interpreting `{{ … }}` component bindings as Liquid.

## Deployment

The canonical site is live at **[drayker.com](https://drayker.com)** through GitHub Pages and the repository `CNAME`. The generated document is indexable: `STAGING = false` in `drayker.org/tools/make-com.js`, and the deployed `index.html` has no staging `noindex` directive.

After changing institutional content in `drayker.org`:

1. run the generator into this repository;
2. run the render checks from `drayker.org` against the generated file;
3. confirm the diff contains only intended generated changes;
4. publish and verify the canonical domain.

DNS and `www` redirects are deployment infrastructure; they should be changed only when a concrete domain route is required, not pre-created for every conceptual component.

## Running it locally

```bash
python3 -m http.server 8767
```

Site content is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); the code is under the license in `LICENSE`.
