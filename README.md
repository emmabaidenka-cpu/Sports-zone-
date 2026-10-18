# SPORTZONE — Complete Starter Website

SPORTZONE is a full-stack sports news starter project with:
- Responsive public homepage for desktop and mobile
- Admin sign-in dashboard at `/admin`
- Create, edit, publish, draft and delete your own articles
- Categories for Ghana, football, basketball, boxing, athletics, tennis and other sports
- Server-side RSS headline aggregation from selected publishers
- JSON file storage for articles
- External headlines link to their original publishers

## Important before publishing
This is a deployable starter project, not a website already published on the internet. You need a Node.js host/server and must complete the secure configuration below. RSS feed addresses can change or be blocked by publishers, so check each feed and its terms before launch. The starter uses a JSON file for article storage; for a larger production site, migrate to a managed database and add backups, rate limiting, monitoring and a persistent session store.

## Run locally
1. Install Node.js 18 or newer.
2. Unzip this project and open a terminal in the project folder.
3. Install packages:
   ```bash
   npm install
   ```
4. Copy `.env.example` to `.env`.
5. Generate a password hash. Replace `YOUR_STRONG_PASSWORD` with a password you will keep private:
   ```bash
   node -e "require('bcryptjs').hash('YOUR_STRONG_PASSWORD', 12).then(console.log)"
   ```
6. Put the generated hash into `ADMIN_PASSWORD_HASH` in `.env`. Set a long random `SESSION_SECRET`, and set your own `ADMIN_USERNAME`.
7. Start the server:
   ```bash
   npm start
   ```
8. Open `http://localhost:3000` for the public site and `http://localhost:3000/admin` for the dashboard.

## News sources and copyright
The RSS integration shows headlines and short publisher-provided summaries, with links back to source articles. Do not copy complete articles or images from other publishers without permission. Confirm the publisher permits RSS display and comply with its terms, attribution requirements and applicable copyright law. You can edit the `FEEDS` list in `server.js` to use feeds you are authorized to display.

## Deployment checklist
- Use a hosting provider that supports Node.js and persistent storage, or migrate article data to a database.
- Set `NODE_ENV=production`, `SESSION_SECRET`, `ADMIN_USERNAME`, and `ADMIN_PASSWORD_HASH` in the host's environment settings.
- Serve over HTTPS.
- Do not upload `.env` or passwords to a public repository.
- Set up regular backups of `data/articles.json`.
- Add a persistent session store before using multiple server instances.
- Verify RSS sources, image rights, privacy/contact information, and editorial accuracy.
- Replace `news@sportzone.example` in `public/index.html` with a real newsroom email address.

## Files
- `server.js` — API, admin authentication and RSS feed aggregation
- `public/index.html` — public homepage
- `public/admin.html` — publishing dashboard
- `public/styles.css` — site styles
- `public/app.js` — homepage article and RSS rendering
- `public/admin.js` — admin dashboard behavior
- `data/articles.json` — starter article data
