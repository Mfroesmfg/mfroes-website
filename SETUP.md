# MFroes Website — Admin System Setup

This turns your site into one you can edit yourself: a login page at
**yoursite.com/admin** where you edit content and upload photos through
simple forms, hit **Publish**, and the live site updates automatically.

You'll do this **once**. Don't worry if a step looks technical — Delfino's
assistant will walk you through each one live. Total time: ~20–30 minutes.

---

## What's in this folder

```
mfroes-website/
├── index.html              ← the website
├── content/                ← your editable content (the admin edits these)
│   ├── used.json           ← Used & Refurbished machines
│   ├── videos.json         ← Videos
│   ├── plants.json         ← Plants & Projects
│   ├── story.json          ← Our Story photos
│   └── crops.json          ← Crops we clean
├── admin/                  ← the admin panel
│   ├── index.html
│   └── config.yml          ← ⚠️ change ONE line here (see Step 3)
├── netlify.toml
└── SETUP.md                ← this file
```

**You still need to add two folders you already have:** copy your existing
`images/` folder (all your photos) and `pdfs/` folder into this folder, so
they go up with everything else.

---

## Step 1 — Put it on GitHub

1. Go to **github.com** and sign in.
2. Click **New repository**. Name it **`mfroes-website`**. Leave it Public
   (or Private — both work). Click **Create repository**.
3. On the new repo page, click **uploading an existing file**.
4. Drag in **everything** from this folder — `index.html`, the `content`,
   `admin`, `images`, and `pdfs` folders, `netlify.toml`. Then **Commit**.

## Step 2 — Connect Netlify (auto-publishing)

1. In Netlify, click **Add new site → Import an existing project → GitHub**.
2. Authorize GitHub if asked, then pick your **mfroes-website** repo.
3. Leave the build settings blank (publish directory `.`). Click **Deploy**.

That's it — from now on, any change (yours in the admin, or a file change)
publishes automatically. No more dragging files.

## Step 3 — Point the admin at your repo

1. In your GitHub repo, open **`admin/config.yml`** and click the pencil (edit).
2. Find the line: `repo: YOUR-GITHUB-USERNAME/mfroes-website`
3. Replace `YOUR-GITHUB-USERNAME` with your real GitHub username
   (e.g. `repo: cornelius/mfroes-website`). Commit.

## Step 4 — Turn on the login (one-time)

The admin logs you in with your GitHub account. To allow that:

1. **Create a GitHub OAuth app:** GitHub → your profile → **Settings** →
   **Developer settings** → **OAuth Apps** → **New OAuth App**.
   - Application name: `MFroes Admin`
   - Homepage URL: your Netlify site URL (e.g. `https://yoursite.netlify.app`)
   - Authorization callback URL: `https://api.netlify.com/auth/done`
   - Click **Register**, then **Generate a new client secret**. Copy the
     **Client ID** and **Client secret**.
2. **Add it to Netlify:** your Netlify site → **Site configuration** →
   **Access & security** → **OAuth** → **Install provider** → **GitHub** →
   paste the Client ID and Client secret → Save.

## Step 5 — Log in and edit

Go to **yoursite.netlify.app/admin** → **Login with GitHub**. You'll see
sections for Used Machines, Videos, Plants, Our Story, and Crops. Edit, add
photos, hit **Publish**, and the site updates in about a minute.

## Step 6 — Go live on mfroesmfg.com

In Netlify → **Domain settings** → **Add a custom domain** → enter
`mfroesmfg.com`. Netlify shows the DNS records to set at your domain provider.
Point them there and the new site takes over your address. (Do this last,
once you're happy with everything.)

---

### Notes
- The site now reads its lists from the `content/` files, so it must be
  viewed on the web (Netlify), not by double-clicking `index.html` locally.
- Product catalog (models, specs, spec-sheet PDFs) is not in the admin yet —
  that's a planned Phase B. For now those are still edited in `index.html`.
