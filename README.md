# Stipple Agent Skills

**Outcome-focused agent skills for document trust, verification, and evidence workflows.**

Each skill solves a problem end-to-end — verify a document, fact-check a report, screen a counterparty — using the [Stipple API](https://www.stipple.sh) as infrastructure. Skills work with Claude Code, Codex, Cursor, Gemini CLI, and any agent that reads SKILL.md files.

**Free anonymous tier** — every skill runs without an API key or signup. Get a free key at [stipple.sh](https://www.stipple.sh) for your own metering.

## Skills

| Skill | What it does | Stipple endpoint |
|---|---|---|
| [verify-citations](skills/verify-citations/) | Verify a report's citations resolve and support claims; flag unsupported claims; recompute arithmetic | `/v1/verify-references` |
| [verify-document](skills/verify-document/) | Forensic authenticity check: risk band + per-signal evidence for PDFs/images | `/v1/warrants` |
| [find-matching-tenders](skills/find-matching-tenders/) | Search open AU/NZ government tenders, rank against your company, gap analysis | `/v1/tenders`, `/v1/tenders/match` |
| [detect-ai-text](skills/detect-ai-text/) | AI-written-prose probability with linguistic tells; abstains on non-prose | `/v1/detect-ai-text` |
| [extract-document-data](skills/extract-document-data/) | Grounded structured extraction: values cite their page, missing values abstain | `/v1/extract` |
| [check-identity-pack](skills/check-identity-pack/) | AFP 100-point / AUSTRAC identity check with exactly-what's-missing output | `/v1/identity-check` |
| [screen-adverse-media](skills/screen-adverse-media/) | Corroboration-gated adverse media / PEP / sanctions screening | `/v1/adverse-media` |

## Connecting the MCP server

All skills also work through the hosted MCP server in any MCP client:

```json
{ "mcpServers": { "stipple": { "url": "https://www.stipple.sh/mcp" } } }
```

## REST quick reference

Base URL: `https://www.stipple.sh` · [OpenAPI spec](https://www.stipple.sh/openapi.json) · [API docs for agents](https://www.stipple.sh/agents.md)

Document endpoints take multipart file uploads (or `bytes_b64` form field). Options like `scheme`, `deep`, `fresh` are query parameters. Anonymous callers share a free weekly allowance per IP; free API keys get their own metering.

## Open-source integrations

The same verification layer is already wired into popular open-source tools — see [stipple-kits](https://github.com/Sketchjar/stipple-kits) for ready-made integrations:

| Project | Integration |
|---|---|
| magicrew/doc7 | Trust gate before document→Markdown conversion |
| ucbepic/docetl | `stipple_verify` ETL operator |
| datalab-to/lift | `--verify` flag on extraction CLI |
| feyninc/chonkie | `TrustChef` pre-chunking wrapper |
| CatchTheTornado/text-extract-api | Verification in OCR pipeline |
| shibing624/ChatPDF | Corpus-level trust metadata |

## License

Apache-2.0

---

*Built on the [Stipple API](https://www.stipple.sh) — the same verification layer is available as a hosted [MCP server](https://github.com/Sketchjar/stipple-mcp).*
