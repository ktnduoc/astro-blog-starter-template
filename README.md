# Astro Blog with EmDash CMS

[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/cloudflare/templates/tree/main/astro-blog-starter-template)

<!-- dash-content-start -->

A blog built with Astro and [EmDash CMS](https://github.com/emdash-cms/emdash), deployed on Cloudflare Workers with D1 (database) and R2 (media storage).

Features:

- ✅ EmDash CMS admin panel at `/_emdash/admin`
- ✅ Database-driven content with Cloudflare D1
- ✅ Media storage with Cloudflare R2
- ✅ Minimal styling (make it your own!)
- ✅ SEO-friendly with canonical URLs and OpenGraph data
- ✅ RSS Feed support
- ✅ Server-side rendering via Cloudflare Workers
- ✅ Built-in Observability logging

<!-- dash-content-end -->

## Getting Started

1. Install dependencies:

```bash
npm install
```

2. Create a D1 database and an R2 bucket in your Cloudflare account, then update the IDs in `wrangler.json`:

```bash
wrangler d1 create astro-blog-starter-template
wrangler r2 bucket create astro-blog-starter-media
```

3. Initialize the EmDash database (runs migrations):

```bash
npm run bootstrap
```

4. Start the local dev server:

```bash
npm run dev
```

5. Open `/_emdash/admin` in your browser to create your first post.

## 🚀 Project Structure

```text
/
├── public/             Static assets (fonts, favicon, etc.)
├── src/
│   ├── components/     Astro UI components (Header, Footer, etc.)
│   ├── layouts/        Page layout templates
│   ├── pages/
│   │   ├── blog/       Blog listing and post pages
│   │   └── rss.xml.js  RSS feed endpoint
│   ├── content.config.ts  (legacy, replaced by EmDash)
│   ├── live.config.ts  EmDash live collection config
│   ├── worker.ts       Cloudflare Worker entrypoint
│   └── consts.ts       Site-wide constants
├── astro.config.mjs    Astro + EmDash configuration
└── wrangler.json       Cloudflare Workers configuration
```

Content is stored in Cloudflare D1 (SQLite) and managed through the EmDash admin UI at `/_emdash/admin`. Use `getEmDashCollection("posts")` and `getEmDashEntry("posts", slug)` from the `"emdash"` package to query content in your pages.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                           | Action                                              |
| :-------------------------------- | :-------------------------------------------------- |
| `npm install`                     | Installs dependencies                               |
| `npm run bootstrap`               | Initialize EmDash database (run once after install) |
| `npm run dev`                     | Starts local dev server at `localhost:4321`         |
| `npm run build`                   | Build your production site to `./dist/`             |
| `npm run preview`                 | Preview your build locally, before deploying        |
| `npm run astro ...`               | Run CLI commands like `astro add`, `astro check`    |
| `npm run deploy`                  | Deploy your production site to Cloudflare           |
| `npm wrangler tail`               | View real-time logs for all Workers                 |

## 👀 Want to learn more?

- [EmDash CMS documentation](https://github.com/emdash-cms/emdash)
- [Astro documentation](https://docs.astro.build)
- [Cloudflare D1 documentation](https://developers.cloudflare.com/d1/)
- [Cloudflare R2 documentation](https://developers.cloudflare.com/r2/)
