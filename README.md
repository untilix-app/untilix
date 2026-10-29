# Untilix Public Site

Static HTML files for the Untilix iOS app public site, hosted on GitHub Pages.

## What this is

This folder is a ready-to-publish bundle for the Untilix app's public-facing pages. The same three pages are referenced from App Store Connect:

- `index.html` - Landing page
- `privacy.html` - Privacy Policy (required by Apple App Store)
- `support.html` - Support FAQ + contact

The files are pure static HTML and CSS. No JavaScript, no build step, no dependencies.

## Files

| File | Purpose |
|---|---|
| `index.html` | Marketing landing page |
| `privacy.html` | Privacy Policy (Apple App Store required URL) |
| `support.html` | Support FAQ and contact |
| `README.md` | This document |

All pages are UTF-8 encoded. No external scripts, no fonts, no images. Theme (light/dark) follows the visitor's system preference via `prefers-color-scheme`.

## Publish with GitHub Pages

### Step 1 - Create a new public GitHub repository

Create a new public repository on GitHub named `untilix` (no template, no .gitignore, no README at creation time so the folder contents stay flat).

If you already have a GitHub Pages site at `untilix-app.github.io`, you can use a subfolder such as `daysuntil` and rename this folder accordingly. The URLs in step 4 assume the standalone repo approach.

### Step 2 - Add these files to the repository root

The three HTML files and this README should live at the root of the `untilix` repository, not in a subfolder.

```
untilix/
  index.html
  privacy.html
  support.html
  README.md
```

### Step 3 - Enable GitHub Pages

- Open `https://github.com/untilix-app/untilix/settings/pages`
- Source: **Deploy from a branch**
- Branch: `main`
- Folder: `/ (root)`
- Save

GitHub Pages will build and publish within a few minutes.

### Step 4 - Verify the published URLs

Open each URL in a browser (private/incognito recommended for first verification):

- `https://untilix-app.github.io/untilix/`
- `https://untilix-app.github.io/untilix/privacy.html`
- `https://untilix-app.github.io/untilix/support.html`

Each page must:

- Load over HTTPS (no certificate warnings)
- Show the Untilix branding
- Have the support email `untilixapp@gmail.com` visible and working as a `mailto:` link
- Render the same content as the local files (no mojibake, no broken characters)

## Expected URLs

After GitHub Pages is live, the three URLs are:

```
https://untilix-app.github.io/untilix/
https://untilix-app.github.io/untilix/privacy.html
https://untilix-app.github.io/untilix/support.html
```

These three are the values to enter into App Store Connect:

- **Privacy Policy URL** -> the `/privacy.html` URL
- **Support URL** -> the `/support.html` URL
- **Marketing URL (optional)** -> the root URL

Replace `untilix-app` with the actual GitHub username that owns the `untilix` repository.

## Pre-App Store URL checklist

Before using the URLs in App Store Connect, confirm each one:

- [ ] Returns HTTP 200 (not 404 or redirect loop)
- [ ] Loads over HTTPS (no mixed content warnings)
- [ ] Renders correctly on iPhone Safari
- [ ] No `OWNER_REQUIRED` placeholder text remains in any page
- [ ] Support email link opens the user's mail app
- [ ] No broken characters or mojibake in titles or body text
- [ ] Privacy text matches the app's actual behavior (no account, no cloud, no analytics, no tracking)
- [ ] No personal information leaks (real name, real email beyond the support address, real phone)

If any of these fail, fix before submitting the app to App Store Review.

## Do not store secrets here

This repository is public. Do not commit:

- Apple ID, App Store Connect API keys, App Store Connect issuer ID
- Apple Developer Team ID or App Store Connect Apple ID (these are public-ish but should not be in a public repo)
- EAS access tokens, Expo access tokens
- API keys, OAuth secrets, JWT signing keys
- Passwords, recovery codes, 2FA seeds
- `.p8`, `.p12`, `.cer`, `.mobileprovision` files
- Personal phone numbers or real personal email addresses

The only email that should appear is the public support email.

## Updating content

To change any text:

1. Edit the HTML file locally
2. Verify the change in a browser
3. Commit and push to `main`
4. GitHub Pages rebuilds within seconds

No secrets are involved at any step.