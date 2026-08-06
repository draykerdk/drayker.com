# drayker.com — Drayker institutional site

The institutional presentation of Drayker: what the organization is, what each part of the system does, and how the whole thing fits together.

Companion to **[drayker.org](https://drayker.org)**, the volunteers portal. Participation lives there — the open-functions board and the volunteer application are not duplicated here, they are handed over to the portal.

## `index.html` in this repository is generated

Do not edit it by hand. It is produced from the component in [`draykerdk/drayker.org`](https://github.com/draykerdk/drayker.org):

```bash
# in a checkout of draykerdk/drayker.org
node tools/make-com.js ../drayker.com-site/index.html
```

One component, two sites. The generator changes exactly four things — the `SITE` build constant, the cross-site link, the document head, and the staging `noindex` — so the two deployments can never drift apart. **Content for these pages is edited in `drayker.org/index.html`** (the `com*` fields of each project, and the `.com` branch of each page's copy) and regenerated here.

`support.js` is the generated Design Component runtime and is also copied as-is. `.nojekyll` keeps GitHub Pages from interpreting `{{ … }}` component bindings as Liquid.

## Staging

The site is published at `draykerdk.github.io/drayker.com` and carries `<meta name="robots" content="noindex, nofollow">` until the `drayker.com` domain is pointed at GitHub Pages.

Going live means, in order:

1. Point the DNS for `drayker.com` at GitHub Pages.
2. Add a `CNAME` file containing `drayker.com` to this repository.
3. Set `STAGING = false` in `tools/make-com.js` (in the `drayker.org` repository) and regenerate `index.html`.
4. Change `CROSS_SITE_URL` in `drayker.org/index.html` from the staging address to `https://drayker.com`.
5. Open `https://drayker.com` and confirm the `noindex` is gone from the served page.

## Running it locally

```bash
python3 -m http.server 8767
```

Site content is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); the code is under the license in `LICENSE`.
