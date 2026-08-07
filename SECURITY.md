# Security Policy — Super POS & Inventory

**CodeUmbrella** · Last updated 7 August 2026

---

## Reporting a vulnerability

If you believe you have found a security vulnerability, please report it privately.

**Email:** ismailamin.pk@gmail.com — subject line beginning `SECURITY:`

Please **do not** open a public GitHub issue, post it publicly, or disclose it on social media
before it has been fixed. This software runs the till in small retail businesses; a public
disclosure puts those shops at risk before they can update.

### What to include

- What the issue is and why you think it is a security problem
- Steps to reproduce it
- The application version (shown in the About panel) and your operating system
- Whether it requires an authenticated session, and at what permission level
- Any proof-of-concept — **with no real business data in it**

### What to expect

| | |
|---|---|
| Acknowledgement | Within 5 working days |
| Initial assessment | Within 14 days |
| Fix for a confirmed critical issue | As soon as practicable, in a patch release |
| Credit | Offered in the release notes, unless you prefer otherwise |

CodeUmbrella is a small independent developer. There is no paid bug bounty programme.

### Safe harbour

We will not pursue action against you for good-faith security research that:

- respects the privacy of others and does not access, modify or destroy real business data
- does not degrade or disrupt any service
- does not use social engineering, phishing or physical attacks
- gives us reasonable time to fix the issue before public disclosure

---

## Supported versions

| Version | Supported |
|---|---|
| 1.2.x | ✅ |
| 1.1.x | ⚠️ Upgrade advised |
| 1.0.x | ❌ |

Security fixes are issued for the latest release. Updating is done from within the application —
the title bar shows an **Update** button when a newer version is published.

---

## How the application is built

Useful context for anyone assessing it.

### Data protection

- The business database is **SQLite encrypted with SQLCipher** (via `better-sqlite3-multiple-ciphers`).
- The 256-bit key is generated on the machine at first launch and sealed with **Windows DPAPI** or
  the **macOS Keychain** through Electron `safeStorage`. Copying the database to another computer
  does not make it readable.
- Backups are byte copies of the encrypted file, so they are encrypted too.
- Passwords are stored as **scrypt** hashes (N=16384, r=8, p=1, 64-byte key, 16-byte salt) and
  compared in constant time. There is **no default or recoverable password** — the first
  administrator is created by the shop during first-run setup.
- The database never leaves the computer. No business data is transmitted anywhere.

### Application boundary

- Electron **context isolation is enabled**; **Node integration is disabled**; `webviewTag` is off.
- The renderer reaches the system through a **fixed allowlist of IPC channels** in the preload
  bridge. It cannot name a channel that does not exist, and it has no filesystem, database or
  Electron API access.
- **Every privileged IPC handler re-checks permissions in the main process.** Authority lives
  there, not in the renderer — a tampered renderer cannot grant itself anything.
- Navigation is restricted to `file://`; every window-open request is denied and `http(s)` links
  are handed to the system browser.
- All file paths originate from an OS file dialog or from the application's own data directory.
  The renderer never supplies a path.
- Release notes fetched from GitHub are stripped to plain text before display, so nothing
  published on a release page can render as markup inside the application.

### Known limitations

Stated plainly rather than left to be discovered:

- **Installers are not yet code-signed.** Windows SmartScreen warns about an unknown publisher and
  macOS Gatekeeper requires an override. Code signing and notarization are in progress. Until
  then, verify downloads against the published SHA-256 checksums.
- **If the OS keystore is unavailable**, the database key is written to disk unwrapped and
  protected only by file permissions. The database itself stays encrypted. This is logged as a
  warning when it happens.
- **Anyone with administrator access to the computer, signed in as the same OS user, can decrypt
  the database.** The encryption protects against a stolen disk or a copied file, not against a
  compromised user account.
- **The application does not defend against a compromised operating system.**

---

## Verifying a download

Every release publishes `SHA256SUMS.txt`. Check your download before installing:

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

On Windows PowerShell:

```bash
Get-FileHash .\SuperPOSInventory-1.2.2-Setup.exe -Algorithm SHA256
```

Compare the result against the line for that file in `SHA256SUMS.txt`.

Only download from [codeumbrella.com](https://codeumbrella.com) or the official GitHub releases
page at `github.com/ismail-vmi/pointofsale/releases`. Installers offered anywhere else are not
ours and may be modified.

---

## Contact

**CodeUmbrella** — Muhammad Ismail · ismailamin.pk@gmail.com · [codeumbrella.com](https://codeumbrella.com)
