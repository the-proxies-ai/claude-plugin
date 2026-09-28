# The Proxies for Claude

Use your business’s Proxies helpers, company knowledge and authorised connections
in Claude. This plugin bundles the live MCP connection and lightweight usage guidance.

**Pre-release branch — not ready for customer installation.** The shared gateway
connection must pass security review, deploy and fresh-client testing before this
version is released or submitted. The public main branch is still version 1.0.0.

## Existing customers

The intended flow is **install → sign in → choose your workspace → connect**.
This package includes the remote MCP configuration for
`https://api.the-proxies.ai/v1/workspace`; the helpers, knowledge and business
logic remain in the live Proxies service.

On first use, verify your email and choose a shared sign-in password. Link each
workspace once using its existing workspace password. Later sign-ins show your
verified workspaces, including businesses that have different passwords. The
selected workspace stays fixed for that connection. Passwords only go into the
Proxies sign-in page, never chat.

Existing workspace-specific connections continue to work. Avoid enabling both
the old connection and the new plugin connection for the same business in a chat.
Installing the plugin does not grant workspace membership or bypass billing.
Additional simultaneous connections depend on the Claude host's support.

## New customers

[Request an initial consultation](https://the-proxies.ai/contact) to discuss your
business, scope and pricing. We configure your workspace and provide your login
and connection instructions during onboarding. An active Proxies workspace and
completed onboarding are required to use the connected workflows.

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

The plugin consists of a manifest, remote MCP configuration and text instructions. It contains no credentials,
client data, executable scripts, local server or telemetry. When you use a workflow,
Claude may send relevant tool arguments to your authorised Proxies connector and
receive workspace data. The connected service may read or write data according to
the tool, your permissions and your instructions. The Proxies service’s data
processing and retention are described in our [Privacy Policy](https://the-proxies.ai/privacy).
Claude’s own processing is governed by Anthropic’s terms and privacy policy.

## Support

Email [hello@the-proxies.ai](mailto:hello@the-proxies.ai), or use our
[contact page](https://the-proxies.ai/contact). Include the workspace name and a
brief description of the problem, but do not send passwords or access tokens.

## Installation outside the directory

After this version is released, Claude Code users can install the marketplace:

```text
/plugin marketplace add the-proxies-ai/claude-plugin
/plugin install the-proxies@the-proxies-workflows
```

Then open `/mcp` and complete OAuth for the bundled Proxies connection. Verify the
workspace in the client you are using; connections do not automatically carry
between Claude clients.

Directory submission does not imply approval or endorsement by Anthropic.
