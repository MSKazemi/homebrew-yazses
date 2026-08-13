# MSKazemi/homebrew-yazses

Homebrew tap for **[YazSes](https://github.com/MSKazemi/yazses)** — free, open-source,
**offline** hold-to-talk voice dictation for Linux, macOS and Windows. Hold a key, speak,
release; your speech is transcribed on-device with
[faster-whisper](https://github.com/SYSTRAN/faster-whisper) and typed into whatever app
has focus. No cloud, no account, no subscription.

## Install

```sh
brew tap MSKazemi/yazses
brew install --cask yazses
```

Upgrade with `brew upgrade --cask yazses`, remove with
`brew uninstall --zap --cask yazses`.

## Read this before you install

**Apple Silicon only.** The cask declares `depends_on arch: :arm64` and will refuse to
install on an Intel Mac. That is deliberate and it is not a policy choice — the `.dmg` is
built host-arch on GitHub's `macos-latest` runner, which is an arm64 image, so the bundle
carries no `x86_64` slice and cannot launch on Intel. Refusing is better than installing an
app that silently never starts.

**On an Intel Mac, install from PyPI instead** — same daemon, same CLI, architecture
independent:

```sh
pipx install yazses
yazses quickstart
```

**The app is unsigned.** macOS Gatekeeper will block the first launch: right-click
**YazSes.app** → **Open** → **Open**. You only do this once per version. Signing and
notarisation are wired into CI already and switch on as soon as an Apple Developer
Program certificate is available.

**It needs two permissions.** Accessibility (to see the hotkey) and Microphone (to hear
you). macOS prompts for both; the cask's caveats repeat the exact panes.

Full walkthrough: **[docs/macos-install.md](https://github.com/MSKazemi/yazses/blob/main/docs/macos-install.md)**

## What's in here

| Path | What it is |
|---|---|
| `Casks/yazses.rb` | The cask. Byte-identical to `packaging/homebrew/yazses.rb` in the main repo, which is the source of truth. |

The version and checksum are regenerated from the assets actually attached to each
release tag by `scripts/refresh-package-manifests.py` in the main repo — never
hand-copied, because a wrong hash makes Homebrew refuse the download and the project
look broken to someone seeing it for the first time.

## Links

- **Project:** https://github.com/MSKazemi/yazses
- **Homepage & docs:** https://mskazemi.com/yazses/
- **Report a problem:** https://github.com/MSKazemi/yazses/issues

Issues and pull requests belong in the **main repo**, not here — this tap holds nothing
but the cask.

## Licence

The cask in this repository is Apache-2.0, matching YazSes itself.
