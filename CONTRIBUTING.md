# 参与船长密码箱

谢谢愿意来帮忙！修错字、补文档、报问题、写代码都欢迎。

## 动手之前

- 小改动（修 bug、改文档、调界面）直接提合并请求就行。
- 新功能先开个议题聊一下。碰到加密、保险库格式、解锁流程的改动，一定先聊。
- 安全问题别公开，按 [SECURITY.md](https://github.com/heihuzi-labs/.github/blob/main/SECURITY.md) 私下报告。对密码管理器来说，这一条最要紧。

## 跑起来

需要 Node.js 22 和 Rust。

```sh
npm ci
npm run tauri dev
```

开发时请新建一个测试用的保险库，别拿自己真正在用的那个调试。

## 提交前跑这些

和自动检查跑的一样：

```sh
npm run build
cargo check --locked --manifest-path src-tauri/Cargo.toml
```

改了界面请附截图。

## 这几条请特别注意

- **绝对不要提交真实的密码。** 示例数据、测试、截图里只用 `demo@example.com` 这种假账号和随手生成的假密码。截图前先确认界面上没有真实条目。
- **别让老用户打不开保险库。** 保险库的加密方式、文件格式、存放位置（数据目录名 `CaptainPassword`）改动时，要能读懂旧格式并自动升级，并在合并请求里写清楚怎么测的。
- **不加新的联网动作。** 现在唯一联网的是检查新版本。
- 敏感数据用完要清掉：解锁用的密钥、主密码不要写进日志，不要长时间留在内存里（用 `zeroize`）。
- 应用和安装包的英文名 `CaptainPassword` 别改，老版本检查更新、各平台文件名都靠它。

## 合并请求

写清楚改了什么、为什么、怎么验证的，模板里都有。一个合并请求只做一件事。

提交的代码按 [MIT](LICENSE) 许可证发布。

---

## Contributing (English)

Thanks for helping! Typos, docs, bug reports and code are all welcome.

- Small fixes: open a pull request directly. New features: open an issue first, and always discuss changes to encryption, the vault format or the unlock flow before writing them. Security problems: report privately, see [SECURITY.md](https://github.com/heihuzi-labs/.github/blob/main/SECURITY.md); for a password manager this matters most.
- Setup: Node.js 22 and Rust. `npm ci`, then `npm run tauri dev`. Create a throwaway vault for development; never debug with your real one.
- Before submitting (same as CI): `npm run build` and `cargo check --locked --manifest-path src-tauri/Cargo.toml`. Attach screenshots for UI changes.
- Never commit real passwords: sample data, tests and screenshots use fake accounts like `demo@example.com`. Existing vaults must keep opening: changes to encryption, file format or location (data folder `CaptainPassword`) need to read the old format and migrate. No new network calls; the update check is the only one. Wipe secrets after use (`zeroize`) and never log them. Keep the ASCII name `CaptainPassword`; update checks and installer names depend on it.
- Contributions are released under the [MIT](LICENSE) license.
