# Super POS & Inventory — Releases

Installation, upgrade and release notes for **Super POS & Inventory**.

Download the latest installer from
<https://github.com/ismail-vmi/pointofsale/releases/latest>.

Developed by **CodeUmbrella** — Muhammad Ismail · ismailamin.pk@gmail.com · 03061600937

---

## Installing for the first time

1. Download **`SuperPOSInventory-<version>-Setup.exe`** from the latest release.
   (Releases up to v1.1.2 were published as `SufiyanEnterprisesPOS-<version>-Setup.exe`. Automatic
   updates are unaffected by the rename — the app downloads whatever `latest.yml` names, and never
   guesses a filename.)
2. Run it. Windows SmartScreen will warn that the publisher is unknown, because the installer is
   not code-signed. Choose **More info → Run anyway**.
3. Pick an install folder (the default is fine) and finish. A desktop and Start-menu shortcut are
   created.
4. Start the app. The first launch opens a short setup wizard — there is no default password and
   no seeded account:

   - **Store information:** shop name (required), branch, address, phone, email, currency and tax.
   - **Administrator:** your name, an email address and/or mobile number, and a password you
     choose. At least 10 characters, with a letter and a number.

   You are signed in automatically once it finishes. Either the email address or the mobile
   number works as the login name from then on.

5. **Keep that password safe.** It is stored only as a scrypt hash inside the encrypted database,
   so nobody — including the developer — can recover or reset it for you.
6. Open **Settings** to fill in anything the wizard did not ask about: receipt width, printer,
   document numbering and backup schedule.

**Requirements:** Windows 10 or 11, 64-bit. About 300 MB of disk space plus room for your data. No
internet connection is needed to use the system.

## Upgrading an existing installation

You do not need to do anything by hand. When a new version is published, the running app shows an
**Update** button in the title bar; click it, read what changed, choose **Download update**, then
**Restart to update**.

To upgrade manually instead, download the new setup file and run it over the top of the existing
installation. Do not uninstall first.

**Your data is safe either way.**

- The installer only replaces the program files. Everything you have entered lives in
  `%APPDATA%\sufiyan-enterprises-pos\` and is not touched.
- Before any change to the database's structure, the app copies your database into the backups
  folder as `superpos_pre_upgrade_…​.db` (`sufiyan-pos_pre_upgrade_…​.db` in builds before v1.2.0 —
  both are listed and both restore). If that copy cannot be written, the upgrade does not proceed
  and nothing is changed.
- Each structural change is applied in a transaction. If one fails, your database stays on the last
  version that worked and the app tells you.
- Uninstalling only offers to delete business data during a real uninstall, and it defaults to
  keeping it. An update never asks.

**Before a major upgrade**, it still costs nothing to take a manual backup: *Backup & Restore →
Create backup*, then copy the file somewhere off the machine.

## Rolling back

Only the current release is published. Superseded versions are removed once a newer one is
available, so there is no older installer to download — if a release causes you a problem, contact
support rather than trying to go backwards.

**Your data is still safe either way.** Before any version upgrades your database it writes a
complete copy of it first, and that copy stays on your computer:

1. Open *Backup & Restore*.
2. Restore the `superpos_pre_upgrade_…​.db` copy taken just before the upgrade (older
   installations may have one named `sufiyan-pos_pre_upgrade_…​.db`).

A database that has been upgraded by a newer version is refused rather than opened by an older
one, so restoring that pre-upgrade copy is the step that matters — not reinstalling an old build.

## Where your data is

`%APPDATA%\sufiyan-enterprises-pos\` — paste that into the address bar of File Explorer, or use
*Backup & Restore → Open data folder*.

The folder name is older than the product's current name, and is kept that way on purpose: it is
where every existing installation's data already is, and renaming it during an upgrade would look
exactly like losing the business. It is an internal path and appears nowhere else.

```
data/       your encrypted database and its key
backups/    every backup, including the automatic ones
images/     product photos and the shop logo
invoices/   generated invoice PDFs
exports/    Excel exports
logs/       application log, useful when reporting a problem
```

### Your data is locked to this computer and this Windows account

The database is encrypted, and its key is sealed by Windows itself against your user account on
this machine. That is what makes a stolen laptop or a copied file harmless.

It also has a consequence worth knowing **before** you need it:

> **Backups restore only on the computer that made them.** Copying `sufiyan-pos.db`, or a backup
> file, to a different computer or a different Windows account will not make it readable there.

So a backup protects you against the things that actually go wrong day to day — a mistaken
deletion, a bad import, a failed disk in the same machine — and it is well worth keeping. It is
not, on its own, a way to move your shop to a new computer.

**If you are replacing the computer, contact support before you wipe the old one.** Export what
you need to Excel while the old machine still works. A proper "move to a new computer" feature is
planned; until it exists, please do not assume your backups will open elsewhere.

---

## Release notes

### v1.2.2 — you choose your own administrator password

**Your data, your users, your settings and the way the system works are unchanged.** Upgrading is
the same as always: install over the top, and everything is where you left it.

**No more shared default password.** Until now every copy of the software started with the same
built-in administrator and the same password, and that password was printed in the documentation.
That was fine when the software was handed to one shop in person. It is not fine for a product
anyone can download.

A **brand-new installation** now opens a short setup wizard instead:

- **Store information** — shop name, branch, address, phone, email, currency and tax.
- **Administrator** — your name, an email address and/or mobile number, and a password you choose.

You are signed in automatically when it finishes.

**If you are already using the software, you will not see the wizard.** Your administrator
account, your password and every other user are exactly as they were. The wizard only appears on
an installation that has never been signed into.

Keep your password somewhere safe. It is stored only as a cryptographic hash inside your encrypted
database, so nobody — including the developer — can recover it for you.

**Also in this release**

- The installer now shows the licence agreement before installing.
- Every release publishes SHA-256 checksums, so you can verify a download is genuine before you
  run it. See the release page.
- Full attribution for the open-source components the application uses, and a machine-readable
  software bill of materials.
- Groundwork for signed Windows and macOS builds, which will remove the "unknown publisher"
  warnings once the certificates are in place.
- Preparation for the **Founder Free Period**: the software is free to use, and this release adds
  the internal plumbing to describe that without changing anything you can do. Nothing is
  restricted, nothing is checked over the internet, and no account is required.

**Still true, and staying true**

- Everything works with no internet connection.
- Your business data stays in an encrypted database on your own computer.
- Nothing about your shop is uploaded anywhere.

### v1.2.1 — the new Super POS & Inventory mark

A visual update. Your data, your settings and the way the system works are all unchanged, and there
is nothing to re-enter.

- The software carries its approved mark — the green cube inside a silver sweep, over the words
  *Super POS & Inventory*. It replaces the plain default mark everywhere it appeared: the sign-in
  screen, the round application button at the top left, the foot of the navigation pane, the window
  and taskbar icon, and the letterhead on printouts.
- **If you have uploaded your own logo, none of your printouts change.** The product's own mark
  stands in only for a shop that has not uploaded one, exactly as before — upload yours and it
  replaces the default everywhere at once.
- The desktop and Start-menu icons change with this update. If Windows keeps showing the old one for
  a while, that is its icon cache; it clears on the next sign-in.
- The sign-in screen now gives the support phone number beside the support email, so there is a
  number to ring on the one screen you can reach without signing in.

### v1.2.0 — the application takes your shop's name, not somebody else's

The application is now **Super POS & Inventory**, and it carries no shop's name of its own. Wherever
a business used to be named in the software, it now shows *your* business — the name, branch,
address, phone, email and logo you enter under **Settings → Store**.

**Your data is untouched by this.** Everything stays exactly where it is, in the same folder, in the
same encrypted database, opened with the same key. Your registered store name, your uploaded logo,
your invoices, customers, purchases and backups all carry straight over. Update over the top as
usual; there is nothing to move and nothing to re-enter.

**Your details, everywhere**

- Your store name, branch, address, phone and email now appear on the sign-in screen, the title bar,
  the sidebar, the dashboard and the status bar — and on every invoice, receipt, quotation, delivery
  challan, goods received note, credit and debit note, customer statement, payment receipt, stock
  slip, report and Excel export.
- **Changes appear immediately.** Type a new name, press *Save*, and the whole application follows at
  once — including the next print preview. No restart, no reopening the window.
- The line at the foot of a printout telling you who to ring about the *software* is now clearly
  separate from your own letterhead, so a customer can never mistake one for the other.

**Sensible defaults instead of blanks**

- Leave any store field empty and it falls back to a sensible default rather than printing a gap.
  Each field on the Settings screen tells you what it will fall back to.
- Extra spaces are tidied up as you save, and a name that is nothing but spaces is treated as empty
  rather than printed as a blank letterhead.
- Names in any language are preserved exactly as typed.

**A default logo**

- A new shop, or one that has not uploaded a logo, now gets a clean default mark on screen and on
  paper instead of plain text. It is designed to stay legible on a thermal receipt and in black and
  white.
- Upload your own logo and it replaces the default everywhere at once; remove it and the default
  comes back. The Settings screen always shows which of the two is in use.
- If your logo file is ever moved or deleted, printouts fall back to the default instead of coming
  out with a hole in the letterhead — and Settings tells you the file is missing.

**Also**

- The installer is now `SuperPOSInventory-<version>-Setup.exe`. Automatic updates are unaffected by
  the rename.
- New backup files are named `superpos_…`. Backups taken by earlier versions keep their old names and
  remain listed and restorable.
- The application folder, the database file and the update identity are all deliberately unchanged,
  which is what makes this update safe for existing shops. See
  [Where your data is](#where-your-data-is).

### v1.1.2 — a clearer message when the database cannot be unlocked

A maintenance release. Nothing you use day to day has changed.

- *Fixed: if this computer's secure keystore refused to unlock the database key, the startup message
  was the internal fault text — "Error while decrypting the ciphertext provided to
  safeStorage.decryptString" — which tells a shop nothing.* It now names the usual cause (a data
  folder copied from another computer or another Windows account) and says to restore the most
  recent backup. The key itself, and the way it is sealed, are unchanged.

The rest of this release is developer tooling: the sample database used to review printouts can now
produce a quotation and a goods received note, and the preview folder is emptied between runs so a
document left over from a previous run cannot be mistaken for a current one.

### v1.1.1 — readable update notes

- *Fixed: the "what's new" panel in the update dialog showed the raw HTML of the release notes —
  `<p><strong>…` — instead of the notes themselves.* GitHub hands the application the release notes
  already rendered as HTML, and the dialog shows them as plain text on purpose, so that nothing
  published on a release page can be rendered as markup inside the till. The tags are now taken out
  before the notes are shown: one bullet per point, and the author's line wrapping no longer breaks
  sentences in half.

Because the panel is drawn by the version you are *running*, notes will look right from this
version onwards — the dialog that offered you v1.1.1 was still drawn by v1.1.0.

### v1.1.0 — printed documents, the shop logo, goods received notes

**Every document the shop hands over now prints properly**

- Eleven printable documents share one design and one rendering path: A4 invoice, sales receipt
  (58 mm and 80 mm), quotation, return / credit note, payment receipt, purchase order, goods
  received note, supplier return / debit note, customer statement, stock movement slip and any
  report.
- Each one has an on-screen preview that renders from exactly the same code as the printer, so what
  you approve is what comes out.
- Barcodes and the invoice number print as a scannable barcode where there is room for one.

**Your logo on everything**

- *Settings → Logo*: upload a PNG, JPG, WebP or SVG once and it appears on every A4 document and, in
  black and white, on the thermal receipts. It can be previewed, replaced and removed.

**Goods received notes**

- Receiving stock against a purchase order now produces a numbered GRN you can print — what
  arrived, against which order, what is still outstanding, and what the delivery was worth.
- Deliveries you received *before* this version are not missing: on first launch the app rebuilds a
  note for each one from the stock ledger. No figure anywhere is changed — stock, costs and the
  supplier balance are still driven by receiving exactly as before.

**Customer statements**

- A printable statement for any customer over any date range: opening balance, every invoice,
  return and payment in order, and the closing balance.

**Keeping the installed copy working**

- *Fixed: after a development build had been run on the same computer, the installed application
  refused to start with "this database was created by a newer version of the application".* Test
  builds now keep their data in a folder of their own, so they cannot leave the shop's database in a
  state the installed version does not understand.
- If a copy of the application ever does meet a database from a newer version, it no longer stops at
  an error. It explains that only the program files are behind, and offers **Get the latest version**
  and **Open the data folder**.

**Also**

- macOS installers are built and published alongside the Windows one.

### v1.0.0 — first public release

The complete offline point-of-sale and inventory system.

**Selling**

- Fast till with barcode and SKU entry, held sales, per-line and invoice-level discounts, tax,
  partial payments and change.
- Thermal receipts at 58 mm and 80 mm with an on-screen preview that renders from the same code as
  the printer, so what you see is what prints.
- Returns against an invoice restock the goods and credit the customer; cancelling an invoice
  reverses every stock movement. Nothing financial is ever deleted.

**Quotations**

- Formal estimates that move no stock and take no money, with validity dates, staff-only notes,
  payment terms and a printable document.
- A full status trail — draft, sent, accepted, rejected, expired, cancelled — and one-click
  conversion into a real invoice, which is the only moment stock moves.

**Products and inventory**

- SKU, barcode, categories, purchase and sale prices, per-product discounts, reorder levels, photos,
  and a history of every price and discount change.
- A permanent stock ledger: every movement is a row that is never edited or removed. Adjustments,
  damage and expiry write-offs, and transfers each have their own movement type.

**Purchases and suppliers**

- Purchase orders, partial and full receiving, supplier returns and payments.
- Stock and the supplier balance move when goods are *received*, not when they are ordered, and a
  partial delivery accrues only its own share of the value.
- A supplier ledger that reconciles to the balance.

**Customers and credit**

- Customer accounts with a running ledger, a dues screen, and printable payment receipts.
- Payments settle the oldest invoices first unless allocated by hand; anything left over stays on
  the account as credit rather than being lost.
- Credit belongs to a named customer — the shared walk-in record cannot run a balance.

**Excel, reports and printing**

- Product import with a preview step, then an all-or-nothing apply that re-validates the file
  inside one transaction.
- Filtered exports of every list, with money written as real numbers so columns can be summed.
- 13 reports with filters, A4 printing and Excel export, all sharing one result shape so the
  screen, the print and the export cannot disagree.

**Global search**

- One field in the title bar, or **Ctrl+K** anywhere, searches products, invoices, quotations,
  customers, suppliers and purchases at once.
- Suggestions appear from the second character, ranked so an exact SKU, barcode, invoice number or
  mobile number always comes first, and always offering at least three places to go.
- The full results screen also searches inside invoice, quotation and purchase lines, so a product
  code finds every document that ever sold or ordered it.
- Only the modules your role can open are searched, and the screen says what it left out.

**Automatic updates**

- The app checks this repository's releases shortly after launch and every four hours, and shows an
  **Update** button in the title bar when a newer version exists.
- Downloading and installing are both explicit choices; a version can be skipped, and **Check for
  updates** in the application menu asks at any time.
- Installing closes the database cleanly first, and the new version upgrades your data
  automatically on its first launch — after copying it aside.

**Users, security and data**

- Six built-in roles, 43 permissions, per-user overrides, login history and a non-deletable super
  administrator.
- The database is encrypted with SQLCipher and its key is sealed with Windows DPAPI.
- Manual, scheduled, pre-restore and pre-upgrade backups. Every backup is a byte copy of the
  encrypted database and is validated before any restore, which itself takes a safety copy first.
- A full audit log of who changed what.

**Fixed in this release**

- *"better_sqlite3.node is not a valid Win32 application" on a fresh install.* The database engine
  is now located by absolute path instead of being searched for around the installed files, it is
  checked before it is loaded so a damaged copy produces a message you can act on, and the build
  itself now refuses to produce an installer around an engine it cannot verify.

**Known limitations**

- The installer is not code-signed, so Windows SmartScreen warns on first run and during automatic
  updates. A signing certificate would remove both warnings.
- Windows 64-bit only. A macOS build can be produced from the same source on a Mac.

---
