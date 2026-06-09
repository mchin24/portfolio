# Security Hardening Checklist

Static site — no backend, no forms, no user input. Attack surface is minimal. These are hardening improvements, not patches for active vulnerabilities.

---

## 1. HTTP Security Headers
**Where:** Coolify reverse proxy config (not the HTML)  
**Why:** Browsers respect these headers to prevent a class of attacks even when no vulnerability exists in your code. Set-it-and-forget-it.

- [ ] **`X-Content-Type-Options: nosniff`**  
  Stops the browser from guessing a file's content type. Prevents a browser from interpreting a `.jpg` as executable JavaScript if an attacker ever managed to upload something. Low relevance for a static read-only site, but costs nothing.

- [ ] **`X-Frame-Options: DENY`**  
  Prevents your site from being loaded inside an `<iframe>` on another domain. Blocks "clickjacking" — where an attacker overlays your page invisibly and tricks a user into clicking something. Not a real threat here since there's nothing to click that causes harm, but it's standard practice.

- [ ] **`Referrer-Policy: strict-origin-when-cross-origin`**  
  Controls how much URL information is sent in the `Referer` header when a visitor clicks a link off your site. With this value, the full path stays private — only the origin (`https://midnightdev.studio`) is shared, not the specific page they were on.

- [ ] **`Permissions-Policy: camera=(), microphone=(), geolocation=()`**  
  Explicitly opts the page out of browser APIs you don't use. Prevents a rogue script (e.g., from a compromised CDN) from requesting camera or location access. The empty `()` means "nobody is allowed."

- [ ] **`Strict-Transport-Security: max-age=63072000; includeSubDomains`**  
  Tells browsers to always use HTTPS for your domain for the next 2 years, even if a link or redirect tries to use HTTP. Prevents SSL stripping attacks. Only add this once you're confident HTTPS is stable on your domain — it's hard to undo quickly.

---

## 2. Self-Host Google Fonts
**Where:** `index.html` (lines 15–17) + add font files to `assets/fonts/`  
**Why:** Currently every visitor's IP is logged by Google when the font loads. Also, if Google Fonts CDN were ever compromised, malicious CSS could load on your page.

- [ ] Download Inter font files (woff2) from [fonts.google.com](https://fonts.google.com/specimen/Inter)  
  Weights needed: 300, 400, 500, 600, 700, 800
- [ ] Place files in `assets/fonts/`
- [ ] Add `@font-face` rules to `css/styles.css`
- [ ] Remove the two `<link rel="preconnect">` tags and the Google Fonts `<link>` from `index.html`

---

## 3. Add `noreferrer` to External Links
**Where:** `index.html` lines 248, 271, 277  
**Why:** `noopener` (already present) prevents the target page from accessing `window.opener`. `noreferrer` additionally suppresses the `Referer` request header, so LinkedIn and GitHub don't receive a signal that the visitor came from your site.

- [ ] Change all three external links from `rel="noopener"` to `rel="noopener noreferrer"`

```html
<!-- Before -->
<a href="https://linkedin.com/in/mychalchin" target="_blank" rel="noopener">

<!-- After -->
<a href="https://linkedin.com/in/mychalchin" target="_blank" rel="noopener noreferrer">
```

---

## 4. Content Security Policy (CSP)
**Where:** Either as an HTTP header (preferred, same place as #1) or as a `<meta>` tag in `index.html`  
**Why:** A CSP is an allowlist that tells the browser exactly which sources are permitted to load scripts, styles, fonts, and images. If anything outside that list tries to load — a compromised CDN, an injected script tag — the browser blocks it and can report it.

- [ ] Draft a policy. Starting point for this site (after self-hosting fonts):
  ```
  default-src 'none';
  script-src 'self';
  style-src 'self';
  font-src 'self';
  img-src 'self' data:;
  connect-src 'none';
  frame-ancestors 'none';
  base-uri 'self';
  form-action 'none';
  ```
- [ ] Test in report-only mode first (`Content-Security-Policy-Report-Only`) to catch any violations before enforcing
- [ ] Promote to `Content-Security-Policy` once clean

> Note: If you keep Google Fonts instead of self-hosting (#2), add `https://fonts.googleapis.com` to `style-src` and `https://fonts.gstatic.com` to `font-src`.
