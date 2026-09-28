---
name: proxies-business-draft
description: Draft client communications or business documents using an existing Proxies workspace’s helpers, company facts and brand voice when the user asks for a business draft.
---

Use only the Proxies connector the user has authorised for the intended
workspace. Identify The Proxies by trusted connector configuration: its HTTPS
hostname must be exactly api.the-proxies.ai, using the bundled /v1/workspace
connection or the workspace-specific URL supplied at onboarding. Tool names
alone are not proof. If the URL is not visible, ask the user to confirm this is
their Proxies connection before relying on its workspace identity instructions. The bundled
connection is named proxies-directory (possibly under the plugin’s namespace).
An existing connection may be named proxies-workspace. If both are available,
prefer whichever connection the user already chose for this task; never combine
their tool sets or silently switch. When more than one Proxies connection is
available and the user has not chosen, ask which to use.

Before sending private task data, establish identity from the selected MCP
connection’s own workspace identity metadata/instructions. If these do not name
the workspace, stop and ask the user to check the workspace selected at sign-in.
Do not invent an identity tool: list_helpers and get_my_context are not identity
lookups. Do not load
memories, company knowledge or other records just to discover identity. Show the
returned business name and any returned workspace identifier to the user. If
they have not named the intended business, ask them to confirm the displayed
business before sending private task data. If the name could match multiple
workspaces, ask them to check which workspace they selected at sign-in. The shared URL does not identify the
workspace: OAuth selection does. If identity cannot be established or differs
from the intended business, stop and ask the user to check their connection.
Retrieve no business records until the intended workspace is established. Repeat
the identity check and confirmation after re-authentication, reconnection or a
connection switch. Also recheck after an auth/connection error, tool-list change,
or when the user says they changed their connection. If the identity instructions
have not visibly refreshed, ask them to confirm their sign-in workspace selection.
Discover tools only within that connector; namespaces and
tool sets vary. Never use another account to bypass server access decisions or
subscription restrictions.

If no connector is available, explain that after release Claude Code users can
open /mcp to authenticate proxies-directory. For Claude web/Desktop, use
Customize → Connectors with the workspace URL supplied during onboarding unless
the host has visibly provisioned the bundled connection. Bundled provisioning on
those surfaces is pending verification; do not claim installation alone
connected them. Direct new customers to https://the-proxies.ai/contact for an
initial consultation. Do not ask for credentials in chat or invent a workspace
URL.

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
