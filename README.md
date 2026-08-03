# Mathuradas Meghji &mdash; website

Static site for M/s Mathuradas Meghji, Main Bazar, Okha (retail &amp; wholesale groceries, authorised dealer for RAVI, GEETA and JP edible oils).

## Structure

```
index.html      Homepage (hero, about, products teaser, brands, why us, contact)
products.html   Full product catalogue, grouped by category
privacy.html    Privacy Policy
terms.html      Terms & Conditions
404.html        Custom "page not found" page
css/styles.css  Shared stylesheet for every page
assets/logo.png Shop logo (also used as the browser tab icon)
CNAME           Custom domain for GitHub Pages
```

Every page shares the same header, footer and `css/styles.css` — colours and fonts live in `:root` at the top of that file, so a palette or font change only needs to happen once.

## Editing content

- **Contact details, GSTIN, phone numbers:** appear in the footer `ledger` block and contact section of every page — search for the value across all `.html` files and replace it everywhere it appears.
- **Product list:** edit the `.item-list` blocks in `products.html`. Each item is one `<span class="item-chip" lang="gu">…</span>`. Update the `count` label next to a category heading if you add or remove items.
- **Logo:** replace `assets/logo.png` with a new image of the same approximate square size; every page picks it up automatically.

## Hosting on GitHub Pages with a custom domain

1. **Push these files to the repository** (`master-dg/mathuradas-meghji`), with `index.html` at the repo root — not inside a subfolder.
2. In the repo, go to **Settings &rarr; Pages**.
3. Under **Build and deployment &rarr; Source**, choose **Deploy from a branch**, then pick the branch (`main`) and folder (`/root`). Save.
4. Still on the Pages settings screen, under **Custom domain**, enter your domain and save. This is what writes the `CNAME` file check on GitHub's side — the `CNAME` file already included in this repo should match exactly.
5. At your domain's DNS provider (wherever the domain was purchased), add:
   - Four **A** records for the apex domain, pointing to:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - One **CNAME** record for `www` pointing to `master-dg.github.io`, so `www.` also works.
6. DNS changes can take anywhere from a few minutes up to ~24 hours to propagate. Once GitHub shows a green check next to the custom domain in Settings → Pages, tick **Enforce HTTPS**.

Full reference: [GitHub Docs — Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
