# SecuVidyra Academy website

A buildless, responsive website for secuvidyra.com. Upload this repository to GitHub and connect a static hosting provider. Public files live in `dist/`. No Node install or build is required.

## Included
- Responsive homepage with navigation, course filtering, course-detail dialogs and FAQs.
- Four standalone course syllabi with downloadable text versions.
- Instructor profile, illustrative work sample and honest planning-stage course information.
- Enquiry preparation with no hidden submission or personal-data storage.
- Privacy/learning terms, sitemap, robots file, favicon and 404 page.
- No third-party scripts, fonts, analytics or package dependencies.

## Before public launch
1. Edit `dist/assets/config.js` with a VERIFIED admissions email. The form then opens the visitor's mail client with a draft; it does not automatically send mail. Without an email, it downloads an enquiry text file and clearly states nothing was sent.
2. Optionally configure your verified WhatsApp number using international digits only.
3. Confirm and enter the actual legal operator. Review the privacy and learning terms accordingly.
4. Confirm course dates, mode, fees and equipment requirements. Publish payment/refund terms before accepting payment.
5. Test email drafting on a device with a configured email client. A server-backed form would need a separately configured service and privacy review.
6. Review all copy and test syllabi, mobile navigation and links on the actual hosted domain.

## GitHub upload
Create a repository such as `secuvidyra-website`. Upload the CONTENTS of this folder, keeping `dist/` intact. Do not upload the outer ZIP itself or any student records. Keep `dist/index.html` at that path. A private repository is appropriate when supported by your chosen host.

## Recommended deployment: GitHub + Cloudflare Pages
GitHub stores source code. Cloudflare Pages serves the website.
1. In Cloudflare Workers & Pages, create a Pages project using the GitHub repository.
2. Select the main branch. Framework preset: None. Build command: `exit 0`. Build output directory: `dist`.
3. Deploy and test the host-generated pages.dev URL. Do not invent this URL; use the one returned by Cloudflare.
4. In the Pages project's Custom domains, add `secuvidyra.com` before configuring its DNS.
5. For the apex domain, add the domain as a Cloudflare zone and use the exact nameservers Cloudflare assigns. Preserve all existing MX and TXT email records when moving DNS. Review DNSSEC migration with your registrar if enabled.
6. Add `www.secuvidyra.com` through the same Custom domains workflow. Use the host-generated CNAME target when requested. Do not copy another project's target.
7. Confirm both domains activate and HTTPS works. Select the preferred canonical domain and configure a redirect for the other using the hosting/DNS provider.
8. Confirm GitHub pushes update the deployment.

Exact DNS values depend on the project and provider; this package does not change DNS or register hosting. Do not replace email-related records when adding the website.

## GitHub Pages distinction
GitHub Pages is a separate hosting product from GitHub repositories. GitHub's published limits prohibit using Pages as free hosting for an online business or a site primarily facilitating commercial transactions. This academy is intended to support a training business, so the guide recommends an external static host connected to GitHub rather than assuming GitHub Pages eligibility.

## Other hosting
Any static web server can serve the CONTENTS of `dist/`. On your own server, configure the web root to this directory, obtain a TLS certificate and use that server's actual address for DNS. `_headers` is a Cloudflare-style header configuration; other servers need equivalent native settings.

## Local review
Open `dist/index.html` in a modern browser, or use `python -m http.server 8000 --directory dist`. The site also works under a repository subpath because local links are relative. The canonical URL and sitemap target the intended final domain.

## Editing map
- `dist/index.html`: homepage content and course summary cards.
- `dist/assets/style.css`: colours, typography and responsive layout.
- `dist/assets/app.js`: course dialog content and interactions.
- `dist/assets/config.js`: public contact/operator configuration; NEVER add secrets.
- `dist/syllabi/`: HTML and text syllabi. Keep these aligned with course changes.
- `dist/privacy.html`, `dist/terms.html`: public disclosures.

This first version has no student login, LMS, payments, live chat, backend inbox or admissions database. No fake testimonials or accreditation claims are included. It has not been published or connected to your DNS.

## Official deployment references (checked 13 November 2026)
- https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- https://developers.cloudflare.com/pages/configuration/custom-domains/
- https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits
