# chrismoffett.com

One-page personal site, plain HTML and CSS, published with GitHub Pages. Edit `index.html`; changes on `main` go live automatically.

## Design (settled 2026-11-22)

- EB Garamond throughout. Text at display scale (`main` font-size clamp 22–35px, line-height 1.42, 31em column). No navigation, no images, no dates.
- Run-in name "Chris Moffett" in roman at 1.7em. Keep "Moffett" in one text run with no letter-spacing so the ff ligature survives.
- Colours: background #f7f5ee, text #2a2723, accent #9d2933, footer grey #55514b. Dark mode has its own palette.
- Links: full red underline, .05em, thickening to .08em on hover, offset .22em.
- Footer: short red rule (two text lines above, .44em below), then CV / LinkedIn / X / Facebook / Instagram / Email in EB Garamond small caps (Scholar and Academia stay in the JSON-LD sameAs only), underlined only on hover. Font is set by `--footer-font`.
- Email: the mailto in the text is HTML-entity encoded. Never write the address in plain text. Commits use a noreply address.

## Going live on chrismoffett.com (not done yet)

The `CNAME` file in this repo already holds `chrismoffett.com`. GitHub says to add the custom domain in Pages before changing DNS, so do step 5's custom-domain part right after step 1.

1. Settings → Pages → Deploy from a branch → `main`, `/ (root)`. Preview: https://chrismoffett.github.io/chrismoffett.com/
2. Export the full zone from EuroVPS first, as a backup.
3. In the EuroVPS DNS zone for chrismoffett.com, change only these:
   - apex A records → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 (replacing 77.235.54.106)
   - `www` CNAME → chrismoffett.github.io
   - `mail` and `ftp`: today CNAMEs to the apex; change each to an A record for 77.235.54.106 so they stay on the old server
4. Leave every mail record alone: the Google Workspace MX, SPF (Google + MailerLite), MailerLite and Google verification TXT, and DMARC. Also add the pending TXT `mailerlite-domain-verification=ea01e323ee3683ff05f44059c2c9e5eb7d591581`.
5. Add `chrismoffett.com` as the custom domain in Pages (matches the `CNAME` file), and turn on Enforce HTTPS once the certificate is issued.
6. aestheticrelationalexercises.com stays on EuroVPS, on the same nameservers. Do not cancel the EuroVPS account.

## Search (2026-11-23)

- `index.html` head: title, meta description, canonical `https://chrismoffett.com/`, Open Graph and Twitter card tags (text only, no image), and a JSON-LD `ProfilePage` whose `Person.sameAs` lists every public profile. Take profile URLs from the Notion page "Public profiles". Bump `dateModified` and the sitemap `lastmod` when the page text changes.
- `sitemap.xml` lists the one page; `robots.txt` points to it.
- `404.html` forwards any unknown URL (old WordPress links such as /student-work) to the homepage at once. GitHub still sends a 404 status, so Google drops the old URLs instead of indexing duplicates.
- Google Search Console: the zone already holds a `google-site-verification` TXT record (from the Google Workspace setup), so adding a Domain property for chrismoffett.com from the same Google account may verify at once; otherwise add the TXT record Search Console gives. Then submit `https://chrismoffett.com/sitemap.xml`.
