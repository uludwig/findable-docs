# Findable Docs Site

This is the Mintlify-powered documentation site for Findable, sourced from the platform's main `README.md` in the repo root.

## Local Preview

Install the Mintlify CLI once and then run it from this directory:

```sh
npm i -g mintlify
cd docs-site
mintlify dev
```

The dev server starts on `http://localhost:3000` and live-reloads on file changes.

If your port is taken, run `mintlify dev --port 3333`.

## File Layout

```
docs-site/
├── docs.json                 # Site configuration: theme, colors, nav
├── README.md                 # This file
├── getting-started/
│   ├── quickstart.mdx
│   ├── setup-wizard.mdx
│   └── prerequisites.mdx
├── architecture/
│   ├── overview.mdx
│   ├── cosmos-containers.mdx
│   └── hidden-settings.mdx
├── ai-providers/
│   ├── providers-overview.mdx
│   ├── model-versions.mdx
│   └── role-based-access.mdx
├── data-sources/
│   ├── datasource-catalog.mdx
│   ├── chat-with-your-data.mdx
│   ├── data-connections.mdx
│   ├── vector-store.mdx
│   ├── sharepoint.mdx
│   └── onedrive.mdx
├── flow-designer/
│   ├── flow-designer.mdx
│   └── flow-retriever.mdx
├── forms-prompts/
│   └── prompt-library.mdx
├── tools-mcp/
│   ├── tool-providers.mdx
│   ├── tool-setup.mdx
│   ├── web-search-rag.mdx
│   └── memory-system.mdx
├── access-identity/
│   ├── role-based-access.mdx
│   ├── entity-scopes.mdx
│   ├── chat-logging-audit.mdx
│   └── azure-app-registration.mdx
├── operations/
│   ├── production-deployment.mdx
│   ├── ci-cd.mdx
│   ├── capacity-limits.mdx
│   ├── notifications.mdx
│   └── troubleshooting.mdx
└── meta/
    ├── related-resources.mdx
    └── license.mdx
```

The navigation in `docs.json` mirrors the nine Webflow docs categories: Getting Started, Architecture, AI Providers & Models, Data Sources, Flow Designer, Forms & Prompts, Tools & MCP, Access & Identity, Operations & Deployment, plus a Reference group for the meta pages.

## Brand Settings

`docs.json` is preconfigured with:

- **Theme:** `mint`
- **Name:** `Findable`
- **Primary color:** `#EA580C` (terracotta)
- **Light variant:** `#F97316`
- **Dark variant:** `#C2410C`
- **Logo:** `/logo.svg` (both light and dark)
- **Favicon:** `/favicon.svg`

Drop `logo.svg` and `favicon.svg` into this directory before deploying. The brand colors match the Webflow marketing site.

## Deploying to Mintlify

### 1. Create a Mintlify account

Sign up at <https://mintlify.com>. The free Hobby plan supports a connected GitHub repo, automatic builds on push, and a custom subdomain.

### 2. Connect this repo

In the Mintlify dashboard, click **Add docs** → connect GitHub → select this repository. When prompted, point Mintlify at the `docs-site/` subfolder (it will look for `docs.json` there).

Push to the configured branch (default: `main`) and Mintlify will build and publish automatically.

### 3. Configure the `docs.findable.net` subdomain

In Mintlify project settings → **Custom Domain**, enter `docs.findable.net`. Mintlify will display a `CNAME` target (typically `cname.mintlify.com`).

At your DNS provider, add:

```
Type:  CNAME
Host:  docs
Value: <value shown in Mintlify dashboard>
TTL:   3600
```

DNS propagation usually takes 5–30 minutes. Once Mintlify shows the green check next to the domain, the site is live at <https://docs.findable.net>.

### 4. Updating content

Edit any `.mdx` file in this folder, commit, and push. Mintlify rebuilds on every push to the connected branch (typically `main`). No manual deploy step is required.

To preview before pushing, run `mintlify dev` locally.

## Source

All content is derived from `README.md` in the repository root. When the source README changes substantially, regenerate the affected `.mdx` files rather than editing them in place — this keeps the docs site and product README aligned.
