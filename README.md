# FakeGrass Cape Town — Website Deployment Guide
## www.fakegrasscapetown.co.za

---

## 📁 File Structure

```
fakegrasscapetown/
├── index.html                    ← Homepage (main landing page)
├── services.html                 ← All services overview
├── about.html                    ← About the company
├── contact.html                  ← Contact + quote form
├── robots.txt                    ← SEO: search engine instructions
├── sitemap.xml                   ← SEO: full site map
├── .htaccess                     ← HTTPS redirects, caching, security
├── README.md                     ← This file
│
├── areas/
│   └── southern-suburbs.html     ← Local SEO: Southern Suburbs page
│   (+ add more area pages below)
│
└── services/
    ├── residential.html
    ├── commercial.html
    ├── sports-turf.html
    ├── pet-friendly.html
    ├── schools.html
    └── balcony-rooftop.html
```

---

## 🚀 DEPLOYMENT STEPS

### 1. Domain & Hosting Setup
- Register **www.fakegrasscapetown.co.za** via a South African registrar (e.g., Afrihost, HOSTAFRICA, Domains.co.za)
- Set up hosting — recommended: **cPanel shared hosting** (Afrihost/HOSTAFRICA) or **Cloudflare Pages** (free, fast CDN)
- Point DNS A record to your hosting server IP
- Add CNAME www → @ (or your host's requirement)

### 2. SSL Certificate (HTTPS)
- Use **Let's Encrypt** (free) via your cPanel or Cloudflare
- The `.htaccess` already enforces HTTPS redirects once SSL is active
- Verify: https://www.fakegrasscapetown.co.za should load without warning

### 3. Upload Files
Upload ALL files via:
- **cPanel File Manager** (drag & drop)
- **FTP client** (FileZilla) to `public_html/` directory
- **Git deployment** if using Cloudflare Pages / Netlify

### 4. Update Phone Numbers & Contact Info
Find and replace these placeholders throughout all HTML files:
- `021 000 0000` → your actual Cape Town landline
- `082 000 0000` → your actual mobile/WhatsApp number
- `info@fakegrasscapetown.co.za` → your actual email
- WhatsApp links: `https://wa.me/27820000000` → replace `27820000000` with your actual number (country code + number, no spaces)

### 5. Connect the Contact Form
The form currently has a JavaScript simulation. Connect to a real backend using ONE of:
- **Formspree.io** (free tier): Add `action="https://formspree.io/f/YOUR_ID"` to `<form>` tag
- **Netlify Forms**: Add `netlify` attribute to `<form>` tag (if hosting on Netlify)
- **EmailJS**: Replace the JS handler with EmailJS SDK
- **Custom PHP**: Create a `submit-form.php` backend handler

Example (Formspree):
```html
<form id="quoteForm" action="https://formspree.io/f/xyzabcde" method="POST">
```

### 6. Google Analytics (GA4)
Add before `</head>` in index.html and all pages:
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### 7. Google Search Console
1. Go to https://search.google.com/search-console
2. Add property: `https://www.fakegrasscapetown.co.za`
3. Verify ownership (HTML file method recommended)
4. Submit sitemap: `https://www.fakegrasscapetown.co.za/sitemap.xml`

### 8. Google Business Profile
1. Go to https://business.google.com
2. Create/claim listing for "FakeGrass Cape Town"
3. Add your website URL, phone, hours, photos
4. Add the Business Profile embed/badge to your contact page

---

## 🔍 SEO CHECKLIST

### ✅ Already Implemented
- [x] Unique title tags on every page
- [x] Unique meta descriptions
- [x] H1 hierarchy (one H1 per page)
- [x] robots.txt with sitemap reference
- [x] XML sitemap with all pages
- [x] Canonical URLs on every page
- [x] Schema.org LocalBusiness structured data
- [x] Internal linking (no orphan pages)
- [x] Breadcrumb navigation
- [x] Cape Town local SEO keywords throughout content
- [x] Area landing pages (Southern Suburbs done; add more)
- [x] Mobile-responsive design
- [x] .htaccess HTTPS enforcement
- [x] Performance headers (caching, compression)
- [x] Open Graph meta tags
- [x] geo.region and geo.placename meta tags

### ⏳ To-Do After Launch
- [ ] Add Google Analytics 4 tracking code
- [ ] Submit to Google Search Console
- [ ] Create Google Business Profile
- [ ] Connect real contact form backend
- [ ] Add actual product/installation photos (replace emoji placeholders)
- [ ] Build remaining area pages (Northern Suburbs, Atlantic Seaboard, etc.)
- [ ] Add blog/FAQ section for long-tail keywords
- [ ] Get Google reviews from Stefan's clients
- [ ] Register on local directories (HelloPeter, Snupit, Yellow Pages SA)
- [ ] Create social media pages (Facebook, Instagram) linked from site

---

## 📄 ADDITIONAL AREA PAGES TO BUILD

Copy `areas/southern-suburbs.html` and adapt for:
- `/areas/northern-suburbs.html` — Durbanville, Bellville, Parow, Goodwood, Tygervalley
- `/areas/atlantic-seaboard.html` — Sea Point, Green Point, Camps Bay, Bantry Bay
- `/areas/constantia.html` — Constantia Valley, Tokai, Bergvliet
- `/areas/stellenbosch.html` — Stellenbosch, Franschhoek, Paarl
- `/areas/hout-bay.html` — Hout Bay, Llandudno
- `/areas/durbanville.html` — Durbanville, Kraaifontein, Brackenfell
- `/areas/somerset-west.html` — Somerset West, Strand, Gordon's Bay

---

## 📱 PAGESPEED OPTIMISATION TIPS

To hit 60+ on Google PageSpeed Insights:

1. **Images**: Convert all photos to WebP format, compress with Squoosh.app
2. **Add loading="lazy"** to all below-fold images: `<img loading="lazy" src="...">`
3. **Fonts**: The site uses `display=swap` — already optimised
4. **Hosting**: Use a CDN (Cloudflare free plan strongly recommended)
5. **CSS/JS**: All styles are inline/in `<style>` blocks — no render-blocking external files
6. **Preload**: Add `<link rel="preload">` for hero images once real images are added

---

## 🎨 BRANDING

**Colour Palette:**
- Deep Green: `#1a3a2a` (primary brand)
- Mid Green: `#2d6a4f`
- Bright Green: `#40916c` (CTAs, highlights)
- Light Green: `#74c69d`
- Pale Green: `#d8f3dc` (backgrounds)
- Gold: `#c9a84c` (accent, premium CTA)

**Fonts:**
- Headings: Playfair Display (900, 700)
- Body: DM Sans (300, 400, 500, 600)

---

## 📞 CONTACT FOR UPDATES

Built for: www.fakegrasscapetown.co.za
Source: Migrated and redesigned from www.artgrasspro.com
