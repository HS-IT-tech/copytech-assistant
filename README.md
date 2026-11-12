# Copytech Field Service Assistant (PWA)

A dark-mode, installable web app on top of the Gemini API. Photo diagnosis, quick-action presets, and local session history (searchable by machine model / error code).

## 1. Get a free API key
1. Open https://aistudio.google.com/apikey and sign in.
2. Create a key. **Do not enable billing** on its project if you want to stay on the free tier.
3. Free tier note: Google may use free-tier prompts (including photos) to improve its products. Avoid photographing customer documents or screens showing personal data.

## 2. Host it (free, HTTPS is required for camera + install)
**GitHub Pages**
1. Create a GitHub account and a new **public** repository (e.g. `fsa`).
2. Upload everything in this folder to the repository root (Add file -> Upload files).
3. Settings -> Pages -> Source: "Deploy from a branch" -> `main` / `/ (root)` -> Save.
4. After about a minute your app is at `https://<your-username>.github.io/fsa/`.

The repo is public, but it contains no secrets: your API key is typed into the app and stays on your phone only.

(Alternative: drag the folder onto https://app.netlify.com/drop for an instant HTTPS URL.)

## 3. Install on the Samsung phone
1. Open the URL in **Chrome** (or Samsung Internet).
2. Menu (three dots) -> **Add to Home screen** / **Install app**.
3. Launch from the home-screen icon. It opens full-screen with the splash screen.
4. On first launch, Settings opens: paste your key, tap **Test connection**.

## 4. Customize branding
- In-app: Settings -> company name, app title, logo upload.
- In the files: replace `logo.svg`, `icon-192.png`, `icon-512.png`; edit `name` and `short_name` in `manifest.webmanifest` (the home-screen label is read from there). After changing icons, uninstall and re-add the app to the home screen.

## 5. Model
Default is `gemini-3.8-flash`, changeable in Settings. As of Nov 2026, Google's pricing page lists a free tier for it, with rate limits. If you see a 429 error, you hit the free-tier limit; wait a minute. Free-tier limits can change; check https://ai.google.dev/gemini-api/docs/rate-limits.

## Notes
- Sessions and photos are stored in the phone's browser storage (IndexedDB). Clearing site data deletes them.
- Answers are AI-generated and can be wrong; each answer carries a reminder to verify against the service manual.
- To update the app after editing files, re-upload them; bump `CACHE` in `sw.js` (e.g. `fsa-shell-v2`) so phones fetch the new version.
