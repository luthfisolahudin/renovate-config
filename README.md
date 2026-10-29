# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for my public projects.

## Usage

Add this to a repository's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>luthfisolahudin/renovate-config"]
}
```

## Policy

- Wait 7 days after a release before proposing an update (`minimumReleaseAge`).
- Run weekly, Monday before 09:00 Asia/Jakarta.
- Automerge non-major dev dependency updates only after CI passes.
- Require manual approval for major updates.
- Follow Node.js LTS releases; Renovate treats a new major as stable only once it reaches LTS.
- Pin GitHub Actions to full commit SHAs and keep the released version in a trailing comment.
- Refresh lock files monthly.
- Security updates bypass the release-age check.

Pair this with the package manager's own cooldown so transitive dependencies are covered too:

- pnpm: `minimumReleaseAge: 10080` in `pnpm-workspace.yaml`
- uv: `exclude-newer = "7 days"` in `pyproject.toml`
