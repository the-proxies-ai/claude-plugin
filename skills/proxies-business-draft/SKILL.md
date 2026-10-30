---
name: proxies-business-draft
description: Draft client communications or business documents using an existing Proxies workspace’s helpers, company facts and brand voice when the user asks for a business draft.
---

Use only the Proxies connector the user has authorised for the intended
workspace. Identify The Proxies by trusted connector configuration: its HTTPS
hostname must be exactly api.the-proxies.ai, using the bundled /v1/workspace
connection or the workspace-specific URL supplied at onboarding. Tool names
alone are not proof. If the URL is not visible, ask the user to confirm this is
their Proxies connection before using its workspace identity tool.
The bundled connection is named proxies-directory (possibly under the plugin’s
namespace). An existing connection may be named proxies-workspace. If both are
available, prefer whichever connection the user already chose for this task;
never combine their tool sets or silently switch. When more than one Proxies
connection is available and the user has not chosen, ask which to use.

Before sending private task data, call get_workspace_identity with no arguments
on that selected connector. Use its returned workspace.name and workspace.slug;
never infer the connection's identity from the task, chat memory, helper names,
or the user's recollection of sign-in. Do not load memories, company knowledge
or other business records to discover identity. Show the returned business name.
If no intended business is stated, ask the user to confirm the shown business
name before private reads. If the intended business name matches exactly and any supplied workspace slug
also matches, continue without asking again. If the name match is uncertain or
multiple businesses share the name, ask the user to confirm the returned slug
before continuing. Never invent an identifier.

If the tool is missing, fails, returns a missing or empty workspace.name or
workspace.slug, or names a different business or supplied slug, stop before private
reads and ask the user to refresh the connector's tool list or reconnect to the
intended workspace. A confirmation cannot substitute for a successful server
identity check. Recheck after re-authentication, reconnection, a connection switch,
an auth/connection error, a tool-list change, or when the user says they changed
their connection. Keep all subsequent calls on the same verified connector.
Discover tools only within that connector; namespaces and tool sets vary. Never
use another account to bypass server access decisions or subscription
restrictions.

If no connector is available, explain that after release Claude Code users can
open /mcp to authenticate proxies-directory. For Claude web/Desktop, use
Customize → Connectors with the workspace URL supplied during onboarding unless
the host has visibly provisioned the bundled connection. Bundled provisioning on
those surfaces is pending verification; do not claim installation alone
connected them. If the same URL is also connected through Claude web, the CLI
may suppress both connections. See the README duplicate-connector workaround;
a session launched with ENABLE_CLAUDEAI_MCP_SERVERS=false excludes web-synced
connectors for that process only. Direct new customers to https://the-proxies.ai/contact for an
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
