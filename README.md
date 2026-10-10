# ChristianMoesl's Homebrew tap

Homebrew formulas for ChristianMoesl's tools.

## Radar

[Radar](https://github.com/ChristianMoesl/radar) is a terminal dashboard for tasks
and development workspaces.

**Status: awaiting the notifier-registration fix in a new Radar release.**
The `v0.3.0` candidate was authenticated, but current Homebrew blocks app
registration from formula install hooks. The fix moves registration into
Radar's interactive notification setup. No failing formula is published on
`main`; the install command below will become available after the fixed release
passes native Apple Silicon and Intel checks.

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
   package, and tests the candidate with current Homebrew on Apple Silicon and Intel.
3. Review the generated `Formula/radar.rb`, validate it, and commit it directly
   to `main`. Pull requests are used only when explicitly requested.

Updates use `brew upgrade radar`. Pi core and profile-managed Pi extensions have
separate update ownership. Existing configuration, notes and workspaces are not
removed by the formula.
