# VodouAI/integrations

The public catalog of integration presets bundled with the [Vodou](https://vodou.ai) gateway.

Each JSON file in `presets/` describes a remote MCP server the gateway can connect to. Contributors add new integrations via pull request — **one JSON file, no code changes**.

## Contribute a preset

1. Fork this repo.
2. Copy `presets/_template.json` to `presets/<your-provider>.json` (filename must match the `id` field).
3. Fill in the fields — full schema in [`presets/_schema.json`](presets/_schema.json).
4. Validate locally:
   ```bash
   npm install --save-dev ajv ajv-formats
   node scripts/validate-presets.mjs
   ```
5. Open a PR against `main` with a one-sentence description. CI will re-run validation on every push.

See [`presets/README.md`](presets/README.md) for the full contributor guide — auth paths, schema fields, rules, and category conventions.

## How it flows into Vodou

- Each Vodou release cuts a snapshot of this repo at a pinned commit SHA.
- The gateway's `src/api/oauth-presets.ts` loader reads from a local `presets/` directory that the release build populates by cloning this repo.
- Merged presets appear in end-users' `#/integrations` page on their next gateway update.

## License

MIT. By contributing you agree your preset can be bundled and redistributed with the Vodou gateway. See [`LICENSE`](LICENSE).
