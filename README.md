# drayker.com. Drayker institutional site

The institutional presentation of Drayker: what the organization is, what each part of the system does, and how the whole thing fits together.

Companion to **[drayker.org](https://drayker.org)**, the volunteers portal. Participation lives there. The open-functions board and volunteer flow are not duplicated here. This site contains the institutional case for each of the 25 public component repositories and the public funding and partnership route.

## `index.html` in this repository is generated

Do not edit it by hand. It is produced from the component in [`draykerdk/drayker.org`](https://github.com/draykerdk/drayker.org):

```bash
# in a checkout of draykerdk/drayker.org
node tools/make-com.js ../drayker.com-site/index.html
cd ../drayker.com-site
node tools/prerender.js --site=com
node tools/prerender-check.js --site=com
```

One component, two sites. The generator changes the `SITE` build constant, the cross-site link and the document head. It can also add a staging `noindex` when explicitly enabled. The prerender step then emits clean, crawlable route documents with unique metadata and full favicon paths. **Content for these pages is edited in `drayker.org/index.html`** and regenerated here.

`support.js` is the generated Design Component runtime and is also copied as-is. `.nojekyll` keeps GitHub Pages from interpreting `{{ … }}` component bindings as Liquid.

## Deployment

The canonical site is live at **[drayker.com](https://drayker.com)** through GitHub Pages and the repository `CNAME`. The generated document is indexable: `STAGING = false` in `drayker.org/tools/make-com.js`, and the deployed `index.html` has no staging `noindex` directive.

After changing institutional content in `drayker.org`:

1. run the generator into this repository.
2. run the render checks from `drayker.org` against the generated file.
3. run `tools/prerender.js --site=com` and `tools/prerender-check.js --site=com` in this repository.
4. confirm the diff contains only intended generated changes.
5. publish and verify the canonical domain and at least one clean subpage.

DNS and `www` redirects are deployment infrastructure. They should be changed only when a concrete domain route is required, not pre-created for every conceptual component.

## Running it locally

```bash
python3 -m http.server 8767
```

Site content is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The code is under the license in `LICENSE`.
