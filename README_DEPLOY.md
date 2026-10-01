# TradeX AI — Public preview website (Render, free address)

This is a **standalone static public preview**. It is deliberately different from your local subscription prototype:

- The chart is generated using **fictional sample instruments and synthetic prices**, not NSE/BSE or Yahoo Finance data.
- "Sample Pro" enables only this browser's interactive preview. No subscription, login, stored customer accounts, backend order execution, payment collection, or real orders.
- The virtual wallet and trade activity are stored in the visitor's browser (`localStorage`) only. Clearing browser data resets them. **Do not use this build to accept customer payments or credentials.**
- Pro pricing of ₹999 per month is marked *proposed*.
- Your original Flask app and local `data` directory stay on your own computer, separate from this public preview.

## Upload to GitHub

1. Extract the ZIP. Open the `TradeX_AI_Public_Preview` folder.
2. Create a **new** GitHub repository, e.g. `tradex-ai-preview`. Don't put private credentials, your old `data` folder, `.venv`, or `.env` in any public repository.
3. In GitHub, choose **Add file → Upload files**, then upload **`index.html`, `render.yaml`, `README_DEPLOY.md` and the `assets` folder** from this directory. Verify GitHub shows `index.html` in the repository root and `assets/style.css` and `assets/app.js` nested inside `assets/`.
4. Commit changes to the default branch.

## Deploy on Render

1. Visit https://dashboard.render.com and log in.
2. Select **New → Static Site** (not Web Service).
3. Connect your GitHub repository `tradex-ai-preview`.
4. Set **Branch** to your repository's default branch (usually `main`). Leave **Build command** empty. **Publish directory**: `.` (a dot, meaning the repository root).
5. Create the static site. Render provides an HTTPS address in the form `https://<your-unique-name>.onrender.com`. The exact name depends on availability.
6. Test the site on a phone and laptop; test fictional instruments, chart timeframes and sample trading.

`render.yaml` is included for optional Blueprint-based deployment and documents the same configuration, but the manual Static Site process above is simplest.

## Later — turning this into a real hosted subscriber app

The older Flask prototype isn't ready for public paid hosting. It uses SQLite on local disk, which free Render hosting won't preserve reliably. Before opening registrations/payment, migrate accounts and per-user ledgers to persistent hosted storage; use a verified billing provider/webhooks; add security hardening and privacy/terms; and get appropriate legal review plus rights to any displayed Indian stock-market data. Do not set `TRADEX_LOCAL_DEMO_UPGRADE=1` on a public server.
