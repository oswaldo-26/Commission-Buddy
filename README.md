# Commission Tracker

A free, private app for artists to keep art commissions on track: deadlines, payments, colors, themes, and image receipts. It runs in your browser, installs on your phone like an app, and works offline. No account needed.

**[Open the app](https://oswaldo-26.github.io/Commission-Buddy/)**

---

## What it does

- **Track every commission.** Title, client, deadline, notes, and an optional total price.
- **See what needs attention.** Commissions are grouped into Overdue, Next 7 days, Later, and No deadline.
- **Record payments.** Mark each commission Unpaid, Downpayment paid, or Fully paid, and enter how much was paid and on what date, for the downpayment and for the full payment.
- **Note the design details.** Add the colors to use (names, hex codes, or a color picker) and a free-text theme like "cozy witch" or "cyberpunk city".
- **Make receipts.** Create a receipt for the downpayment or the full payment and save it as a picture, or share it straight to your client.
- **Finish and archive.** Mark a commission as finished and it moves to the Finished tab. Finished commissions that aren't fully paid are highlighted so you don't forget to collect.
- **Make it yours.** Pick light, dark, or automatic mode, and a theme color. The whole app follows it.
- **Back up your data.** Export everything to a file and import it on another device.

## Install it as an app

Open the link above in your phone's browser, then:

| Device | How to install |
| --- | --- |
| **Android (Chrome)** | Tap **Install** on the card that appears after you add your first commission, or open the browser menu and choose **Install app**. |
| **iPhone (Safari)** | Tap the **Share** button, then **Add to Home Screen**. |
| **Computer (Chrome or Edge)** | Click the install icon at the right end of the address bar. |

Once installed, it opens full screen from your home screen and works without internet.

You can also skip installing and just use the link like a normal website.

## Quick guide

### Add a commission
Tap **New commission**, fill in what you know, and tap **Save**. Only the title is required.

### Keep track of payments
- In the editor, choose **Unpaid**, **Downpayment**, or **Fully paid**.
- Choosing Downpayment shows fields for the amount and date received. Choosing Fully paid shows those for the full payment too. Typing an amount fills in today's date, and you can change it.
- Add a **Total price** if you want receipts to show the balance.
- On a commission's card, tap the payment label to move it quickly from Unpaid to Downpayment paid to Fully paid.

### Make a receipt
1. Tap **Receipt** on a commission's card. It appears once a payment amount has been recorded.
2. Choose **Downpayment** or **Full payment** at the top.
3. Enter your name or studio, your currency symbol, and a message for the bottom. These are remembered for next time.
4. Tap **Save image** to download the receipt as a PNG. On phones you can also tap **Share receipt** to send it directly to a chat or save it to your photos.

A receipt shows who paid, what for, the amount, the date, and a receipt number. If you entered a total price, it also shows what has been paid so far and the balance.

### View or edit a commission
Tapping a card opens a read-only view, so nothing changes by accident. To change something, tap the pencil on the card or the **Edit** button in the view.

### Finish a commission
Tap the circle on the card, or use **Mark as finished** in the view. Every quick action (finishing, changing payment, deleting) shows an **Undo** button for a few seconds.

### Change how it looks
Tap the palette icon at the top to pick **Auto**, **Light**, or **Dark** and a theme color.

### Back up your data
Tap the download icon at the top.
- **Export backup** saves a file with all your commissions and receipt settings.
- **Import a backup** adds the commissions from a backup file. If a commission already exists, the backup's version replaces it. Nothing else is deleted.

## Your data and privacy

- Everything is saved **only in your browser, on your device**. There is no server, no account, and no tracking.
- Because of that, your data does **not** sync between devices. To move it, export a backup on one device and import it on the other.
- **Clearing your browser data will erase your commissions.** Export a backup now and then.
- On iPhone, Safari can clear a website's data after about a week of not opening it. An app added to the Home Screen avoids this, but backups are still a good idea.
- The app loads its font from Google Fonts. After the first visit the font is stored on your device for offline use.

## Host your own copy

You can run your own copy for free with GitHub Pages.

1. Create a new repository on GitHub. It can be public.
2. Upload all of these files to the top level of the repository (not inside a folder):

   | File | What it does |
   | --- | --- |
   | `index.html` | The app itself |
   | `manifest.webmanifest` | Lets people install it as an app |
   | `sw.js` | Makes it work offline |
   | `icon-192.png`, `icon-512.png` | App icons |
   | `icon-maskable-512.png` | App icon for Android's adaptive shapes |
   | `apple-touch-icon.png` | App icon for iPhone |

3. Go to **Settings**, then **Pages**. Under **Source** choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. After a minute or two, your app is live at `https://YOURUSERNAME.github.io/REPONAME/`.

Anyone with the link can open the app, but each person only ever sees their own commissions, because they're stored on their own device.

### Updating
Upload the new files over the old ones. The app checks for a new version each time it's opened with internet. If you ever change the icons, also change `commission-tracker-v1` in `sw.js` to a new name (for example `commission-tracker-v2`) so devices pick up the new files.

## FAQ

**Does it cost anything?**
No. It's free to use and free to host on GitHub Pages.

**Do I need an account?**
No.

**Can I use it on my phone and my computer?**
Yes, but each device keeps its own data. Use Export backup and Import a backup to copy your commissions across.

**Where do my receipts go?**
On most devices, Save image puts the file in your Downloads folder. On iPhone, an installed app opens the share sheet instead, where you can choose Save Image or Save to Files. On any phone, Share receipt lets you send it straight to a client or save it to your photos.

**Can I change the currency?**
Yes. Enter your symbol in the Currency symbol field on the receipt screen. By default it's guessed from your device's language and region.

**Does it work offline?**
Yes, after you've opened it once with internet.

**I added a commission but can't see the Receipt button.**
The button appears once you've entered a downpayment or full payment amount on that commission.

## For developers

- A single self-contained `index.html`. No build step, no dependencies, plain JavaScript.
- Storage is the browser's `localStorage`. Receipts are drawn on a `<canvas>` and exported as PNG.
- The colors follow Material You (Material Design 3): a tonal palette is generated in the browser from a single seed color.
- `sw.js` is a small service worker: pages are fetched fresh when online and served from cache when offline.
