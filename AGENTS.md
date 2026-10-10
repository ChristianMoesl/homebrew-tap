# Agent instructions

## Main-first delivery

- Deliver validated changes on `main`. Do not open a pull request unless the user explicitly asks for one.
- Work directly on `main` in a standalone checkout. If using an isolated worktree branch, fast-forward local `main` to the validated commits before reporting completion.
- If `main` advances, rebase unpublished task commits onto current `main`, preserve both changes, rerun relevant checks, then fast-forward. Keep `main` unchanged until validation succeeds.
- Never rewrite `main` or published history, discard user changes, or bypass failing checks. Ask when conflicts require a product decision or user changes prevent safe integration.
- Create a local commit after completing and validating requested changes unless the user asks for read-only work or uncommitted changes. Push only when the user has explicitly authorized publication.
- Use conventional commit messages. For non-trivial changes, explain the motivation and important behavior in the commit body.

## Formula publication

- Generate Radar's formula from its source repository; keep this tap aligned with that template.
- Publish only against an existing, authenticated Radar release and its matching public npm package. Do not replace immutable release artifacts or publish around failed installation tests.
- Test with current Homebrew on native Apple Silicon and Intel. Never disable Homebrew sandboxing or suppress registration failures to make checks pass.
