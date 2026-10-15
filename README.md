# Debt Tracker

A calm, single-page web app for tracking paying off one total debt. No frameworks, no backend, no build step. Everything is saved in your browser. Works on phones and desktops.

## How it works

1. Enter what you owe. The app opens the **Calculator** so you can add your interest rate and monthly payment (or skip to the tracker).
2. Log payments on the **Tracker** as you make them.
3. When interest, fees or a statement changes what you owe, set your current balance. You can do this from the Tracker or by editing the balance in the Calculator; both update the same balance.

## Features

**Tracker**
- **The big number:** what you still owe, front and center, with a progress bar and your projected debt-free date
- **Log a payment:** type an amount and the total counts down
- **Set your current balance:** enter the new balance and the difference is logged in your history
- **History:** every payment and adjustment with its date; remove one logged by mistake (it asks first)
- **Sound:** a casino-style jingle when the app starts, a soft chime on each payment (both can be turned off in the footer)
- **Zero celebration:** confetti and a bigger sound when you hit $0.00

**Schedule:** a month-by-month payoff table showing start balance, payment, interest, principal and end balance, with totals and your debt-free date. On phones each month is shown as a card.

**Chart:** your balance over time (actual history plus the projected path) and how each payment splits between principal and interest. Hover, or tap on a phone, for details.

**Calculator:** your current balance (shared with the tracker), interest rate (APR), monthly payment and first payment month. It shows the next payment's start balance, interest cost, principal payment and final balance, plus total principal, total interest cost and the payoff date for the whole loan.

**Mobile friendly:** on phones the tabs move to a bottom bar, buttons are sized for thumbs, and charts are drawn at phone size so they stay readable. Dark mode follows your device setting.

## Use it

**Online (GitHub Pages):** In your repo, go to **Settings → Pages**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`, and save. The app will be live at `https://<your-username>.github.io/<repo-name>/` in a minute or two.

**On your phone's home screen:** open the GitHub Pages link, then use **Share → Add to Home Screen** (iPhone) or **⋮ → Add to Home screen / Install app** (Android). It opens full screen with its own icon.

**Locally:** Download `index.html` and open it in Chrome, Safari, Edge or Firefox.

You can link straight to a tab with `#schedule`, `#chart` or `#calc`.

## Privacy

Your numbers never leave your device. Nothing is sent to a server. Data is stored per browser and per site, so:

- The GitHub Pages version and a local copy keep separate histories.
- On iPhone, the home-screen app keeps its own data, separate from Safari. Pick one place to track.
- Clearing your browser data erases it.

## Tech

`index.html` holds the whole app (inline HTML, CSS and JavaScript). The other files are the home-screen icons and `manifest.webmanifest`.

- Money is stored as whole cents to avoid rounding errors
- Payoff math is standard monthly amortization (interest = balance × APR ÷ 12), assuming a fixed rate and no new charges
- Charts are hand-drawn SVG, with no library
- Sounds are made with the Web Audio API, so there are no audio files. Browsers only allow sound after you interact with a page, so if the browser blocks it at launch, the start-up jingle plays on your first tap, click or key press instead
- Confetti is drawn on a plain `<canvas>`, with no library
- Respects `prefers-reduced-motion` and `prefers-color-scheme`

## License

MIT. See [LICENSE](LICENSE).
