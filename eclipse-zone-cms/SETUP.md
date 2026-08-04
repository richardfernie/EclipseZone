# Eclipse Zone — Setup Checklist

This turns your blog into a real site with an "Add Post" / "Delete Post"
panel at yoursite.com/admin, usable from your phone or desktop.

## What's in this folder
- `src/posts/*.md` — your two existing posts, now as editable content files
- `src/index.njk`, `src/_includes/` — templates that auto-build the homepage from your posts
- `admin/` — the Content Manager (Decap CMS) panel
- `netlify.toml`, `package.json`, `.eleventy.js` — build configuration

You won't normally touch any of these once it's running — you'll just use
the /admin panel.

## Step 1 — Create a GitHub repository
1. Go to github.com, sign in (or create a free account)
2. Click **New repository** → name it e.g. `eclipse-zone` → Create
3. Upload this entire folder's contents to that repository
   (easiest way: on the repo page, use "Add file → Upload files" and
   drag everything in, keeping the folder structure)

## Step 2 — Connect Netlify to that repository
1. Go to netlify.com, sign in (you can sign in with your GitHub account)
2. **Add new site → Import an existing project → GitHub**
3. Pick the `eclipse-zone` repo
4. Build settings should auto-fill from `netlify.toml` — confirm:
   - Build command: `npx @11ty/eleventy`
   - Publish directory: `_site`
5. Click **Deploy** — your site will build and get a URL like
   `random-name-123.netlify.app` (you can rename this or add a real
   domain later in Site settings)

## Step 3 — Turn on Identity + Git Gateway (this is what powers login)
1. In your Netlify site dashboard: **Site configuration → Identity → Enable Identity**
2. Under Identity settings, set **Registration → Invite only**
   (so nobody else can sign up)
3. Scroll to **Services → Git Gateway → Enable Git Gateway**
   (this lets the CMS commit changes to GitHub on your behalf)
4. Go to the **Identity** tab → **Invite users** → enter your own email
5. Check your email, click the invite link — it'll ask you to set a password

## Step 4 — Log in and use it
1. Go to `yoursite.netlify.app/admin`
2. Log in with the account you just set up
3. You'll see **Posts** with a **New Post** button and, inside each post,
   a **Delete entry** option
4. Every add/edit/delete you make there:
   - Commits directly to your GitHub repo
   - Triggers Netlify to rebuild the site automatically
   - Goes live within about a minute, on any device

## Notes
- New posts you write in the CMS body field use the same markdown/HTML
  as the existing posts (bold, headers, and blocks like
  `<div class="pullquote">...</div>` or `<div class="takeaway">...</div>`
  all work if you paste them into the body).
- The homepage automatically shows your newest post as "Latest Post" and
  the rest in the grid below — you never need to edit the homepage by hand.
- If you ever want a custom domain instead of the `.netlify.app` one,
  that's under **Site configuration → Domain management** in Netlify.
