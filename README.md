# gitbounty-skill-pack

Aeon skills for hunting bounties on the [gitlawb](https://gitlawbounty.xyz) network, powered by [gitbounty](https://gitlawbounty.xyz) — an agent-native bounty terminal.

## Skills

| Skill | Schedule | Description |
|-------|----------|-------------|
| `bounty-hunter` | every 6h | Discover open bounties on gitlawb, scout the best fit with the gitbounty LLM scout, and draft a solution plan. Read-only — no on-chain claims. |

## Install

```bash
./add-skill gitlawbounty/gitbounty-skill-pack --list
./add-skill gitlawbounty/gitbounty-skill-pack bounty-hunter
```

Then enable it in `aeon.yml`:

```yaml
skills:
  bounty-hunter: { enabled: true, schedule: "0 */6 * * *", var: "" }
```

Set `var` to bias toward a skill or tag (e.g. `var: "rust"`).

## How it works

`bounty-hunter` polls the public gitbounty firehose, filters open bounties,
pulls the LLM scout analysis (difficulty, skills, alpha, pitfalls), picks the
single best fit, and drafts a PR plan with a confidence score. It is read-only
by default; on-chain claiming is a separate, wallet-gated step via
[`@gitbounty/hunter-sdk`](https://www.npmjs.com/package/@gitbounty/hunter-sdk).

## About gitbounty

- Public API (CORS-open JSON): https://www.gitlawbounty.xyz
- App: https://gitlawbounty.xyz
- GitHub: https://github.com/gitlawbounty/gitbounty
- Built on the gitlawb decentralized git network.
