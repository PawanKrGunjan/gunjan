# Gunjan

A small personal writing site for [thegunjan.in](https://thegunjan.in), built as a static page for GitHub Pages.

For the repeatable local, deployment, live-site, and DNS checks, see [TESTING.md](TESTING.md).

## Pages

- `index.html` — Home with the featured post
- `blogs.html` — Blog index with all posts
- `about.html` — About Gunjan and contact details

## Publish with GitHub Pages

1. Push this repository to GitHub.
2. Open the repository's **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then select `main` and `/ (root)`.
4. Save and wait for GitHub Pages to publish the site.

## Connect `thegunjan.in`

In **Settings → Pages**, enter `thegunjan.in` as the custom domain and save. The repository already includes the required `CNAME` file.

At GoDaddy, remove any conflicting forwarding or parking records, then add these DNS records:

| Type | Name | Value |
| --- | --- | --- |
| `A` | `@` | `185.199.108.153` |
| `A` | `@` | `185.199.109.153` |
| `A` | `@` | `185.199.110.153` |
| `A` | `@` | `185.199.111.153` |
| `CNAME` | `www` | `PawanKrGunjan.github.io` |

DNS changes can take up to 48 hours. Once active, enable **Enforce HTTPS** in GitHub Pages settings.
