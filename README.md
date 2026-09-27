# The Proxies for Claude

Use your business’s Proxies helpers, company knowledge and authorised connections
in Claude. This plugin supplies three workflow skills for your existing workspace.

## Existing customers

1. Install **The Proxies** plugin using the
   [installation instructions below](#installation-outside-the-directory)
   (Claude Code only until the directory listing is approved).
2. Enable your existing Proxies workspace connector in Claude. If you have not
   connected it yet, add the exact workspace URL provided during onboarding under
   **Customize → Connectors**, then sign in through the Proxies login page.
3. Ask “Which Proxies helpers can help me today?”, “Find our procedure for this”,
   or “Draft a client update using our company voice”.

Keep the workspace connector you already use. This plugin does not add a second
connector or change your account. Each business has its own connection URL;
contact support if you cannot find yours. Never enter your password into chat.
If Claude cannot see which service a connector belongs to, it may ask you to
confirm the Proxies workspace before using business information.

Your workspace membership, enabled helpers, subscription state and connected
services determine what is available. Installing this plugin does not grant
additional permissions or create a Proxies account.

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

The plugin consists of a manifest and text instructions. It contains no credentials,
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

Until a directory listing is approved, Claude Code users can add this repository
as a plugin marketplace and install `the-proxies@the-proxies-workflows`.
Connect your workspace in the Claude client where you use the plugin.
For Claude Code, first check `/mcp`; do not add a duplicate if your workspace
connector is already available. Otherwise use the exact HTTPS workspace URL
supplied at onboarding:

```sh
claude mcp add --transport http --scope user proxies-workspace YOUR_WORKSPACE_URL
```

Replace `YOUR_WORKSPACE_URL` with your provided URL; it is not a password or API
key. Each URL is specific to your business; do not reuse another organisation’s.
In Claude Code, open `/mcp` and complete the Proxies OAuth sign-in if prompted.
Connecting a service in one Claude client does not guarantee it is connected in
every other client; verify its state in the client you are using.

```text
/plugin marketplace add the-proxies-ai/claude-plugin
/plugin install the-proxies@the-proxies-workflows
```

Directory submission does not imply approval or endorsement by Anthropic.
