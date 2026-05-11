# TopoLift: Negotiation Skill (v1.2.2)

The public dialect skill for **TopoLift atom-grounded negotiation reasoning**.

The atom corpus stays on TopoLift's GPU. What this skill ships — and teaches
your agent — is the public **dialect**: the closed vocabulary in which
TopoLift speaks, plus the four ways to call the live reasoning API.

## What you get

When an MCP-aware agent loads this skill, it learns to read TopoLift's
**bilingual** API responses:

- A typed `topology` object (`regime`, `load_bearing_strategies[]`,
  `bridge_pivots[]`, `topology_signals{}`) drawn from a closed vocabulary
- Prose with inline `[Cluster_X#strategy1,strategy2]` citation tokens
  anchoring every claim to the cluster + load-bearing atoms that drove it
- A `citation_grounding` audit field verifying every citation against the
  actual retrieval set + atom strings — hallucinations are surfaced as
  issues, so your agent can branch on `.grounded` to decide whether to
  trust the prose

## Live dialect endpoint

```bash
curl https://api.topolift.ai/v1/dialect
```

No auth. No rate limit. Returns the canonical vocabulary your agent needs.

## Four install paths

### Hosted MCP endpoint (lowest friction — no install)

Point any MCP-compatible client (Claude Code, Cursor, Agents SDK) at:

```
https://mcp.topolift.ai/mcp
```

Claude Code:

```bash
claude mcp add topolift --transport http https://mcp.topolift.ai/mcp \
  --header "Authorization: Bearer tl-..."
```

### MCP via pip (fully local stdio)

```bash
pip install topolift-mcp
claude mcp add topolift-negotiation \
  -e TOPOLIFT_API_KEY=tl-... \
  -- topolift-mcp
```

### Bearer key (Stripe-provisioned)

```bash
curl -X POST https://api.topolift.ai/v1/negotiate \
  -H "Authorization: Bearer tl-..." \
  -H "Content-Type: application/json" \
  -d '{...}'
```

**$10 for 10 calls.** One-time payment via Stripe, no subscription, keys
provisioned immediately. Buy at <https://topolift.ai>.

### x402 pay-per-call (autonomous agents)

`$0.10 USDC` per call on Base mainnet. No API key. No signup. Standard x402
protocol via the Coinbase facilitator. POST without auth to get a 402
challenge with `PaymentRequirements`.

## Status of the downloadable atoms

The atom corpus remains paused for download — TopoLift evolves the atoms
continuously, and we don't want stale copies fragmenting the dialect across
agents in the wild. The reasoning is served as a managed API instead.

Pre-pause Lite bundles remain under their original Apache-2.0 license. The
dialect itself (the vocabulary published at `/v1/dialect`) is open and stable.

## Links

- **Hosted MCP**: <https://mcp.topolift.ai/mcp>
- **Site**: <https://topolift.ai>
- **API**: <https://api.topolift.ai>
- **Live dialect**: <https://api.topolift.ai/v1/dialect>
- **MCP server source**: <https://github.com/TopoLift/topolift-mcp>
- **PyPI**: <https://pypi.org/project/topolift-mcp/>
- **Official MCP registry**: <https://registry.modelcontextprotocol.io/v0/servers?search=topolift>
- **Contact**: atoms@topolift.ai

— TopoLift
