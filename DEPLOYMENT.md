# Deployment Plan: Seam Cricket Academy Website

## Repository Info

- **Repo**: `seamcricketacademy-png/html-seamcricketacademy`
- **URL**: https://github.com/seamcricketacademy-png/html-seamcricketacademy
- **Live Site**: https://www.seamcricketacademy.com
- **Hosting**: GitHub Pages (from `main` branch root)

---

## Current State on GitHub

```
main branch (LIVE on GitHub Pages):
├── CNAME                 # Domain: www.seamcricketacademy.com
├── README.md
├── assets/               # Images
└── index.html            # Current live HTML (47KB)
```

## Local State (Ready to Deploy)

```
D:\html-seamcricketacademy\
├── astro-revamp/              # NEW Astro project
│   └── dist/                  # Built files → Deploy this
│       ├── _astro/
│       ├── assets/
│       ├── favicon.svg
│       └── index.html
│
├── backup-legacy/             # ✅ FAILSAFE BACKUP
│   ├── index.html
│   └── assets/
│
├── index.html                 # To be replaced
├── CNAME                      # Keep (domain config)
└── DEPLOYMENT.md
```

---

## Option 1: GitHub Actions (Recommended) ✅

Create automated deployment via GitHub Actions:

### Step 1: Create Workflow File

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy Astro to GitHub Pages

on:
  push:
    branches: [main]
  release:
    types: [published]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install and Build
        working-directory: ./astro-revamp
        run: |
          npm ci
          npm run build

      - name: Copy CNAME
        run: cp CNAME astro-revamp/dist/

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./astro-revamp/dist
          cname: www.seamcricketacademy.com
```

### Step 2: Configure GitHub Pages

1. Go to **Settings** → **Pages**
2. Set **Source**: `gh-pages` branch (created by action)
3. Custom domain: `www.seamcricketacademy.com`

### Step 3: Create Release

```bash
git tag v2.0.0
git push origin v2.0.0
```

Then create a release on GitHub to trigger deployment.

---

## Option 2: Manual Deploy with Git (Simple)

### Step 1: Build Locally
```bash
cd astro-revamp
npm run build
```

### Step 2: Prepare Root for Deploy
```bash
cd ..
# Remove old files
rm index.html
rm -rf assets

# Copy new build
cp -r astro-revamp/dist/* .
cp CNAME .  # Ensure CNAME stays
```

### Step 3: Commit and Push
```bash
git add .
git commit -m "🚀 Deploy v2.0.0 - Astro Revamp Christmas Release"
git push origin main
```

GitHub Pages will auto-deploy from `main`.

---

## Option 3: GitHub Release with Build Artifacts

### Step 1: Build and Create Release Bundle
```bash
cd astro-revamp
npm run build
cd dist
zip -r ../../release-v2.0.0.zip .
```

### Step 2: Create GitHub Release
1. Go to **Releases** → **Create new release**
2. Tag: `v2.0.0`
3. Title: `🎄 Christmas Release - Astro Revamp`
4. Attach `release-v2.0.0.zip` as asset
5. Publish release

### Step 3: Deploy from Release
Download zip, extract to repo root, push.

---

## Rollback Plan

If issues occur, restore from backup:

```bash
rm -rf _astro assets index.html favicon.svg
cp backup-legacy/index.html .
cp -r backup-legacy/assets .
git add .
git commit -m "🔙 Rollback to v1.0.0 legacy HTML"
git push origin main
```

---

## Pre-Deploy Checklist

- [x] Backup created (`backup-legacy/`)
- [ ] `npm run build` successful
- [ ] Test locally: `npx serve dist`
- [ ] All images/videos load
- [ ] Contact form works
- [ ] WhatsApp button visible on contact section
- [ ] Mobile responsive
- [ ] CNAME in dist folder

---

## Recommended Approach

**Use Option 1 (GitHub Actions)** for:
- ✅ Automated builds on push/release
- ✅ Clean separation of source and built files
- ✅ Easy rollback via releases
- ✅ Professional CI/CD workflow

**Use Option 2 (Manual)** for:
- Quick one-time deployment
- Full control over what gets pushed

---

## Next Steps

1. Shall I create the GitHub Actions workflow file?
2. Or proceed with manual deployment now?
