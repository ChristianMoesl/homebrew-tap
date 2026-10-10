# ChristianMoesl's Homebrew tap

Homebrew formulas for ChristianMoesl's tools.

## Install Radar

[Radar](https://github.com/ChristianMoesl/radar) is a terminal dashboard for tasks
and development workspaces. On macOS (Apple Silicon or Intel):

```sh
brew install ChristianMoesl/tap/radar
radar
```

The formula installs Radar, its notification companion, manual pages, fd, tmux
and gh. Git must already be on PATH. Install [Pi](https://pi.dev) yourself with
Node.js 24+ and npm; these remain user-managed, not formula dependencies.

First launch, or a missing required executable, starts Radar setup. Setup checks
prerequisites and asks before changing configuration or installing Pi extensions.
It does not install CLI tools automatically. Native notifications require the
usual macOS launch approval and notification permission.

If an older installation exists, check `which -a radar pi tmux` for PATH
precedence. The formula never removes other installations.

## Updates

```sh
brew update
brew upgrade radar
radar restart # if the daemon is running
```

Use Homebrew, not `radar update`, to replace the Homebrew-managed files. Pi core
and profile-managed Pi extensions have separate update ownership. Reload or
restart active Pi sessions after updating an extension.

Review Radar's [installation and rollout guidance](https://github.com/ChristianMoesl/radar/blob/main/docs/installation.md#homebrew)
before upgrading. The formula does not migrate or remove user configuration,
notes or workspaces.

## Maintaining the formula

The formula template and generator are maintained in the Radar repository under
[`scripts/homebrew/`](https://github.com/ChristianMoesl/radar/tree/main/scripts/homebrew),
not independently in this tap.

1. Publish a new stable Radar release and approve its matching npm package.
2. Run Radar's **Homebrew formula** workflow for that release. It authenticates
   the release metadata, verifies both macOS archives and matching public npm
   package, and tests the candidate on a macOS runner.
3. Review the generated `Formula/radar.rb` and submit it here. The tap's CI
   installs and tests it on Apple Silicon and Intel before publication.

The first published formula uses [Radar v0.3.0](https://github.com/ChristianMoesl/radar/releases/tag/v0.3.0).
