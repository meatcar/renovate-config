# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) presets.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>meatcar/renovate-config"]
}
```

`default.json`: `config:best-practices`, weekly schedule, 7-day dependency cooldown, vulnerability alerts, and `flake.lock` updates.
