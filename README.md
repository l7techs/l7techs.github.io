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

## 963 Aqar

- Shared property links: `https://l7techs.github.io/aqar/property/<property id>`
- With the app installed, the link opens the property in the app (Android App Links / iOS Universal Links).
- Without it, `404.html` / `aqar/index.html` sends iPhone users to the App Store (id 6832349568) and Android users to
  Google Play (`com.l7techs.aqar`, referrer `property=<id>`); on Android it first tries to open the app.
- `404.html` serves both apps: paths starting with `/aqar/` get Aqar's branding and store links, everything else keeps
  963 Sale's behaviour.
- `.well-known/assetlinks.json` — Android: package `com.l7techs.aqar`, Play app-signing and upload key SHA-256.
- `.well-known/apple-app-site-association` — iOS: `CHF2B23FTZ.com.l7techs.aqar`, paths `/aqar/property/*`.
- Link previews (WhatsApp, etc.) for `/aqar/property/<id>` come from `404.html`'s static tags, which are 963 Sale's:
  crawlers don't run the script that switches the branding.

Keep the `/sale/` and `/aqar/` paths stable: links already shared in chats depend on them. Another app can be added under its own path
by adding its entries to both `.well-known` files and a branch in `404.html`.
