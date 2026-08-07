# Privacy Policy — Super POS & Inventory

**CodeUmbrella** · Draft of 7 August 2026 · Applies to version 1.2.2 and later

> **[LEGAL REVIEW REQUIRED]** This is a professionally structured draft. It has not been reviewed
> by a qualified lawyer. Before publication, counsel must confirm it satisfies the privacy law of
> every market you sell into — in particular GDPR (EU/UK) if you sell there, and the disclosure
> requirements of the Microsoft Store and Apple App Store, both of which require a published
> privacy policy URL.

---

## The short version

**Super POS & Inventory does not send your business data anywhere.**

Your products, customers, suppliers, invoices, sales, purchases, stock, reports, passwords and
backups are stored in an encrypted database **on your own computer**. CodeUmbrella cannot see
them, does not receive a copy of them, and has no way to access them.

The application works fully offline. The only thing it currently sends over the internet is a
check for a newer version.

---

## What stays on your computer

Everything you record. Specifically:

| | |
|---|---|
| Products, categories, barcodes, prices, images | Local only |
| Customers, suppliers, contact details, credit accounts | Local only |
| Invoices, sales, returns, quotations, delivery challans | Local only |
| Purchases, goods receipts, supplier payments | Local only |
| Stock levels, movements, adjustments, transfers | Local only |
| Reports and Excel exports | Local only |
| Users, roles, permissions, audit logs, login history | Local only |
| Passwords (as scrypt hashes — never plain text) | Local only |
| Backups | Local only |

### Where it is stored

- **Windows:** `%APPDATA%\sufiyan-enterprises-pos\`
- **macOS:** `~/Library/Application Support/sufiyan-enterprises-pos/`

The folder name is an internal legacy identifier and does not affect what is stored.

### How it is protected

The database is encrypted with SQLCipher using a 256-bit key generated on your computer at first
launch. That key is sealed by your operating system's own secure store — Windows DPAPI or the
macOS Keychain — so copying the database file to another computer does **not** make it readable.

Backups are byte-for-byte copies of the encrypted database, so a backup on a USB stick is no more
readable than the original.

**CodeUmbrella does not hold your encryption key and cannot decrypt your database or recover your
password.** This is a deliberate design decision. It also means that if you lose your computer and
your backups, we cannot help you recover your data.

---

## What leaves your computer

### Update checks

The application asks GitHub whether a newer version has been published — about 20 seconds after
start-up, then every four hours.

The request is an ordinary HTTPS request for a small metadata file. It contains no business data
and no account information. As with any web request, the server receives your IP address and the
standard request headers.

You can prevent this entirely by blocking the application in your firewall. **The point of sale
continues to work normally with no internet connection at all** — updates simply will not be
offered.

### Support links

If you click a support link, your browser opens a page on `codeumbrella.com`. Nothing is sent from
the application itself.

### Licence verification — not yet active

The Founder Free Period requires no account, no activation and no internet connection. Nothing is
transmitted for licensing purposes today.

When paid subscriptions begin, licence verification will transmit **only**:

- a licence or order identifier
- an anonymous installation identifier (a random value generated on your computer)
- the subscription status and its expiry
- the application version and operating system version
- the activation date

It will **never** transmit products, customers, invoices, sales, purchases, suppliers, stock,
reports, passwords, your database, or any other business data. Verification will be periodic and
non-blocking: an unreachable licensing server will never stop you from making a sale.

This policy will be updated, and the change published, before any such transmission begins.

### Analytics and crash reporting — not present

The application currently contains **no analytics, no telemetry and no crash reporting**. Nothing
is collected about how you use it.

If any of this is ever added it will be **opt-in**, documented here before it ships, and incapable
of carrying business data.

---

## Logs

The application writes technical logs to a `logs` folder inside its data directory — start-up
messages, database schema version, update checks and errors. These stay on your computer and are
never transmitted. If you send a log file to support when reporting a problem, you choose to do
that; nothing sends it automatically.

---

## Children

The Software is business software and is not directed at children.

---

## Your rights over your data

Because your data never leaves your computer, you exercise most data rights directly:

- **Access and portability** — export to Excel from within the application, or copy the database
  file itself.
- **Correction** — edit any record in the application.
- **Deletion** — delete records in the application, or uninstall and choose to remove the data
  folder. The uninstaller asks; choosing "No" keeps your data for a future reinstall.

There is nothing for CodeUmbrella to disclose, correct or delete, because we hold nothing.

> **[LEGAL REVIEW REQUIRED]** If you sell into the EU/UK, counsel must confirm whether
> CodeUmbrella is a data controller for anything at all under this architecture, and what the
> position becomes once licence verification begins.

---

## Changes

Material changes will be published here and noted in the release notes. The version of this policy
distributed with your copy applies to that copy.

---

## Contact

**CodeUmbrella** — Muhammad Ismail
[codeumbrella.com](https://codeumbrella.com) · ismailamin.pk@gmail.com

> **[LEGAL REVIEW REQUIRED]** A registered business address may be required for store listings and
> for privacy law in some markets. Confirm what must be published.
