---
name: campaign-links
description: Creates one DexURL short link per marketing channel for a campaign and reports them as a table with their QR addresses, then later summarizes clicks per channel. Use when the user gives a campaign and a list of channels (for example email, Instagram, flyer, newsletter) and wants trackable links, or asks how a campaign's links are doing.
---

# Campaign links

Use the DexURL connector tools to give each channel of a campaign its own short link, so the clicks can be
told apart later. The tools are `get_account`, `find_links`, `get_link`, `get_stats`, `create_link`,
`update_link` and `delete_link`. If the DexURL connector is not connected, say so and point the user to
https://dexurl.com/connect.

## Before creating anything

1. Collect three things. Ask for whatever is missing, in one message:
   - the campaign name (short, for example `spring-sale`),
   - the destination address the links should lead to,
   - the channels, one per link.
2. Call `get_account` to learn the plan. A Free account holds a limited number of active short links. If the
   channel list would go past the limit, tell the user how many links fit and ask which channels to do first.
3. Ask once whether to add tracking parameters to each destination (`utm_source=<channel>` and
   `utm_campaign=<campaign>`). Do it only if the user says yes.

## Creating the links

For each channel, call `create_link` with:

- `destinationUrl`: the destination, with the tracking parameters if the user wanted them,
- `title`: `<campaign> - <channel>`, so the links are easy to find in DexURL later,
- any expiry (`expiresInMinutes`) or click cap (`maxClicks`) the user asked for, and nothing else.

Create the links one at a time. Do not set passwords, one-time use, routing or a readable address unless the
user asked for them. If a request returns a message saying a feature needs the Pro plan, show that message
exactly as it came back, skip the feature, and carry on with the plain link if the user agrees.

Then answer with a table, one row per channel:

| Channel | Short link | QR address | Manage in DexURL |
|---|---|---|---|

Use `shortUrl`, `qrUrl` and `manageUrl` from each result. The QR address is the address to put in a QR
code generator or in DexURL's QR studio; say so in one sentence under the table.

## Reporting clicks later

When the user asks how the campaign is doing:

1. Call `find_links` with the campaign name as `query` to list its links.
2. Call `get_link` for each one and read its `clicks` total. This works on every plan.
3. If the account is on Pro, `get_stats` with a link's `slug` and a number of `days` adds daily totals. If it
   returns a message that stats need Pro, pass that message on and report the totals from step 2 instead.
4. Answer with a table of channel and clicks, the best channel first, and one sentence on what stands out.
   Report only numbers the tools returned.

## Rules to follow

- Ask before deleting a link and before pointing an existing link at a new destination. Name the exact links
  and what will change, and wait for a clear yes. A delete stops that link's printed QR codes working and
  cannot be undone from here. A change can take up to a minute to reach visitors.
- Never delete or repoint several links at once on one general instruction. Confirm the list first.
- Respect plan messages. When DexURL says a limit or feature belongs to a plan, repeat what it said and do not
  try another route around it.
- Do not guess slugs or link addresses. Take them from tool results.
- You cannot see private Vault items, publish a Bio page, or change billing or account settings. Say so if
  asked, and do not look for a way around it.
