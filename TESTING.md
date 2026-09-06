# Testing Guide

Use this checklist whenever the site is changed or deployed.

## 1. Check the local files

From the repository root, start a local server:

```bash
python3 -m http.server 8000
```

Open these URLs in a browser:

```text
http://127.0.0.1:8000/
http://127.0.0.1:8000/blogs.html
http://127.0.0.1:8000/about.html
```

Confirm that:

- The page title and content are correct.
- The navigation opens Home, Blogs, and About.
- The featured post and blog cards display correctly.
- The About email link opens an email client.
- The layout works on desktop and mobile widths.
- No images, fonts, or styles are missing.

Stop the server with `Ctrl+C` when finished.

## 2. Check the repository

Run these commands before pushing:

```bash
git diff --check
git status
```

The working tree should contain only intentional changes. Confirm that no passwords, API keys, or private files are included.

## 3. Push and check GitHub Pages

```bash
git add .
git commit -m "Describe the change"
git push origin main
```

In GitHub, open **Settings → Pages** and confirm:

- Source is **Deploy from a branch**.
- Branch is `main`.
- Folder is `/ (root)`.
- Custom domain is `thegunjan.in`.
- **DNS check successful** is shown.
- **Enforce HTTPS** is enabled.

## 4. Check the live site

Run:

```bash
curl -I https://thegunjan.in
curl -I https://www.thegunjan.in
curl -I https://PawanKrGunjan.github.io/gunjan/
```

Expected results:

- `https://thegunjan.in` returns `200`.
- `https://www.thegunjan.in` redirects to `https://thegunjan.in/`.
- The GitHub Pages URL redirects to the custom domain.

Check every page in a browser:

```text
https://thegunjan.in/
https://thegunjan.in/blogs.html
https://thegunjan.in/about.html
```

## 5. Check DNS if the site is not live

```bash
nslookup thegunjan.in 1.1.1.1
nslookup www.thegunjan.in 1.1.1.1
```

The root domain should return these four GitHub Pages addresses:

```text
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

`www.thegunjan.in` should be a CNAME pointing to:

```text
PawanKrGunjan.github.io
```

If DNS is correct but GitHub returns 404, check the Pages source and wait for the Pages deployment to finish. DNS changes can take up to 48 hours, although this site usually updates within a few minutes.