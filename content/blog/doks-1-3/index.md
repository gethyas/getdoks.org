---
title: "Doks 1.3"
url: "/blog/doks-1-3/"
description: "Doks 1.3 — our first release of the new year — is here! This release includes restructured dependencies, deduplicated Bootstrap variables, and more."
summary: "Doks 1.3 — our first release of the new year — is here! This release includes restructured dependencies, deduplicated Bootstrap variables, and more."
date: 2024-01-17T09:03:26+01:00
lastmod: 2024-01-17T09:03:26+01:00
draft: false
weight: 50
categories: []
tags: []
contributors: ["Henk Verlinde"]
pinned: false
homepage: false
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Doks 1.3 — our first release of the new year — is here! This release includes restructured dependencies, deduplicated Bootstrap variables, and more.

Highlights include:

- [Restructured dependencies](#restructured-dependencies)
- [Deduplicated Bootstrap variables](#deduplicated-bootstrap-variables)

To take advantage of the latest features, make sure you’re running the latest version of Doks. You can upgrade to Doks 1.3 by following the [Upgrade to v1.3](/migration-guides/v-1/v-1-3/) migration guide.

## Restructured dependencies

Doks main dependencies are now specified in Doks' `package.json` — in stead of in `@hyas/doks-core`'s `package.json` — so you can easily update for example Hugo, Hyas Images, and Hyas SEO yourself.

```json
{
  "scripts": {
    "postinstall": "hugo-installer --version otherDependencies.hugo --extended --destination node_modules/.bin/hugo"
  },
  "dependencies": {
    "@hyas/doks-core": "^1.3.0",
    "@hyas/images": "^2.0.3",
    "@hyas/inline-svg": "^1.0.5",
    "@hyas/seo": "^2.1.0",
    "@tabler/icons": "^2.40.0",
    "exec-bin": "^1.0.0",
    "gethyas": "^2.2.2",
    "hugo-installer": "^4.0.1"
  },
  "devDependencies": {
    "shx": "^0.3.4"
  },
  "otherDependencies": {
    "hugo": "0.121.1"
  }
}
```

Hyas Images for example is updated like any `@hyas/*` integration (or theme):

{{< tabs "update-doks" >}}
{{< tab "npm" >}}

```bash
npm install @hyas/images@latest
```

{{< /tab >}}
{{< tab "pnpm" >}}

```bash
pnpm upgrade @hyas/images --latest
```

{{< /tab >}}
{{< tab "Yarn" >}}

```bash
yarn upgrade @hyas/images --latest
```

{{< /tab >}}
{{< /tabs >}}

## Deduplicated Bootstrap variables

Doks now only specifies customized Bootstrap SCSS variables in [`_variables-overrides.scss`](https://github.com/gethyas/doks-core/blob/main/assets/scss/common/_variables-overrides.scss) — instead of overriding _all_ Bootstrap SCSS variables — making customizations [easier and more robust](https://github.com/gethyas/doks-core/blob/main/assets/scss/app.scss).

Add your customizations in `assets/scss/common/`:

```scss {title="_variables-custom.scss"}
/* Put your custom SCSS variables here */
```

```scss {title="_custom.scss"}
/* Put your custom SCSS code here */
```

## Bug Fixes

Additional bug fixes are included in this release. Check out the [release notes](https://github.com/gethyas/doks-core/releases/tag/v1.3.0) to learn more.
