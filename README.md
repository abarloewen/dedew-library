# Dedew Library — deployable build

Static site. No build step, no dependencies.

    index.html      the whole application
    data/*.json     the corpus (fetched at runtime)
    vercel.json     noindex headers + JSON content types
    robots.txt      disallow all crawlers

## Deploy (Vercel, matching UC's usual pattern)

1. Create a **private** GitHub repo, e.g. `abarloewen/dedew-library`.
2. Push this folder's contents to `main`.
3. Vercel → Add New → Project → import that repo.
   Framework preset: **Other**. Build command: none. Output directory: `./`
4. Deploy. Every push to `main` redeploys.

## Access gate

`index.html` carries a client-side gate, access code `avb`, matching the other UC
client demos. **This is a soft gate, not security** — it keeps the page from being
read by anyone who stumbles on the URL, but the JSON under `/data/` is fetchable
directly by anyone who knows the paths.

For a real gate, use Vercel's own **Password Protection**
(Project → Settings → Deployment Protection). That sits in front of every request
including the JSON, and needs a Vercel Pro plan.

## Before this is made public

The 310 records flagged for legal or editorial review are **not in this build** —
their English is not served to the page at all, only titles and the reason.
That is deliberate. Do not swap in the unfiltered corpus without a decision from
the Sheikh's office. See `docs/TRANSLATION-STYLE-GUIDE.md` §12 and the
Held for Review section of the site.
