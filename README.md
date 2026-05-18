# Licensing

Static site that hosts the **privacy policies** for our products, served
via **GitHub Pages** (Jekyll).

## Design rule: products are isolated

Each product lives in **its own top-level folder** and is rendered as a
**standalone page**. There is intentionally **no shared landing page**
and **no cross-links** between products — visitors should only ever
arrive at a policy via the direct URL printed in that product's store
listing / app / website.

The root URL (`/`) returns a generic 404 so the repo cannot be used to
enumerate which products we ship.

## Structure

```
.
├── _config.yml                    # Minimal Jekyll config — no site title
├── 404.md                         # Generic "not found" page for /
├── your-extension/
│   └── index.md                   # Privacy policy for Your Extension
└── <next-product>/
    └── index.md                   # Privacy policy for the next product
```

## Live URLs

After enabling GitHub Pages, each product is reachable directly at:

```
https://<user>.github.io/Licensing/your-extension/
https://<user>.github.io/Licensing/<next-product>/
```

The root `https://<user>.github.io/Licensing/` will show the 404 page.

If you want even stronger separation (different domain per product,
no shared infrastructure visible), use a **custom subdomain per
product**, e.g. `your-extension-privacy.example.com`, by adding a
`CNAME` file — but a single repo with separate folders is usually
enough for "they don't look connected."

## Enable GitHub Pages

1. Push the repo to GitHub.
2. **Settings → Pages → Source: Deploy from a branch → `main` / root**.
3. Wait ~1 minute. The product URLs above will be live.

## Adding a new product

1. Create a new top-level folder: `<product-slug>/`.
2. Inside it, add `index.md` with front matter:
   ```yaml
   ---
   title: <Product Name> — Privacy Policy
   permalink: /<product-slug>/
   ---
   ```
3. Write that product's policy. **Do not** reference any other product,
   shared brand, or shared contact email — keep each product's identity
   self-contained.
4. Use a product-specific contact email (e.g.
   `<product-slug>-privacy@example.com`) rather than a shared one.

## Things to keep separate per product

To avoid making them look related:

- **Contact email** — one per product, not a shared inbox.
- **Company / publisher name** — only mention it if it's already public
  on that product's store page.
- **Last updated date** — track per product.
- **Permissions table / data collected** — must match that product's
  actual `manifest.json` / behavior.

## Local preview (optional)

```bash
gem install bundler jekyll
bundle init
echo 'gem "github-pages", group: :jekyll_plugins' >> Gemfile
bundle install
bundle exec jekyll serve
# open http://localhost:4000/Licensing/your-extension/
```
