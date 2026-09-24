# qbo-oauth-callback

Static OAuth 2.0 redirect (callback) page for Tatus Consultancy's QuickBooks Online
integration, served via GitHub Pages at **https://qbo-oauth.tatus.co.za/**.

## What it is
When you approve access in QuickBooks during the Authorization Code Grant, Intuit
redirects your browser here with `?code=…&realmId=…&state=…`. This page just reads
those values out of the URL and displays them for you to copy back into the
reporting tool (`python3 qbo_auth.py <client>` or `python3 onboard.py`).

## Why it's public and safe
- It is **static HTML/JS only** — no server, no backend, no database.
- It **never sees the `client_secret`** and never performs the token exchange;
  that happens locally in the private reporting tool.
- The authorization code it displays is single-use, short-lived and worthless
  without the client secret, so there are no secrets to protect here.
- URL values are HTML-escaped before display.
