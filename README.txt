# QuickPrint Shop Demo

This demo has two pages connected to the same Firebase project:

- `index.html` — customer page: upload a document and enter print requirements.
- `dashboard.html` — shop-owner page: see incoming jobs live, open uploaded files, mark jobs as printed, and delete jobs.

## Run the demo

1. Keep both HTML files in the same folder.
2. Upload the folder to a static host (Firebase Hosting, Netlify, or GitHub Pages), or use a local static server.
3. Open `index.html` on the customer's phone.
4. Open `dashboard.html` on the shop owner's laptop.
5. Submit a test print job. It should appear on the dashboard when both pages are connected to the internet.

Both pages are already configured for the Firebase project used in your original code and use the same `print_jobs` Firestore collection and Storage bucket.

## Firebase setup required

In Firebase Console for the configured project:

1. Enable **Cloud Firestore**.
2. Enable **Storage**.
3. For a quick demo, configure Firestore and Storage rules to allow the required reads/writes. Do not leave public write/delete rules enabled for a real shop or production deployment.
4. Make sure the Firebase project's Storage bucket is active and billing/region requirements are satisfied.

## Demo limitations

- This is a front-end demo; it does not include staff login or customer authentication.
- The dashboard's Print action opens the uploaded file in a new browser tab. The shop owner can print it from the browser's PDF/image viewer.
- Automatic deletion after 60 minutes is not enabled. That needs a scheduled server-side task (for example, Cloud Functions/Cloud Scheduler).
- The "printed today" metric relies on `printedAt`; older jobs without that field may not be included.

## Important

The Firebase web config is visible in browser code by design. Security must come from Firebase Security Rules, not from hiding the API key. Use restricted rules and add authentication before using this with real customer documents.
