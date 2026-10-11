# ChristianMoesl's Homebrew tap

Homebrew formulas for ChristianMoesl's tools.

## Radar

[Radar](https://github.com/ChristianMoesl/radar) is a terminal dashboard for tasks
and development workspaces. The formula supports **macOS 13 (Ventura) or newer**
on **Apple Silicon (arm64) only**. Intel Macs are not supported.

```sh
brew install ChristianMoesl/tap/radar
radar
```

The formula installs the prebuilt Radar CLI, its notification companion, manual
pages, and default agent-instruction template. Homebrew also installs **fd, tmux
and gh**. **Git, Node.js 24+/npm and Pi 0.85.1+ remain user-managed**; setup checks
them and provides repair instructions without installing these tools for you.

On first launch, or when required tools are missing, `radar` opens setup. It
reviews configuration, creates missing default agent instructions and offers to
install the Pi extension after consent. Homebrew does not edit your configuration,
Pi settings or shell profiles.

If you previously installed Radar into `~/.local/bin`, check `which -a radar` and
resolve PATH precedence before setup. The formula does not remove another install.

### Notifications

Run this in a normal macOS terminal:

```sh
radar setup notifications
```

Choose **Set up / test** to verify and register the notification companion before
launching the test. Homebrew's sandboxed install hooks cannot register the app.
Launch approval and notification permission are separate macOS decisions; neither
is granted automatically. You can defer notifications and still use Radar. Never
disable Gatekeeper or remove quarantine to bypass approval.

### Updates and removal

```sh
brew upgrade radar
radar restart  # if the daemon is running
```

Homebrew owns this installation: do not use `radar update` to replace it. Update
Pi core and the profile-managed Pi extension separately, then reload or restart
active Pi sessions. After a Radar upgrade, rerun notification setup if needed;
a changed app path can require macOS launch approval again.

`brew uninstall radar` removes Homebrew-owned files, not your Radar configuration,
notes, workspaces or Pi profile. Stop the daemon with `radar stop` first if it is
running. Manuals are available with `man radar` and `man radar-config`.

## Maintaining the formula

The formula template and generator live in Radar's `scripts/homebrew/`; do not
maintain an independent implementation here.

1. Publish a new stable Radar release and approve its exact matching npm package.
2. Run Radar's **Homebrew formula** workflow for that release. It authenticates
   signed metadata, verifies the macOS arm64 archive and the public npm package, then
   updates Homebrew and installs/tests/uninstalls on Apple Silicon.
3. Wait for the Apple Silicon job to pass. Download the `homebrew-formula`
   artifact, then review the version, URL, hash,
   prerequisites and installation behavior.
4. Copy the verified `Formula/radar.rb` unchanged, validate it, and commit directly
   to `main`. Pull requests are used only when explicitly requested. Never replace
   published release artifacts or disable Homebrew sandboxing to bypass a failure.

This tap's CI also checks formula style, installation, CLI/manual/notifier tests
and uninstall with current Homebrew on Apple Silicon. Automated tests do not
verify interactive macOS approval or actual notification delivery/clicks.
