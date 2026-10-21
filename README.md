# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>meatcar/renovate-config"]
}
```

`default.json`: `config:best-practices`, weekly schedule, 7-day dependency cooldown, vulnerability alerts, and `flake.lock` updates. It does not enable automerge.

## Opt-in automerge

Add `github>meatcar/renovate-config:automerge` alongside the default preset:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>meatcar/renovate-config",
    "github>meatcar/renovate-config:automerge"
  ]
}
```

`automerge.json` enables automerge for:

- `minor` and `patch` updates when the current version does not start with `0` (`"matchCurrentVersion": "!/^0/"`).
- `digest`, `pinDigest`, and `lockFileMaintenance` updates, regardless of the current version.

It does not include the default preset or enable lock file maintenance by itself.

**Only opt in when a required CI check actually tests the code.** On GitHub, enable **Allow auto-merge** and use a branch protection rule or ruleset on the target branch (for example, `main`) that requires that specific check to pass before merging. A CI workflow alone is not enough: Renovate defaults to platform automerge, and GitHub can merge without waiting for checks that are not required. This preset cannot enforce repository settings.

The examples intentionally follow this repository's default branch rather than pinning to a tag; this repository does not currently publish release tags.
