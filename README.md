# oriz-ai-providers-data

Provider / model / rate-limit / priority data for [`@chirag127/oriz-ai-providers`](https://github.com/chirag127/oriz-ai-providers-npm-pkg).

## Purpose

The LLM API landscape shifts monthly. This repo decouples that churn from package releases — the npm package fetches the latest tagged release of this repo at runtime (cached 24h).

## Files

| File | Schema |
|---|---|
| `providers.json` | `Array<{ slug, name, country, baseUrl, signupUrl, requiresKey, requiresPhoneVerification, requiresCard, dataUsedForTraining }>` |
| `models.json` | `Array<{ slug, provider, contextWindow, maxOutput, modality, rateLimit: { rpm, rpd, tpd }, family }>` |
| `priority.json` | `{ default, highVolume, reasoning, vision, code }` — each an ordered array of provider slugs |
| `env-vars.json` | `{ providerSlug: ENV_VAR_NAME }` mapping |

## Contributing

1. Open a PR with JSON edits
2. CI validates JSON syntax + cross-refs (model `provider` must exist in `providers.json`)
3. Merge to `main` → release workflow tags a new release
4. The npm package picks up the new release on next 24h cache expiry

## Source attribution

Data sourced from:
- [awesome-free-llm-apis](https://github.com/mnfst/awesome-free-llm-apis)
- [free-llm-api-resources](https://github.com/cheahjs/free-llm-api-resources)
- Each provider's own documentation (see `signupUrl` per provider)

## License

CC0-1.0. Public domain. Use it however you like.
