<p align="center">
  <img src="assets/dexurl-icon.svg" alt="DexURL" width="72" height="72">
</p>

# DexURL connector

Use [DexURL](https://dexurl.com) from your AI assistant: create, find, edit and pause short links and QR
codes, save links to your Vault, and add links to your Bio page, in plain words.

The connector lives at one address:

```
https://dexurl.com/mcp
```

You sign in to DexURL the usual way (Google or an email link) and approve a consent screen. There is no API
key. The same Free and Pro limits apply as in the app, and there is no extra charge for the connector.

Full guide: **[dexurl.com/connect](https://dexurl.com/connect)**

## Add it to Claude

DexURL is in Claude's connector directory: [claude.ai/directory/dexurl](https://claude.ai/directory/dexurl).
In Claude, open Settings, then Customize, then Connectors, search for DexURL and connect it. Sign in to
DexURL and choose Allow.

To add it by address instead, choose Add in Connectors, then Add custom connector, name it DexURL, and enter
`https://dexurl.com/mcp`.

Add it on the web or in the desktop app; it is then available in the Claude mobile app as well.

## Claude Code

Add the connector on its own:

```bash
claude mcp add --transport http dexurl https://dexurl.com/mcp
```

Or install the plugin in this repository, which adds the connector and a `campaign-links` skill:

```bash
claude plugin marketplace add dexurl/connector
```

```bash
claude plugin install dexurl@dexurl-plugins
```

See [`claude-plugin/`](claude-plugin/) for what the plugin contains.

## What an assistant can do

| Area | What you can ask for | Plan |
|---|---|---|
| Account | See your plan and its limits | Free and Pro |
| Short links | Find, read, create, edit, pause and delete short links, with click caps and expiry | Free and Pro |
| Link rules | Passwords, one-time links, smart routing, availability windows, multi-destination boards | Pro |
| Click stats | Click totals for one link or all of them | Pro |
| Vault | Search your Vault and save links to it | Free and Pro |
| Bio pages | See your Bio pages and add links to one | Free and Pro |

## What it cannot do

- See or change private Vault items.
- Publish a Bio page. Links added to a published page wait in its draft until you publish them in the app.
- Touch billing, account settings or custom domains.
- Go past your plan's limits.

## Good to know

- A change to a link can take up to a minute to reach visitors.
- Deleting a link stops its printed QR codes working, and an assistant cannot undo a delete.
- To disconnect, remove the connector in your assistant's connector settings. A disconnected assistant can
  keep access for up to 24 hours, until its sign-in token expires.

## Help

- Guide: [dexurl.com/connect](https://dexurl.com/connect)
- Documentation: [dexurl.com/docs/ai-connector](https://dexurl.com/docs/ai-connector)
- Support: [dexurl.com/support](https://dexurl.com/support)
- Privacy: [dexurl.com/legal/privacy](https://dexurl.com/legal/privacy)

The files in this repository are released under the MIT License. See [`LICENSE`](LICENSE).
