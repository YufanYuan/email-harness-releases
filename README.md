# Email Workbench downloads

Downloadable desktop trial builds of Email Workbench. This repository contains release packages and download instructions. The development repository is private.

## Download

- [Latest main release](https://github.com/YufanYuan/email-harness-releases/releases/latest): historical builds from main, each with its own version tag.
- [Development autobuild](https://github.com/YufanYuan/email-harness-releases/releases/tag/autobuild): latest successful dev build, marked as a prerelease. This download changes over time.

Packages become available after the release pipeline is enabled and its first build succeeds. If a link has no release yet, no download has been published.

| Computer | Package |
| --- | --- |
| Mac with Apple Silicon (M-series) | `Email-Workbench-mac-arm64.zip` |
| Windows with Intel/AMD 64-bit processor | `Email-Workbench-win-x64.exe` |

Each release includes `SHA256SUMS` for checking the downloaded files. Choose the architecture that matches your computer. New builds target macOS Apple Silicon and Windows x64; Intel Macs, Windows ARM and Linux are not built. Older releases may still contain an Intel Mac package.

Download your selected package and SHA256SUMS into the same directory. For an Apple Silicon Mac, check just that package:

```sh
grep '  Email-Workbench-mac-arm64.zip$' SHA256SUMS | shasum -a 256 -c -
```

On Windows, use `Get-FileHash .\Email-Workbench-win-x64.exe -Algorithm SHA256` in PowerShell and compare the Hash value with that file's line in SHA256SUMS. You do not need to download packages for the other platforms.

## Trying the app

Older alpha builds were unsigned. A macOS build made with the old configuration can have an invalid application signature and show “damaged and can't be opened”; those files are not repaired by later workflow changes. Obtain a corrected release rather than granting an exception to a package whose signature fails verification.

The corrected release workflow requires Developer ID signing and Apple notarization by default. New releases can be published only after the maintainer configures the signing certificate and notarization credentials. Explicit ad-hoc test packages remain unnotarized and require a local Gatekeeper exception; they are not normal trusted downloads.

On macOS, verify the checksum, extract the ZIP and move Email Workbench.app to Applications. Verify its complete signature with `codesign --verify --deep --strict --verbose=2 "/Applications/Email Workbench.app"`. For a notarized release, Gatekeeper should accept the application normally. On Windows, run the portable EXE; no installer is required. Windows builds remain unsigned and SmartScreen may show a warning.

Start by adding your own mailbox. Generic IMAP/POP3 plus SMTP is available; Gmail/Outlook browser login requires publisher registration configuration in that particular build. Each release states whether that configuration was included. No mailbox credentials or local user data are shipped in a release.

The AI feature requires a separately installed native Codex runtime, followed by detection and login inside the app. On Windows this must be a native `codex.exe`; a `codex.cmd` wrapper is not supported. Reading and composing mail do not require enabling AI.

Data is stored locally on each computer. Downloading the app on another computer does not sync local conversations, comments, drafts or settings between computers. Sending still requires explicit human confirmation.

## Release channels

Pull requests run checks without building installation packages; builds and publication run after changes reach dev or main. All expected platform builds and macOS signing/trust checks must succeed before publication. Main releases preserve history. The fixed autobuild is replaced only after a complete new package set is staged; a failed build keeps the previous download available. Releases identify their build time and source revision.

This repository is for trial distribution. Native system integration and real mailbox behavior should be verified on your target computer before relying on an alpha build.
