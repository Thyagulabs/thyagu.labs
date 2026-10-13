# thyagulabs website

Marketing site for thyagulabs. It is a single static page: plain HTML, CSS and JavaScript, with no build step and no dependencies to install.

```
index.html              The main site (content, styles and scripts)
privacy.html            Privacy Policy
terms.html              Terms & Conditions
assets/legal.css        Styles shared by the two legal pages
assets/logo-mark.png    Logo mark used in the header, hero badge and footer
assets/logo-full.png    Full logo, used for link previews
assets/favicon.png      Browser tab icon
assets/apple-touch-icon.png
.nojekyll               Tells GitHub Pages to serve files as-is
```

## Preview locally

Open `index.html` in a browser. To test it as a real site:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Host on GitHub Pages

1. Create a new repository on GitHub, for example `thyagulabs-website`.
2. Upload these files, keeping the `assets` folder:

   ```bash
   git init
   git add .
   git commit -m "thyagulabs website"
   git branch -M main
   git remote add origin https://github.com/<your-username>/thyagulabs-website.git
   git push -u origin main
   ```

   Or use **Add file → Upload files** on the GitHub website and drag in everything.
3. In the repository, go to **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/thyagulabs-website/`.

### Use your own domain (e.g. thyagulabs.com)

1. In **Settings → Pages → Custom domain**, enter your domain and save. GitHub adds a `CNAME` file to the repository.
2. At your domain registrar, add the DNS records GitHub shows you:
   - For `www`: a `CNAME` record pointing to `<your-username>.github.io`
   - For the root domain: `A` records pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153` and `185.199.111.153`
3. Once DNS has updated, tick **Enforce HTTPS**.

## Before going live

- **Activate the contact form (one time).** Discovery-call requests are emailed to **support@thyagulabs.com** through [FormSubmit](https://formsubmit.co), a free form-to-email service that needs no account. After the site is live, submit the form once yourself. FormSubmit then sends an activation email to support@thyagulabs.com; click **Activate Form** in it. Every request after that arrives in that inbox as a table with name, email, phone, region, services and notes, and pressing Reply answers the person directly. Until it is activated, visitors see a message asking them to email support@thyagulabs.com instead. To change the address, edit `LEAD_EMAIL` in `index.html`. The form only sends from a real web address (GitHub Pages or `python3 -m http.server`), not from a file opened directly on your computer.
- **Check the legal pages.** `privacy.html` and `terms.html` name the company as "thyagulabs" at the Bengaluru office address, with Indian law and Bengaluru courts. If your registered legal name is different (for example "thyagulabs Private Limited"), search both files for "thyagulabs, #28/4" and update it. These pages are a solid starting point, not legal advice, so have a lawyer review them before you rely on them.
- **Link previews.** For WhatsApp, LinkedIn and Slack previews to show the logo, change `og:image` in `index.html` to the full URL, e.g. `https://thyagulabs.com/assets/logo-full.png`.
- **Compliance badges.** The HIPAA and GDPR badges in the hero and footer are your own statement of compliance (there is no official HIPAA certificate, and the GDPR has no official badge). Make sure you can show the safeguards behind them if a client asks, for example signed Business Associate Agreements for US healthcare projects and a GDPR data processing agreement for EU clients.
- **Check the claims.** Several lines came from the original design mock-up and are promises clients may hold you to: "Lowest price in the market", "Guaranteed callback within your local working hours", and the compliance points on each office card. Keep only what you can stand behind.

## Editing content

All text is in `index.html`:

| What | Where to look in `index.html` |
|---|---|
| Headline, intro, popular chips, hero cards | `<!-- HERO -->` |
| Office cards (Germany, US, Canada, India, Singapore, Dubai) | `const HUBS = [` in the script |
| Services | `const SERVICES = [` |
| Team members and roles | `const ROLES = [` (add or remove names in each `people` list) |
| Form options | `const REGIONS = [` and the services list |
| Footer | `<footer>` |

Colours are defined once at the top of the `<style>` block (`:root { ... }`).
