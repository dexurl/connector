# DexURL for Claude

This plugin connects Claude to your DexURL account and adds one skill, `campaign-links`.

## What it does

- **The connector.** It adds the DexURL connector at `https://dexurl.com/mcp`. Claude can then find, create,
  edit, pause and delete your short links, search your Vault and save links to it, and see your Bio pages and
  add links to one. Click stats and several link rules (passwords, one-time links, smart routing,
  availability windows, multi-destination boards) need the Pro plan. The same Free and Pro limits apply as
  in the app, and there is no extra charge for the connector.
- **The `campaign-links` skill.** Give Claude a campaign and a list of channels. It creates one short link
  per channel, shows them in a table with their QR addresses, and later summarizes the clicks per channel. It
  asks before deleting or repointing any link, and it passes on any plan message DexURL returns.

It cannot see private Vault items, publish a Bio page, or touch billing or account settings.

## Install

Add this marketplace and install the plugin from a shell:

```bash
claude plugin marketplace add dexurl/connector
claude plugin install dexurl@dexurl-plugins
```

The first time Claude uses a DexURL tool, sign in to DexURL (Google or an email link) and choose Allow on
the consent screen.

You can also add the connector without the plugin. See https://dexurl.com/connect.

## Disconnect

Remove the connector in Claude's connector settings. A disconnected assistant can keep access for up to 24
hours, until its sign-in token expires.

## Links

- Documentation: https://dexurl.com/connect
- Support: https://dexurl.com/support
- Privacy policy: https://dexurl.com/legal/privacy

Licensed under the MIT License. See `LICENSE`.
