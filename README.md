# MPRE Prep — offline-capable self-study PWA

An original, challenging 60-question MPRE-style practice app organized into all 12 modules from the supplied study outline. It has a dark-purple mobile-first design, randomized question and answer order, in-app reference notes from the original outline, module practice, 10/25/60-question exams, optional timed mode, immediate answer explanations, missed-question retry, score history, and browser-local progress storage.

## Publish for iPhone / Android home screen

**Important:** Do not open `index.html` directly from a ZIP or `file://` URL for offline PWA installation. Service workers require a secure HTTPS origin (or localhost for testing).

**GitHub Pages (free):**
1. Extract the ZIP and create a public GitHub repository (for example `mpre-prep`).
2. Upload the **contents** of the `mpre_prep` folder to the repository root. Commit all files.
3. In repository **Settings → Pages**, select **Deploy from a branch**, `main`, `/ (root)` and save.
4. Once published, open `https://YOUR_USERNAME.github.io/mpre-prep/` from the phone.
5. **iPhone:** Safari → Share → **Add to Home Screen** → Add. **Android:** Chrome menu → **Install app** / **Add to Home screen**.
6. Open the app online once to cache the content; afterward it works offline. Progress stays on that device/browser, not synchronized to others.

Alternative: deploy the folder using Cloudflare Pages, Netlify, or any static HTTPS host.

## Local testing

From inside the extracted folder, run `python3 -m http.server 8000`, then visit `http://localhost:8000` on that computer. On a phone, use the HTTPS published version for install/offline.

## Design / caveats

- No login, payments, API keys, analytics, or network calls are needed for the quiz.
- All question text is bundled locally in `questions.js`.
- Currently 5 distinct questions per each of 12 modules (60 total). An exam of 60 uses the full bank; repeated sessions reuse scenarios in different order.
- Timed mode gives 90 seconds per selected question. Time expiration ends the session and scores *answered questions only*; unanswered questions are not counted in that percentage (see total answered).
- Results are stored in localStorage. Clear browser data = history erased. Export progress as JSON in My Progress.
- This is an independent study aid based on the provided outline, NOT an NCBE practice exam or BARBRI question bank. The outline is user-provided and may simplify or omit rules. Confirm nuanced issues against the current ABA Model Rules and NCBE exam materials before exam use; local state variations exist.
- The question bank is easy to extend: duplicate an object in `questions.js`, use a unique `id`, assign module 1–12 and adjust the quiz counter in UI if desired.
