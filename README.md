# ChristianMoesl's Homebrew tap

Homebrew formulas for ChristianMoesl's tools.

## Radar

[Radar](https://github.com/ChristianMoesl/radar) is a terminal dashboard for tasks
and development workspaces.

**Status: awaiting the first Homebrew-compatible Radar release.** The tap
repository is public, but `Formula/radar.rb` has not been published yet. The
current `v0.2.1` release predates the setup and manual-page support required by
the prepared formula.

Once the formula is published, installation will be:

```sh
brew install ChristianMoesl/tap/radar
radar
```

The formula will install Radar, its notification companion, manual pages, fd,
tmux and gh. Git must already be on PATH. Pi and Node.js/npm remain user-managed;
Radar setup checks them without installing them automatically.

## Maintaining the formula

The formula template and generator are maintained in the Radar repository under
`scripts/homebrew/`, not independently in this tap.

1. Publish a new stable Radar release containing Homebrew support and approve
   its matching npm package.
2. Run Radar's **Homebrew formula** workflow for that release. It authenticates
   the release metadata, verifies both macOS archives and matching public npm
   package, and tests the candidate on a macOS runner.
3. Review the generated `Formula/radar.rb` and publish it here.

Updates use `brew upgrade radar`. Pi core and profile-managed Pi extensions have
separate update ownership. Existing configuration, notes and workspaces are not
removed by the formula.
