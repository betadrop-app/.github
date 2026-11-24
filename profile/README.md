<img src="https://betadrop.app/images/logo/BetaDropLogo.png" width="72" alt="BetaDrop" />

# BetaDrop

**Put an iOS or Android beta build in a tester's hands with a link.**

Upload an `.ipa` or `.apk`, get an over-the-air install link. The tester opens it on their phone
and installs from the browser — no TestFlight review wait, no Play track, no tester accounts, and
nothing for them to install first.

**[betadrop.app](https://betadrop.app)** · [Pricing](https://betadrop.app/pricing/) · [Docs](https://betadrop.app/docs/) · [Feedback](https://betadrop.app/feedback/)

---

## Publish from wherever you build

| Repo | Surface | What it does |
|---|---|---|
| **[upload-action](https://github.com/betadrop-app/upload-action)** | GitHub Actions | One step in your workflow. The install link lands on the run summary and, optionally, in a pull-request comment that edits itself on every push. |
| **[betadrop-cli](https://github.com/betadrop-app/betadrop-cli)** | Terminal | `betadrop publish app.ipa`. Prints the install link and a scannable QR code. |
| **[betadrop-mcp](https://github.com/betadrop-app/betadrop-mcp)** | AI assistant | An MCP server, so Claude, ChatGPT, Cursor or Copilot can publish builds, check they will install and read tester feedback. Hosted at `https://api.betadrop.app/mcp`, or run locally. |
| **[fastlane-plugin-betadrop](https://github.com/betadrop-app/fastlane-plugin-betadrop)** | fastlane | `fastlane add_plugin betadrop`, then `betadrop` after `gym` or `gradle`. The install URL lands in `lane_context`. |

[![Marketplace](https://img.shields.io/badge/Marketplace-BetaDrop%20IPA%20%26%20APK%20App%20Distribution-2ea44f?logo=github)](https://github.com/marketplace/actions/betadrop-ipa-apk-app-distribution)
[![@betadrop/cli](https://img.shields.io/npm/v/@betadrop/cli?color=0b64fc&label=%40betadrop%2Fcli)](https://www.npmjs.com/package/@betadrop/cli)
[![@betadrop/mcp](https://img.shields.io/npm/v/@betadrop/mcp?color=0b64fc&label=%40betadrop%2Fmcp)](https://www.npmjs.com/package/@betadrop/mcp)

They all wrap the same API and share one account and one set of tokens. Everything here is MIT.

---

## The 30-second version

**GitHub Actions**

```yaml
- uses: betadrop-app/upload-action@v1
  with:
    file: app/build/outputs/apk/release/*.apk
    token: ${{ secrets.BETADROP_TOKEN }}
```

**Terminal**

```bash
npm install -g @betadrop/cli && betadrop login && betadrop publish ./MyApp.ipa
```

**Claude Code**

```bash
claude mcp add betadrop -s user -- npx -y @betadrop/mcp
```

Each one ends the same way: a link you can send, and a QR code a tester can scan.

---

## One link that never changes

A new build normally means a new link, which means telling everyone again. A
**[standing link](https://betadrop.app/standing-links/)** is a fixed link that always serves the
latest build published to it — set it once in CI and stop re-sending.
Wrap it in the [Download from BetaDrop](https://betadrop.app/download-button/) badge and your own
README stays current on every merge.

---

## Useful things on the site

- [Free Apple Developer account — what you actually get](https://betadrop.app/free-apple-developer-account/) — and what the $99 buys
- [UDID checker](https://betadrop.app/udid-checker/) — reads a UDID off the iPhone itself; no Mac, no cable
- [Download button](https://betadrop.app/download-button/) — a badge for your README that follows the latest build

Bugs and feature requests: open an issue on the relevant repo, or use
[betadrop.app/feedback](https://betadrop.app/feedback/).
