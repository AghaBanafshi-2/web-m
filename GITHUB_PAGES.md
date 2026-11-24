# GitHub Pages deployment

This repository can be built as a static site and deployed with the workflow at
`.github/workflows/deploy-pages.yml`.

## One-time setup

1. In the repository, open **Settings → Secrets and variables → Actions → New repository secret**.
2. Add `TELEGRAM_API_ID` and `TELEGRAM_API_HASH` using the values for your Telegram application.
3. Open **Settings → Pages** and set **Build and deployment → Source** to **GitHub Actions**.
4. Merge the `github-pages-deploy` branch into `master`. The workflow will then build and deploy on pushes to `master`.
5. You can also start a deployment manually from **Actions → Deploy Telegram Web A to GitHub Pages → Run workflow**.

The expected site address is:

`https://aghabanafshi-2.github.io/web-m/`

## Telegram API credentials

The workflow reads the two values from GitHub Actions repository secrets. Do not commit them to the repository or put them in frontend source files. Note that values embedded in a browser application are ultimately visible to visitors, so Telegram API ID/hash are application identifiers, not a way to keep a client-side app secret.

## SOCKS5 limitation

GitHub Pages only serves static files. Browsers do not expose a native SOCKS5 transport to web applications, so this site cannot connect through an arbitrary SOCKS5 proxy just by adding a proxy address. Public free proxies are also untrusted and may be unreliable. The web client should use its supported Telegram connection transport; adding a proxy requires a compatible, trusted transport or a separately hosted service, not GitHub Pages alone.
