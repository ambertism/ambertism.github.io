# emberCAP website

Static site for **emberCAP** (embercap.us): a homepage plus a portfolio subpage for each of the three members. Plain HTML/CSS, no build step.

```
index.html                     homepage
assets/style.css               shared styles
members/member-one/index.html  portfolio pages (rename folders to real names)
members/member-two/index.html
members/member-three/index.html
```

## Preview locally

```bash
python -m http.server 8123
```

Then open http://localhost:8123.

## Push to GitHub (ambertism/ambertism.github.io)

Run these from this folder. The first time, set up git and connect to the repo:

```bash
git init -b main
git add .
git commit -m "Initial emberCAP site"
git remote add origin https://github.com/ambertism/ambertism.github.io.git
```

**If the repo is empty**, push normally:

```bash
git push -u origin main
```

**If the repo already has files** you want to keep, pull them in first:

```bash
git pull origin main --allow-unrelated-histories
git push -u origin main
```

(If the pull reports conflicts, fix them or ask Claude to help, then commit and push.)

If git asks you to sign in, use your GitHub account; for a password prompt, use a personal access token from GitHub → Settings → Developer settings.

## Publish settings (one time)

1. On GitHub, open the repo → **Settings → Pages**.
2. Under **Build and deployment**, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**.
3. Under **Custom domain**, enter `embercap.us` and save. Tick **Enforce HTTPS** once it's available.
4. At your domain registrar, DNS should point at GitHub Pages: A records for the apex domain to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and a CNAME for `www` to `ambertism.github.io`. Skip this if the domain already works.

The site goes live a minute or two after each push.

## Updating later

```bash
git add .
git commit -m "Describe your change"
git push
```
