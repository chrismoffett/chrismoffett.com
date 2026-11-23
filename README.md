# chrismoffett.com

One-page personal site, plain HTML and CSS, published with GitHub Pages. Edit `index.html`; changes on `main` go live automatically.

## Design (settled 2026-11-22)

- EB Garamond throughout. Text at display scale (`main` font-size clamp 22–35px, line-height 1.42, 31em column). No navigation, no images, no dates.
- Run-in name "Chris Moffett" in roman at 1.7em. Keep "Moffett" in one text run with no letter-spacing so the ff ligature survives.
- Colours: background #f7f5ee, text #2a2723, accent #9d2933, footer grey #55514b. Dark mode has its own palette.
- Links: full red underline, .05em, thickening to .08em on hover, offset .22em.
- Footer: short red rule (two text lines above, .44em below), then CV / Google Scholar / Instagram in EB Garamond small caps, underlined only on hover. Font is set by `--footer-font`.
- Email: the mailto in the text is HTML-entity encoded. Never write the address in plain text. Commits use a noreply address.

## Going live on chrismoffett.com (not done yet)

1. Settings → Pages → Deploy from a branch → `main`, `/ (root)`. Preview: https://chrismoffett.github.io/chrismoffett.com/
2. Export the full zone from EuroVPS first, as a backup.
3. In the EuroVPS DNS zone for chrismoffett.com, change only these:
   - apex A records → 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153 (replacing 77.235.54.106)
   - `www` CNAME → chrismoffett.github.io
4. Leave every mail record alone: the Google Workspace MX, SPF (Google + MailerLite), MailerLite and Google verification TXT, and DMARC. Also add the pending TXT `mailerlite-domain-verification=ea01e323ee3683ff05f44059c2c9e5eb7d591581`.
5. Then add `chrismoffett.com` as the custom domain in Pages (this creates a CNAME file), and turn on Enforce HTTPS once the certificate is issued.
6. aestheticrelationalexercises.com stays on EuroVPS, on the same nameservers. Do not cancel the EuroVPS account.
