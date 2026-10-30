# The Proxies for Claude

Use your business’s Proxies helpers, company knowledge and authorised
connections in Claude. This prerelease bundles a remote MCP connection and
lightweight usage guidance. The shared gateway is live; end-to-end installation
and sign-in testing for this package is still in progress.

**Pre-release branch — not ready for customer installation.** The shared gateway
connection must pass fresh-client testing before this version is released.
Directory policy eligibility is a separate unresolved gate; successful connection
testing does not establish directory approval. Keep this change in its draft PR
until the release gates pass. Merging the manifest to the tracked branch makes
it available to users.

## Existing customers

The intended flow is **install → sign in → connect your workspace**. An onboarding
update is deployed to connect a sole linked workspace automatically when
there are no additional memberships to link. People with multiple eligible
workspaces retain a chooser. Component tests and the deployed web bundle are
verified; live authenticated proof of the automatic branch remains pending.
This package includes the remote MCP configuration for
`https://api.the-proxies.ai/v1/workspace`;
the helpers, knowledge and business logic remain in
the live Proxies service.

Planned sign-in behaviour, pending live verification: on first use, verify your
email and choose a personal Proxies sign-in password (do not share it). Link
each workspace using the existing password for your own active member account
with that same email address. The planned authorisation requires both the
matching email and that member’s password. Later sign-ins will show verified
workspaces, including businesses with different member passwords. The selected
workspace is intended to stay fixed for that connection. Enter passwords only on
the Proxies sign-in page, never in chat.

Existing workspace-specific connections continue to work. The bundled server is
named `proxies-directory`, distinct from legacy `proxies-workspace`. Use one
connection for a task. In Claude Code, open `/mcp`, select the unused connection
and disable it using the available connection controls. In web/Desktop, manage
unused connections through Customize → Connectors. Check the business name
before using tools; two connections can be authorised for different workspaces.
Installing the plugin does not grant workspace membership or bypass billing.
Additional simultaneous connections depend on the Claude host's support.

## New customers

[Request an initial consultation](https://the-proxies.ai/contact) to discuss
your business, scope and pricing. We configure your workspace and provide your
login and connection instructions during onboarding. An active Proxies workspace
and completed onboarding are required to use the connected workflows.

## Included workflows

- **Proxies workspace:** identify the connected workspace and find a suitable helper.
- **Company knowledge:** retrieve relevant company information with source references
  where available and clearly identify gaps.
- **Business draft:** prepare communications and documents using available business
  context, with drafts kept for review unless you explicitly request an action.

The skills use only tools available on your connected Proxies workspace. They do
not install software, run scripts, connect external accounts automatically or
schedule background work. Feature availability varies between Claude products;
the plugin requires a surface that supports skills and your remote connector.

## Data and privacy

The plugin consists of a manifest, remote MCP configuration and text
instructions. It contains no credentials, client data, executable scripts, local
server or telemetry. When you use a workflow, Claude may send relevant tool
arguments to your authorised Proxies connector and receive workspace data. The
connected service may read or write data according to the tool, your permissions
and your instructions. The Proxies service’s data processing and retention are
described in our [Privacy Policy](https://the-proxies.ai/privacy). Claude’s own
processing is governed by Anthropic’s terms and privacy policy.

## Support

Email [hello@the-proxies.ai](mailto:hello@the-proxies.ai), or use our [contact
page](https://the-proxies.ai/contact). Include the workspace name and a brief
description of the problem, but do not send passwords or access tokens.

## Installation outside the directory

After this version is released, Claude Code users can install the marketplace:

```text
/plugin marketplace add the-proxies-ai/claude-plugin
/plugin install the-proxies@the-proxies-workflows
```

Then open `/mcp` and complete OAuth for `proxies-directory` (which may appear
under the plugin namespace). Verify the workspace in the client you are using;
connections do not automatically carry between Claude clients.

### Installation verification

On 30 October 2026, Claude Code installed this prerelease from a local marketplace
into an isolated configuration. Its inventory found all three skills and the
bundled `proxies-directory` HTTP server. The server health check reached the
shared endpoint and correctly reported that authentication was needed. This
proves local packaging and server discovery. A separate isolated installation
from the GitHub feature branch also succeeded. Its real OAuth attempt was rejected
before sign-in because the gateway did not accept Claude Code’s dynamic localhost
callback port. The fix is tracked in platform PR #1778 and must be deployed and
retested before authenticated use of this installed package is claimed.

### Existing connections and other Claude surfaces

Bundled MCP provisioning in Claude web/Desktop has not yet been verified for
this release. A manual custom connection in Claude web was verified on
30 October 2026: email verification, membership linking, workspace selection,
OAuth callback and a read-only fictional-workspace helper call all succeeded.
This does not establish bundled plugin installation or directory approval.
If the host does not create the connection, open Customize →
Connectors and add the workspace URL provided at onboarding, then complete
sign-in. Installing skills alone does not establish a connection.
In Claude Code, a workspace-specific connection can instead be added with:

```text
claude mcp add --transport http --scope user proxies-workspace YOUR_WORKSPACE_URL
```

Replace the placeholder only with your actual onboarding URL. Do not enable this
alongside the bundled connection for the same task. Existing customers can keep
their current working connection throughout the prerelease.

Directory submission does not imply approval or endorsement by Anthropic.

## Release checklist

Before merging, verify the gateway and each advertised Claude surface. Update
all prerelease and pending-verification wording in this README and all three
skills to match observed results; do not describe an untested surface as
supported.

Verify that each advertised Claude surface supplies the server’s workspace identity
instructions to the model. If not, the skills ask the user to confirm the business
they selected at sign-in before continuing with their task.
In the 30 October Claude web test, the model reported that the server identity
instructions were unavailable. Expect the plugin's sign-in-workspace confirmation
fallback on that surface; installation alone does not prove workspace identity.
A future gateway enhancement may include the workspace slug in those instructions
to distinguish businesses with identical names.
