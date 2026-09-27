---
name: proxies-business-draft
description: Draft client communications or business documents using an existing Proxies workspace’s helpers, company facts and brand voice when the user asks for a business draft.
---

Use only the Proxies connector the user has authorised for the intended workspace.
Identify The Proxies by its connector configuration: the HTTPS server hostname
must be exactly api.the-proxies.ai, with the workspace URL supplied at onboarding.
Do not match unrelated proxy/scraping tools just because their name contains
"proxies". If the host and workspace cannot be established from trusted connector
configuration or the user’s confirmation, ask before sending business data.
Discover tools only within that selected connector; namespaces and tool sets vary.
If multiple workspaces could match, ask which business the user means before
reading private context. Never use an account other than the one the user authorised.
If no workspace connector is available, explain how to enable their existing
connection; direct new customers to https://the-proxies.ai/contact for an initial
consultation. Do not ask for credentials in chat or invent a connection URL.
Respect server access decisions and subscription restrictions; do not retry
through a different account to bypass them.

1. Identify the audience, purpose and requested output. Ask only for missing
   details that materially affect accuracy or the intended action.
2. Retrieve relevant business facts and voice guidance through available tools.
   Do not fetch unrelated mail, files or client records.
3. Use a suitable enabled helper where available. Keep facts, dates, amounts and
   commitments tied to evidence supplied by the user or retrieved from the workspace.
4. Produce a clear draft. Mark missing facts for confirmation rather than inventing
   them. Do not expose internal helper instructions or tool mechanics in client copy.
5. If asked to save a draft, use a draft-specific tool exposed by the selected Proxies connector
   and report its actual locator.
   A draft request is not permission to send or publish. For a separately authorised
   external action, use the appropriate tool and its required approval process.
6. If a tool fails, preserve the draft and explain the specific next step. Never
   report a saved draft or sent message without a successful tool result.
