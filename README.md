# thyagulabs website

Marketing site for thyagulabs. It is a single static page: plain HTML, CSS and JavaScript, with no build step and no dependencies to install.

```
index.html              The whole site (content, styles and scripts)
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

- **Connect the contact form.** The form runs in demo mode: it checks the fields and shows the success message but sends nothing. To receive enquiries, create a free form at [Formspree](https://formspree.io) (or Web3Forms, Basin, etc.), then in `index.html` set:

  ```js
  const LEAD_FORM_ENDPOINT = "https://formspree.io/f/your-form-id";
  ```

  Each submission arrives by email with the region, services, phone, email, name and notes.
- **Add your contact email.** If the form fails to send, the page currently says "please email us directly". Add your real address to that message (search for `email us directly`) and, ideally, to the footer.
- **Link previews.** For WhatsApp, LinkedIn and Slack previews to show the logo, change `og:image` in `index.html` to the full URL, e.g. `https://thyagulabs.com/assets/logo-full.png`.
- **Check the claims.** Several lines came from the original design mock-up and are promises clients may hold you to: "Lowest price in the market", "SLA <15 min response", the response guarantee after submitting the form, and the compliance points on each office card. Keep only what you can stand behind.
- **Legal links.** The footer's Master Services Agreement, Enterprise Security and Privacy Policy links show a "available on request" message. Replace them with real pages when you have them. A privacy policy is required in most countries if you collect contact details.

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
