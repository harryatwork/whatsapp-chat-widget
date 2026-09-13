<div align="center">

# 💬 WhatsApp Chat Widget

**A floating WhatsApp button for any website — pre-filled message, pulse animation, zero dependencies. Drop one script tag and go live.**

[![HTML5](https://img.shields.io/badge/HTML5-pure-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Zero deps](https://img.shields.io/badge/dependencies-zero-brightgreen?style=flat-square)](.)
[![License](https://img.shields.io/badge/license-MIT-a855f7?style=flat-square)](LICENSE)

</div>

---

## The Problem

Every client asks for a WhatsApp button. The third-party widgets either collect analytics you didn't agree to, require an account, or need a bundler. This is 50 lines of plain HTML + CSS + JavaScript — no npm, no build step, no tracking. It works on any website, including static HTML, PHP, WordPress, or a Webflow custom code block.

---

## ✨ Features

- 🟢 **Floating button** — fixed position bottom-right, styled in WhatsApp green
- 💬 **Pre-filled message** — configure a greeting text that auto-fills when the chat opens
- 🔔 **Pulse animation** — soft glowing ring animation to draw attention without being annoying
- 📱 **Mobile-responsive** — opens `wa.me` deep link (native app on mobile, web on desktop)
- 🛎️ **Notification badge** — optional unread-message count bubble
- 🌙 **Dark mode aware** — adapts tooltip background to system theme
- ♿ **Accessible** — `aria-label` on the button, keyboard-focusable
- ⚡ **Single-file drop-in** — one `<script>` tag, everything inlined

---

## 🔧 How It Works

The button generates a `wa.me` URL with your phone number and the pre-filled message encoded as a query parameter. On mobile devices this opens the WhatsApp app directly. On desktop it opens `web.whatsapp.com`. No backend, no API key, no webhook.

```
wa.me URL structure:
https://wa.me/447911123456?text=Hi%2C%20I%27d%20like%20to%20know%20more%20about%20your%20services
```

---

## 🚀 Quick Start

### Option A — Script tag (recommended)

Add this to your HTML before `</body>`:

```html
<script
  src="https://cdn.jsdelivr.net/gh/harryatwork/whatsapp-chat-widget@main/widget.js"
  data-phone="447911123456"
  data-message="Hi, I'd like to know more about your services"
  data-position="bottom-right"
  data-show-after="2000"
></script>
```

Replace `447911123456` with your full number including country code (no `+`, no spaces).

### Option B — Self-host

```bash
git clone https://github.com/harryatwork/whatsapp-chat-widget
```

Copy `widget.js` and `widget.css` to your project, then:

```html
<link rel="stylesheet" href="widget.css">
<script src="widget.js"
  data-phone="447911123456"
  data-message="Hello! How can we help?"
></script>
```

### Option C — Inline HTML

For a WordPress custom HTML block or Webflow embed:

```html
<!-- Paste into any HTML block -->
<a href="https://wa.me/447911123456?text=Hi%2C%20I%27d%20like%20to%20know%20more"
   target="_blank"
   class="wa-float"
   aria-label="Chat on WhatsApp">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6b/WhatsApp.svg/120px-WhatsApp.svg.png"
       width="32" height="32" alt="WhatsApp" />
</a>
<style>
.wa-float { position:fixed; bottom:24px; right:24px; z-index:9999;
  background:#25D366; border-radius:50%; width:56px; height:56px;
  display:flex; align-items:center; justify-content:center;
  box-shadow:0 4px 12px rgba(37,211,102,.4); }
</style>
```

---

## ⚙️ Configuration

| Attribute | Default | Description |
|---|---|---|
| `data-phone` | — | **Required.** Phone number with country code, no `+` or spaces |
| `data-message` | `Hello!` | Pre-filled message text (URL-encoded automatically) |
| `data-position` | `bottom-right` | `bottom-right` or `bottom-left` |
| `data-show-after` | `0` | Delay in ms before the button appears |
| `data-badge` | — | Number to show on the notification badge |
| `data-tooltip` | — | Tooltip label on hover (e.g. `"Chat with us"`) |
| `data-size` | `56` | Button diameter in px |

---

## 📁 Project Structure

```
whatsapp-chat-widget/
├── widget.js          # Self-contained widget with inlined styles
├── widget.css         # Styles as a separate sheet (optional)
├── demo/
│   └── index.html     # Live demo page
└── README.md
```

---

<details>
<summary><strong>Common issues and fixes</strong></summary>

| Issue | Fix |
|---|---|
| Button doesn't appear | Check `data-phone` is set and the script tag has loaded |
| Wrong number format | Use full international format: `447911123456` not `07911123456` or `+44 7911 123456` |
| Opens browser instead of app | Expected on desktop — the widget opens the WhatsApp web app; mobile opens the native app |
| Button hidden by other widgets | Increase `z-index` in the CSS (default is 9999) |
| Pre-filled message not showing | Some older WhatsApp versions ignore the `text` param — no fix; use the latest app |

</details>

---

<div align="center">

Built by [Harish K](https://github.com/harryatwork)

</div>