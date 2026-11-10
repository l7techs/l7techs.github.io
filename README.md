# l7techs.github.io

Link domain for the L7 Techs apps. Not a website — it only makes shared links work.

## 963 Sale

- Shared listing links: `https://l7techs.github.io/sale/listing/<listing id>`
- With the app installed, the link opens the listing in the app (Android App Links / iOS Universal Links).
- Without it, `404.html` / `sale/index.html` sends iPhone users to the App Store and Android users to Google Play
  (on Android it first tries to open the app, which helps inside in-app browsers).
- `.well-known/assetlinks.json` — Android: package `com.l7techs.sale`, Play app-signing and upload key SHA-256.
- `.well-known/apple-app-site-association` — iOS: `CHF2B23FTZ.com.l7techs.sale`, paths `/sale/listing/*`.
- `.nojekyll` keeps GitHub Pages from dropping the `.well-known` folder.

Keep the `/sale/` paths stable: links already shared in chats depend on them. Another app can be added under its own path
(e.g. `/aqar/`) by adding its entries to both `.well-known` files.
