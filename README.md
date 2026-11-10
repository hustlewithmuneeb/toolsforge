# ToolForge v3 — Free All-in-One Online Tools Website

An original, deploy-ready static website with **all 112 tools from the fotools.com
catalogue, plus 8 ToolForge extras = 120 working tools**. Premium branded design:
SVG logo, **monochrome black / grey / white identity**, dark animated-gradient
hero, clean white cards with black accents. A light/dark toggle is included;
both themes are strictly monochrome.

## Navigation (v3)

- **Header “All Tools ▾” mega-dropdown** — a wide, scrollable panel grouping
  all 120 tools under their 12 category headings; click any tool to open it.
- **Header “Categories ▾” dropdown** — lists all 12 categories with tool
  counts; choosing one filters the home grid to that category.
- **Category pills** — each pill in the filter row has its own ▾ caret button
  opening a dropdown of that category's tools (the pill itself still filters).
- **Mobile** — the ☰ hamburger opens an accordion: tap a category to expand
  its tools, tap a tool to open it. Dropdowns close on outside click or
  Escape, and are keyboard accessible (aria-expanded / aria-haspopup).

**Everything runs in the visitor's browser** — no backend, no database, no sign-up.
Most tools need no network at all; a few lookup tools (DNS, IP, currency, SSL,
code runners, PlantUML) call the free public API named inside each tool.

- **Brand:** ToolForge (placeholder — rename-ready, see below)
- **Founder:** Muneeb Ullah · hustlewithmuneeb@gmail.com
- **Files:** just `index.html` (self-contained; libraries load from public CDNs)

## Deploy (free, ~2 minutes)

- **Vercel:** vercel.com → Add New Project → drag the folder (or this ZIP's
  contents) in → Deploy. No build settings needed.
- **Netlify:** app.netlify.com → Sites → drag the folder onto the page.
- **GitHub Pages:** create a repo, upload `index.html`, Settings → Pages →
  deploy from the main branch.

Any static host works. Use HTTPS — WebCrypto tools (hash, HMAC, RSA) and
camera/mic/screen recording require a secure context (HTTPS or localhost).

## Rename the brand

1. In `index.html`, edit the `BRAND` object at the top of the first script block
   (name, tagline, email, founder).
2. Find-and-replace `ToolForge` in the visible text (header wordmark, hero,
   footer, About page) and swap the two inline SVG logo marks (header + footer,
   marked with the comment `BRAND LOGO`) and the SVG favicon `data:` URI in
   `<head>` if you also change the name/mark.
3. Colours live in one place: the CSS variables at the top of the `<style>`
   block (`--accent`, `--accent2`, `--accent3`, `--grad`) and the per-category
   colours in the `CATS` array.

## Tool list (120)

- **JSON Tools (10):** YAML↔JSON, Sort Keys, JSON↔CSV, Escape/Unescape, Compare,
  JSON Schema, XML↔JSON, Parser/Formatter, TOML↔JSON, TOON↔JSON (simple
  line-based format, labelled in the tool)
- **Encoding & Encryption (15):** Base64, Base32, Base58, MD5, SHA-256, SHA-512,
  Bcrypt, HMAC, RSA (WebCrypto), JWT, AES (CryptoJS), URL, Unicode, Morse, ASCII
- **Network (10):** URL Parser, Browser Info, IPv4 Subnet, IPv6 Subnet, HTTP
  Status Lookup, WebSocket Tester, DNS (Cloudflare DoH), SSL Lookup (crt.sh),
  My IP (ipify/ipapi), IP Converter
- **Frontend (13):** JS / HTML / CSS formatters, Color Converter, Palettes,
  Color Picker, SVG Path Editor, Keyboard Detector, Bar / Pie / Line / Scatter
  charts, Doodle Board
- **Backend (10):** Random Number, UUID, Chmod, Cron Builder, JavaScript Runner
  (in-page), Python Runner (Pyodide), Go / Java / PHP / Rust Runners (Piston)
- **Conversion (7):** Timestamp, Number Base, Date Calculator, Area, Weight,
  Length, Temperature
- **Multimedia (10):** Video / Screen / Audio Recorders, MP3 Volume, Audio
  Cutter, Audio Compressor, Video Cutter, Video Compressor, Video to MP4,
  Video to GIF — media tools re-encode in real time via canvas + MediaRecorder;
  each tool labels its exact method and output format honestly
- **Image (10):** to AVIF / WebP / PNG / JPG, Cropper, Compressor, GIF Animator,
  Watermark, Batch Resize, Favicon Generator
- **Document (10):** Markdown, Mermaid, Mind Map, Word→PDF (print view),
  Excel→PDF (print view), Images to PDF, PDF to Image, PDF to Word (text),
  PDF Merge, PlantUML
- **Text (10):** Word Count, Sum Numbers, Sort Lines, Case Change,
  Full↔Half Width, Deduplicate, Text Diff, Variable Naming, Occurrence Counter,
  Column Selector
- **Other (7):** QR Generator, Barcode Generator, Regex Tester, Emoji
  Collection, Stopwatch & Timer, Currency Rates, Password Generator
- **Calculators & Extras (8, kept from v1):** Age Calculator, BMI, Percentage,
  Lorem Ipsum, Slug Generator, Image to Base64, Image Rotate & Flip, Image Filters

## Known honest limitations (also labelled inside each tool)

- **Piston (Go/Java/PHP/Rust):** the free public Piston API became
  whitelist-only in February 2026. The runners still call it and display its
  own refusal message if not whitelisted; for production, self-host Piston and
  change the one `fetch` URL in the `pistonTool` function.
- **Currency:** uses open.er-api.com (free, CORS-enabled) with frankfurter.dev
  (ECB) fallback, because the old api.frankfurter.app endpoint stopped working.
- **AVIF / MP4 output:** depends on the visitor's browser encoder support; the
  tools detect a mismatch and say so instead of delivering a wrong file.
- **WebSocket Tester:** the default public echo server may be unavailable;
  any WebSocket URL can be entered.
- **crt.sh (SSL lookup):** the public service is sometimes busy and returns a
  non-JSON page; the tool shows a friendly retry message.

## Next steps (when you want them)

- Add login (Auth.js / Firebase) and a Pro tier (Stripe / Lemon Squeezy) —
  the UI already has no account dependency, so gating can be added per tool.
- Move heavy tools behind a small Node backend only if traffic demands it.
- One SEO page per tool: the SPA can be pre-rendered per tool route later.

## Logo setup (v3.1)
The ToolForge logo (black rounded square, white wrench) is set up as real files in the site root:
`logo.svg` / `logo-white.svg` (vector, used for favicon + sharing), `logo-512.png` / `logo-192.png` (app icons),
`logo-white-512.png`, `favicon.ico` + `favicon-16/32/48.png`, `apple-touch-icon.png` (180px),
`logo-horizontal-black.png` / `logo-horizontal-white.png` (mark + wordmark lockups for press/social),
`og-image.png` (1200x630 social share image, wired via Open Graph + Twitter meta tags in index.html),
`site.webmanifest` (PWA icons/theme). The header and footer use the same mark inline so the page still
shows the logo even if opened as a single file; keep the logo files in the same folder when deploying.
