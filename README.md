# The Proxies for Claude

Use your business’s Proxies helpers, company knowledge and authorised
connections in Claude. This prerelease bundles a remote MCP connection and
lightweight usage guidance. The shared gateway is live; end-to-end installation
and sign-in testing for this package is still in progress.

**Pre-release branch — not ready for customer installation.** The shared gateway
connection must pass fresh-client testing before this version is released.
Directory policy eligibility is a separate unresolved gate; successful connection
testing does not establish directory approval. Keep this change in its draft PR
until the release gates pass. The marketplace entry is pinned to the released
1.0.0 commit (`a15ef7782cfa8cbb01b45259703d4862649f4bc1`), so merging
this beta does not move marketplace users onto its bundled connection. Advancing
that pin requires a separate reviewed release change after acceptance, including
updating the temporary testing wording in the marketplace metadata.

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

The manual web sign-in flow was verified: on first use, verify your
email and choose a personal Proxies sign-in password (do not share it). Link
each workspace using the existing password for your own active member account
with that same email address. Authorisation requires both the
matching email and that member’s password. Later sign-ins will show verified
workspaces, including businesses with different member passwords. The selected
workspace is intended to stay fixed for that connection. Enter passwords only on
the Proxies sign-in page, never in chat.

Existing workspace-specific connections keep their existing tools and access.
These revised beta skills require `get_workspace_identity` on either a legacy or
bundled connection and stop if that identity check is unavailable or fails. The gateway tool is deployed. The bundled server is
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

## Newly added company knowledge

If your first knowledge upload succeeds but Claude cannot find the company
knowledge search tool, refresh the selected connector's tools in Claude web:
**Customize → Connectors → Yours → your Proxies connection → More options →
Refresh tools list**. Then return to the chat and retry the question. Starting
a new chat alone did not refresh the cached catalogue in our 30 October 2026
test. Keep the same authorised connection; no disconnect or password reset was
needed. Verify the answer cites the document you uploaded before treating the
upload as complete.

This recovery and a sourced search of a fictional Acacia document were verified
with a manual Claude web custom connector. Other hosts and bundled provisioning
remain subject to the release checks below.

## Support

Email [hello@the-proxies.ai](mailto:hello@the-proxies.ai), or use our [contact
page](https://the-proxies.ai/contact). Include the workspace name and a brief
description of the problem, but do not send passwords or access tokens.

## Installation outside the directory

The marketplace currently installs the pinned 1.0.0 skills-only release. After
acceptance and a reviewed update to the release pin, these same commands will
install the bundled-connection version:

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
callback port. A gateway update is now deployed. The subsequent installed-plugin OAuth
completed successfully, and a separate Claude Code MCP health check reported
Connected. A model-issued list_helpers call through the installed package also
passed with the session-only duplicate-connector workaround below; server
instructions identified the selected fictional Acacia workspace.

### Claude Code with the same connection already in Claude web

In Claude Code 2.1.314, the installed plugin and a web-synced connector using the
same URL suppressed each other in our test: the health check passed, but model
sessions had no plugin tools. For an isolated plugin session, Anthropic documents:

```sh
ENABLE_CLAUDEAI_MCP_SERVERS=false claude
```

This excludes web-synced connectors from that process, including any other web
connections you normally use there. It does not disconnect them in Claude web or
change their authorisation. The installed Proxies plugin then successfully listed
Acacia's helpers and supplied its workspace identity. Do not treat this workaround
as proof that the default duplicate-connection case works. See the
[Claude Code connector controls](https://code.claude.com/docs/en/mcp#disable-claude-ai-connectors).

### Prerelease testing in Claude web

The tested route is **Customize → Plugins → Add plugin → Upload plugin**, using
an archive of this exact prerelease commit. For further CLI beta tests, use
`claude --plugin-dir /absolute/path/to/this/checkout` in the isolated test profile;
the marketplace intentionally installs the stable version, even from this branch.
Do not advance the marketplace pin merely to run a beta test. In the 30 October test, importing the
GitHub marketplace URL with a branch fragment displayed the older main-branch
version 1.0.0 with skills only. Do not rely on that URL syntax to select this beta
in Claude web. Verify version **1.1.0-beta.2**, **three skills** and **one connector**
after upload. This remains an acceptance-test procedure, not a customer release.

### Existing connections and other Claude surfaces

Claude web ZIP installation was verified for version 1.1.0-beta.1: three skills
and one bundled connector. Claude reused an existing authenticated test connection
for the shared URL. All three installed skills loaded and completed read-only
fictional workspace, knowledge and drafting checks. Fresh bundled OAuth and
Desktop installation remain unverified. A manual custom connection in Claude web was verified on
30 October 2026: email verification, membership linking, workspace selection,
OAuth callback and a read-only fictional-workspace helper call all succeeded.
This manual connection test does not establish fresh bundled OAuth or directory approval.
If the host does not create the connection, open Customize →
Connectors and add the workspace URL provided at onboarding, then complete
sign-in. Installing skills alone does not establish a connection.
In Claude Code, a workspace-specific connection can instead be added with:

```text
claude mcp add --transport http --scope user proxies-workspace YOUR_WORKSPACE_URL
```

Replace the placeholder only with your actual onboarding URL. Do not enable this
alongside the bundled connection for the same task. Existing customers can keep
their current working connection throughout the prerelease; the revised beta
skills themselves still require the new identity tool.

Directory submission does not imply approval or endorsement by Anthropic.

## Release checklist

Before merging, verify the gateway and each advertised Claude surface. Update
all prerelease and pending-verification wording in this README and all three
skills to match observed results; do not describe an untested surface as
supported.

The beta skills require a successful `get_workspace_identity` call on the selected
connector before private reads. This gateway enhancement is deployed. Missing or failed identity checks stop the workflow;
user recollection of sign-in is no longer a fallback. Legacy and modern registration parity passed SDK tests. Actual web and CLI beta.2
checks verified Acacia’s returned name and slug before helper listing. The CLI
also refused a Beacon request on the Acacia connection before listing helpers.
The production modern-era flag was not enabled; no live modern rollout is claimed. Older knowledge and drafting receipts above cover the previous skill text;
those workflows still need beta.2 acceptance.

Release gate: the same-URL web-synced plus installed CLI connection must work without a workaround, or be explicitly documented as unsupported in the release. The current default combination is unsupported; only the session-only workaround above has passed.

No Claude host is yet confirmed to consume the manifest privacyPolicyUrl field.
The visible README Privacy Policy link remains the documented privacy reference.
Verify host handling before claiming manifest-level support.
