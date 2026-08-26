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
- **Auto-merges anything with green CI** after a 1-day release-age floor — dev deps, Action digests, `packageManager`/`.nvmrc` pins. CI is the safety net, so only enable Renovate on a repo after it runs the shared reusable `test.yml` as its merge gate.
- Runtime dependencies (npm `dependencies`, composer `require`) wait 14 days after release instead (supply-chain cooldown).
- Automerge is set at the top level rather than per-depType: a grouped PR only auto-merges if *every* member has automerge on, so one unlisted depType (an Action, a pnpm pin) silently blocks the whole group.
- Pins GitHub Actions to commit digests.
- Also keeps `packageManager` pnpm pins, `.nvmrc`, and workflow node versions current via Renovate's default managers.
