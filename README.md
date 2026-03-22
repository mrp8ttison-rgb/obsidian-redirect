# obsidian-redirect

HTTPS-to-Obsidian URI redirect page for iOS. Solves the problem where iOS blocks HTTP 308 redirects to custom URI schemes (`obsidian://`).

## Why

Telegram blocks custom URI schemes, so you can't send `obsidian://` links directly. Services like obsid.net work around this with HTTP redirects, but iOS Safari silently blocks server-side redirects to custom schemes (since iOS 13).

This page uses client-side JavaScript instead — which iOS allows.

## Usage

```
https://mrp8ttison-rgb.github.io/obsidian-redirect/?vault=Brains%20Remote&file=_agent%2Fresearch%2F2026-03-22%20-%20Example%20Note
```

**Parameters:**
- `vault` (required) — URL-encoded vault name
- `file` (required) — URL-encoded path relative to vault root, without `.md` extension

## How it works

1. User taps the link in Telegram
2. Page loads and attempts `window.location.href = 'obsidian://open?...'`
3. If auto-redirect fails, a "Open in Obsidian" button is shown as fallback

## Hosting

Hosted on GitHub Pages. No build step, no dependencies — just `index.html`.
