<div align="center">

<img src="src-tauri/icons/128x128.png" width="96" alt="Captain Password">

# Captain Password · 船长密码箱

A password manager that lives only on your computer. One master password to unlock, one shortcut to find and copy.

[简体中文](README.md) · English

<a href="https://github.com/heihuzi-labs/captain-password/releases/latest"><img src="https://img.shields.io/github/v/release/heihuzi-labs/captain-password?style=flat-square&label=download" alt="Download"></a>
<img src="https://img.shields.io/badge/macOS%20%C2%B7%20Windows-555?style=flat-square" alt="macOS · Windows">
<img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT">

</div>

![Main window](docs/screenshots/main-detail.png)

## What it is

Passwords saved in the browser are easy to lose; a cloud password service never feels quite right and bills you every month. Captain Password takes the other road: the vault is one encrypted file on your machine. No account, no upload, no sync, and nothing opens without the master password.

The thing you do most is "log into a site, find the password, copy it". So besides the main window there's a quick-search window: press `Option + K` (`Alt + K` on Windows) from anywhere, type a couple of letters, click to copy. No switching back and forth between the browser and the main window.

## A quick look

<table>
<tr>
<td width="50%"><img src="docs/screenshots/setup.png" alt="Create a vault"><br><sub>First launch: pick a name and a master password</sub></td>
<td width="50%"><img src="docs/screenshots/unlock.png" alt="Unlock"><br><sub>Every launch after that starts locked; without the master password you see nothing</sub></td>
</tr>
<tr>
<td><img src="docs/screenshots/edit-item.png" alt="Edit a login"><br><sub>Editing: username, password, several websites, notes, tags</sub></td>
<td><img src="docs/screenshots/password-generator.png" alt="Password generator"><br><sub>Password generator: length, digits, symbols; click "use" when you like it</sub></td>
</tr>
<tr>
<td><img src="docs/screenshots/quick-search-results.png" alt="Quick search"><br><sub>Quick-search window: summon it with the shortcut and search as you type</sub></td>
<td><img src="docs/screenshots/quick-search-detail.png" alt="Quick search copy"><br><sub>Pick an entry, click the username, password or website to copy it</sub></td>
</tr>
</table>

## What it does

- **Logins and passwords**: title, username, password, several websites, notes, tags and an icon; or just a standalone password.
- **Finding and using**: search, favorites, filter by category, copy any field in one click.
- **Generating passwords**: random, memorable or PIN, with adjustable length and character sets and a strength indicator.
- **Quick-search window**: a global shortcut brings it up, and it can stay on top.

The new-item screen also shows secure notes, credit cards, identities and documents, marked "later". They don't work yet.

## Installing

Download from [Releases](https://github.com/heihuzi-labs/captain-password/releases/latest):

| System | File |
| --- | --- |
| Mac (Apple silicon) | `CaptainPassword-v…-macOS-AppleSilicon.dmg` |
| Mac (Intel) | `CaptainPassword-v…-macOS-Intel.dmg` |
| Windows 64-bit | `CaptainPassword-v…-Windows-x64-Setup.exe` |

The installers aren't signed with Apple or Microsoft developer certificates. If macOS says it can't verify the developer the first time, choose "Open Anyway" under System Settings → Privacy & Security. If Windows shows the blue SmartScreen prompt, click "More info → Run anyway".

The app checks for new versions on its own and tells you when one is out.

## Data and security

- The vault is a single SQLite file on your machine; passwords and other sensitive fields are encrypted before they are written.
- The key is derived from your master password with Argon2id, and contents are encrypted with XChaCha20-Poly1305. Locking wipes the key from memory.
- The master password isn't stored anywhere. If you forget it, it can't be recovered; that's the price of a local vault.
- Your data never leaves the machine. The only network call is the update check, which asks GitHub for the latest version number.

To be honest, this is still an early personal project and hasn't had a third-party security audit. Use it for a while yourself, and keep backups, before trusting it with passwords that really matter.

If you find a security problem, please report it privately through GitHub Security Advisories rather than a public issue.

## Building it yourself

You need Node.js 22 and Rust.

```sh
git clone https://github.com/heihuzi-labs/captain-password.git && cd captain-password
npm ci
npm run tauri dev          # development build
npm run tauri -- build     # package
```

It's built with Tauri 2 (Rust backend) + React 18 + TypeScript + Vite. Pushing a `v*` tag makes GitHub Actions build installers for all three platforms and publish them to Releases; see [.github/workflows/release.yml](.github/workflows/release.yml). How the first version was scoped is written up in [ANALYSIS.md](ANALYSIS.md) (in Chinese).

## License

[MIT](LICENSE). The app and installers use the ASCII name `CaptainPassword` so file names stay stable across platforms. The interface is in Chinese for now.

---

<sub>Part of the Captain series from [heihuzi-labs](https://github.com/heihuzi-labs): [Captain Agents](https://github.com/heihuzi-labs/captain-agents) · [Captain Kube](https://github.com/heihuzi-labs/captain-kube) · [Captain Ops](https://github.com/heihuzi-labs/captain-ops) · [Captain Todo](https://github.com/heihuzi-labs/captain-todo) · **Captain Password**</sub>
