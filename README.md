# Super POS & Inventory

**Offline point-of-sale and inventory management for retail businesses.**
By [CodeUmbrella](https://codeumbrella.com).

[![Latest release](https://img.shields.io/github/v/release/ismail-vmi/pointofsale?label=latest)](https://github.com/ismail-vmi/pointofsale/releases/latest)

---

## Download

**→ [Get the latest version](https://github.com/ismail-vmi/pointofsale/releases/latest)**

| Platform | File | Requirements |
|---|---|---|
| Windows | `SuperPOSInventory-<version>-Setup.exe` | Windows 10 or 11, 64-bit |
| macOS (Apple Silicon) | `SuperPOSInventory-<version>-arm64.dmg` | macOS 11 or later |
| macOS (Intel) | `SuperPOSInventory-<version>-x64.dmg` | macOS 11 or later |

About 300 MB of disk space, plus room for your own data. **No internet connection is needed to
use it.**

Installation, upgrade and rollback instructions are in [RELEASE.md](RELEASE.md), along with the
release notes for every version.

### Verify your download

Every release publishes `SHA256SUMS-windows.txt` and `SHA256SUMS-mac.txt`. The installers are not
yet code-signed, so Windows and macOS will warn that the publisher is unknown — checking the
checksum is how you confirm the file is genuine.

```bash
Get-FileHash .\SuperPOSInventory-1.2.1-Setup.exe -Algorithm SHA256
```

Compare the result with the line for that file in the checksum file on the release page.

Only download from this repository or from [codeumbrella.com](https://codeumbrella.com).
Installers offered anywhere else are not ours.

---

## What it does

A complete till and stock system for a shop, running entirely on one computer.

- **Sales** — barcode scanning, held sales, returns, quotations, delivery challans
- **Inventory** — stock levels, adjustments, transfers, a full movement ledger
- **Purchasing** — purchase orders, goods received notes, supplier returns and payments
- **Customers** — credit accounts, payments, statements, ageing
- **Printing** — thermal receipts (58 mm and 80 mm) and A4 invoices, quotations, credit notes,
  purchase orders and statements
- **Reporting** — sales, stock, profit, customer and supplier reports, exportable to Excel
- **Excel** — bulk product import and export
- **Users** — roles and per-user permissions, with an audit log
- **Backups** — automatic and manual, with validated restore

### Works offline, always

Everything above runs with the network cable unplugged. The only thing that needs the internet is
checking for a new version, and the till opens normally when that fails.

### Your data stays yours

Your products, customers, invoices, sales and stock are stored in an **encrypted SQLite database
on your own computer**, protected with SQLCipher and a key sealed by Windows DPAPI or the macOS
Keychain. Nothing is uploaded. CodeUmbrella never receives a copy and cannot read it.

See [PRIVACY.md](PRIVACY.md) for exactly what does and does not leave your computer.

---

## Founder Free Period

Super POS & Inventory is **free to use during the Founder Free Period**, currently expected to run
for about two years from public launch. No account, no activation, no internet connection.

This is a promotional period, not a perpetual licence — see [EULA.txt](EULA.txt) section 5. After
it ends, new commercial functionality may require a paid subscription. **Your data will always
remain yours and accessible**, whatever happens to a subscription: expiry never deletes, locks or
withholds your business records.

---

## Updating

The application checks for new versions and shows an **Update** button in the title bar. Click it,
read what changed, download, and install. Your database, backups, images and settings are left
untouched — the installer only replaces the program files.

You can also download and run the new installer over the old one. Same result.

---

## Documentation

| | |
|---|---|
| [RELEASE.md](RELEASE.md) | Install, upgrade, roll back, where your data lives, release notes |
| [EULA.txt](EULA.txt) | End User Licence Agreement |
| [LICENSE.txt](LICENSE.txt) | Copyright and licensing |
| [TERMS.md](TERMS.md) | Terms of sale and service |
| [PRIVACY.md](PRIVACY.md) | What leaves your computer (very little) |
| [SECURITY.md](SECURITY.md) | Reporting a vulnerability, and how the app is built |
| [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt) | Open-source components and their licences |

---

## About this repository

This repository distributes the **releases** of Super POS & Inventory — installers, update
metadata, checksums and the documents above.

**Super POS & Inventory is proprietary commercial software and its source code is not public.**
Development happens in a private repository. Earlier versions of this repository did contain
source code; that does not place it under any open-source licence, and no such licence should be
inferred. See [LICENSE.txt](LICENSE.txt).

Please keep using this repository for updates — every installed copy checks it for new versions.

---

## Support

**CodeUmbrella** — Muhammad Ismail
[codeumbrella.com](https://codeumbrella.com) · ismailamin.pk@gmail.com

Found a security problem? Please report it privately — see [SECURITY.md](SECURITY.md).

---

Copyright © 2026 CodeUmbrella — Muhammad Ismail. All rights reserved.
