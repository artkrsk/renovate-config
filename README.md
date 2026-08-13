# renovate-config

Shared Renovate preset for artkrsk repos. Consume with a 3-line `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>artkrsk/renovate-config"]
}
```

What it does:

- Weekly grouped non-major updates (Monday morning), dashboard off.
- **Auto-merges dev dependencies** (npm `devDependencies`, composer `require-dev`) when CI is green — CI is the safety net, so only enable Renovate on a repo after it runs the shared reusable `test.yml` as its merge gate.
- Runtime dependencies wait 14 days after release before auto-merging (supply-chain cooldown).
- Pins GitHub Actions to commit digests.
- Also keeps `packageManager` pnpm pins, `.nvmrc`, and workflow node versions current via Renovate's default managers.
