# Email Workbench downloads

Downloadable desktop trial builds of Email Workbench. This repository contains release packages and download instructions. The development repository is private.

## Download

- [Latest main release](https://github.com/YufanYuan/email-harness-releases/releases/latest): historical builds from main, each with its own version tag.
- [Development autobuild](https://github.com/YufanYuan/email-harness-releases/releases/tag/autobuild): latest successful dev build, marked as a prerelease. This download changes over time.

Packages become available after the release pipeline is enabled and its first build succeeds. If a link has no release yet, no download has been published.

| Computer | Package |
| --- | --- |
| Mac with Apple Silicon (M-series) | `Email-Workbench-mac-arm64.zip` |
| Mac with Intel processor | `Email-Workbench-mac-x64.zip` |
| Windows with Intel/AMD 64-bit processor | `Email-Workbench-win-x64.exe` |

Each release includes `SHA256SUMS` for checking the downloaded files. Choose the architecture that matches your computer. Windows ARM and Linux are not currently built.

## Trying the app

These are unsigned alpha builds. macOS Gatekeeper and Windows SmartScreen may require you to explicitly approve launching a trusted downloaded application. No signing or notarization is claimed.

On macOS, extract the ZIP, move Email Workbench.app to Applications, and use the system's Privacy & Security controls if macOS blocks the first launch. On Windows, run the portable EXE; no installer is required. Use only packages downloaded from this repository and compare the checksum before granting an exception.

Start by adding your own mailbox. Generic IMAP/POP3 plus SMTP is available; Gmail/Outlook browser login requires publisher registration configuration in that particular build. Each release states whether that configuration was included. No mailbox credentials or local user data are shipped in a release.

The AI feature requires a separately installed native Codex runtime, followed by detection and login inside the app. On Windows this must be a native `codex.exe`; a `codex.cmd` wrapper is not supported. Reading and composing mail do not require enabling AI.

Data is stored locally on each computer. Downloading the app on another computer does not sync local conversations, comments, drafts or settings between computers. Sending still requires explicit human confirmation.

## Release channels

All expected platform builds must succeed before publication. Main releases preserve history. The fixed autobuild is replaced only after a complete new package set is staged; a failed build keeps the previous download available. Releases identify their build time and source revision.

This repository is for trial distribution. Native system integration and real mailbox behavior should be verified on your target computer before relying on an alpha build.
