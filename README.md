<div align="center">

# Facebook (Meta) Ads MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Connect Facebook and Meta Ads data to AI with the Coupler.io MCP server. Analyze campaigns, ad sets, ads, creatives, audiences, spend, leads, conversions, and performance across Facebook and Instagram using natural-language questions in ChatGPT, Claude, Gemini, Cursor, and other MCP-compatible AI tools. Requires a Coupler.io account.

[Landing page](https://www.coupler.io/mcp/facebook-ads) · [Documentation](https://docs.coupler.io/ai/mcp) · [All Coupler.io MCP integrations](https://github.com/coupler-io)

</div>

## What you can ask

- Which campaigns have the lowest cost per conversion?
- Which creatives generate the highest CTR?
- Compare campaign performance by age and gender.
- Which ads generate the most sponsored leads?
- How does performance differ between Facebook and Instagram?

## How it works

This repository documents the Facebook (Meta) Ads integration for the Coupler.io MCP server.

1. Connect Facebook (Meta) Ads to Coupler.io.
2. Select your AI tool as the destination.
3. Connect your AI client to Coupler.io MCP.
4. Ask questions about your Facebook (Meta) Ads data in natural language.

Coupler.io sits between Facebook (Meta) Ads and your AI client. It holds the Facebook (Meta) Ads credential, imports the data on a schedule, and exposes the result as a data set the AI can query. Your AI client never calls the Facebook (Meta) Ads API itself.

```
  Facebook (Meta) Ads
      |        credential held by Coupler.io
      v
  Coupler.io          import, transform, store on a schedule
      |
      v
  MCP server          schema, SQL query execution
      |
      v
  Your AI client      your question, in plain language
```

When you ask a question, the AI reads the data set's schema, writes SQL, and Coupler.io runs that query on its own side. Only the result comes back to the AI, so a large data set does not have to fit into the model's context window.

| | |
|---|---|
| **MCP endpoint** | `https://mcp.coupler.io/mcp` |
| **Transport** | Streamable HTTP |
| **Authentication** | OAuth 2.0 |
| **Query language** | SQL, executed by Coupler.io |
| **Refresh schedule** | From monthly to every 15 minutes, depending on your plan |

## Get started

*Note: You will need to set up a data flow in Coupler.io with Facebook (Meta) Ads as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install the [Coupler.io ChatGPT app](https://l.rw.rw/couplerio-chatgpt-app) and complete the authentication. You can also find it by searching for "Coupler.io" in the **Apps** section of **Settings**.

### Cursor

Find it on the [Cursor Directory](https://cursor.directory/mcp/coupler-io-official-remote-mcp).

### Gemini CLI

Go to the **AI integrations** -> **Gemini CLI** page in your Coupler.io account to copy the correct command (unique to each account). It will look like this:

```bash
gemini mcp add coupler --transport=http https://mcp.coupler.io/mcp/xxxxx
```

### OpenClaw

Use the **mcporter** skill to connect, or install the **coupler-io** skill from ClawHub.
Directly ask your OpenClaw agent to add the skill and execute it.

## Data you can access

Access seven report types — performance insights with 100+ metrics, sponsored leads, campaign/ad set/ad structure, and creative asset details.

<details>
<summary><strong>Report types</strong></summary>

| Report type | What it contains | When to use it |
|---|---|---|
| **Reports and Insights** | Performance metrics like spend, impressions, clicks, conversions, and more | Analyzing campaign performance, building dashboards, tracking ROI |
| **List of Sponsored Leads** | Lead form submissions with contact details, submission time, and source campaign/ad | Tracking lead generation, syncing leads to CRM or sales workflows |
| **List of Campaigns** | Campaign statuses, objectives, budgets, and scheduling details | Auditing campaign setup, monitoring active/paused campaigns |
| **List of Ad Sets** | Ad set statuses, optimization goals, budgets, and targeting details | Reviewing ad set efficiency and configuration |
| **List of Ads** | Individual ad statuses, bid amounts, and issue flags | Monitoring ad health and identifying problem ads |
| **List of Ad Creatives** | Creative assets (images, videos, carousels) with text, links, and media details | Reviewing all available creative assets in your account |
| **List of Ads with Ad Creatives** | Ads combined with their linked creative details | Analyzing which creatives drive the best results |

</details>

<details>
<summary><strong>Key metrics</strong></summary>

#### Performance metrics

| Name | Description |
|---|---|
| Clicks | The total number of clicks on your ad. |
| Impressions | The number of times your ad was on screen. |
| Reach | The number of people who saw your ad at least once. |
| Frequency | The average number of times each person saw your ad. |
| Quality ranking | A ranking of your ad's perceived quality vs. ads competing for the same audience. |
| Conversion rate ranking | A ranking of your ad's expected conversion rate vs. ads with the same optimization goal. |

#### Click metrics

| Name | Description |
|---|---|
| CTR | Click-through rate (clicks / impressions). |
| Unique CTR | The percentage of people who saw your ad and performed a click. |
| Unique clicks | The number of people who performed a click. |
| Inline link clicks | Clicks on links within the ad creative that led to a destination on or off Facebook. |
| Outbound clicks | Clicks that lead people off of Facebook-owned properties. |

#### Cost metrics

| Name | Description |
|---|---|
| Amount spend | Total amount spent on your campaign, ad set, or ad. |
| CPC | Cost per click (link). |
| CPM | Cost per 1,000 impressions. |
| Cost per 1000 people reached | The average cost to reach 1,000 people. |
| Purchase ROAS | Return on ad spend from purchase conversions. |
| Website purchase ROAS | Return on ad spend from website purchase conversions. |

#### Video metrics

| Name | Description |
|---|---|
| Video views | Times your video was played for a specified duration. |
| Video ThruPlay | Times your video was played to completion, or for at least 15 seconds. |
| Cost per Video ThruPlay | The average cost for each ThruPlay. |
| Plays at 25% / 50% / 75% / 100% | Times your video was played to that percentage of its length. |
| Average play time | The average duration people watched your video. |

</details>

<details>
<summary><strong>Breakdowns (dimensions)</strong></summary>

| Breakdown | What it shows |
|---|---|
| **Age** | Performance by age group. |
| **Gender** | Performance by gender. |
| **Country** | Performance by country. |
| **Region** | Performance by region. |
| **DMA** | Performance by Designated Market Area (US only). |
| **Publisher platform** | Which platform delivered your ads (Facebook, Instagram, Messenger, Audience Network). |
| **Impression device** | Performance by device type (mobile, desktop, tablet). |
| **Device platform** | The operating system of the device. |
| **Product id** | Performance by product (for catalog/dynamic ads). |
| **Frequency value** | Distribution of impressions by frequency count. |

</details>

Coupler.io imports only the report types, metrics, and breakdowns you select in the data flow. If a metric or breakdown is missing, add it to the source and re-run the flow.

## Example questions

### Performance and efficiency

- Which campaigns have the lowest cost per conversion over the last 30 days?
- Compare purchase ROAS across campaigns and flag any that fell below 1.
- How have CPM and frequency changed week over week for my top-spending ad sets?

### Creative

- Which ad creatives have the highest CTR and ThruPlay rate?
- Which videos lose the most viewers between 25% and 75% of play time?
- Which ads have a below-average quality ranking while still spending?

### Audience and placement

- Compare performance by age and gender for my lead generation campaigns.
- How does performance differ across Facebook, Instagram, and Audience Network placements?
- How many sponsored leads did each campaign generate last month, and at what cost per lead?

## Security and permissions

Your AI client never connects to Facebook (Meta) Ads directly. Coupler.io holds the Facebook (Meta) Ads credential, imports the data, and exposes only the resulting data set over MCP.

- **Your Facebook (Meta) Ads data is never modified.** Coupler.io only reads from Facebook (Meta) Ads. The AI queries the copy Coupler.io imported and cannot edit, delete, or overwrite it, let alone write anything back to your Facebook (Meta) Ads account.
- **Visibility is scoped per AI tool.** An AI client sees only the data sets from data flows that have *that client* set as a destination. Adding Claude as a destination does not expose the data flow to ChatGPT, though one flow can name both.
- **Configuration changes are possible, and confirmed first.** With the full tool set available, the AI can create data flows, add sources and destinations, change a schedule, or trigger a run. Those are real changes to your workspace, so the server instructs the AI to confirm before making one you did not ask for.
- **Nothing else is reachable.** The MCP server exposes the data sets described above and nothing more. It cannot reach your other accounts or your machine.
- **Disconnect at any time** by removing the connector in your AI client, or by deleting the credential or the data flow in Coupler.io.

Coupler.io is SOC 2 certified and compliant with GDPR and HIPAA.

## Troubleshooting

**The AI cannot find my Facebook (Meta) Ads data set.**
Usually you have not added that AI tool as a destination yet. Open the data flow in Coupler.io and add your AI client. One data flow can have several AI tools as destinations at the same time, so adding ChatGPT does not displace Claude. Each tool sees only the flows it is named on.

**The numbers look out of date.**
The AI reads the last imported snapshot, not Facebook (Meta) Ads live. Check the data flow's refresh schedule, or ask your AI client to run the data flow now.

**A field I need is missing.**
Coupler.io imports only the fields you select in the data flow's source. Add the missing fields and re-run the flow.

**The AI misreads a metric.**
Save the business context on the data set: what a metric means, which currency it is in, which rows to exclude. You do not have to leave your AI tool to do it, just tell the assistant to update the data set context and it saves it for you. The AI reads that context before it queries, so the next conversation uses your definitions instead of guessing.

**The connector does not appear in my AI client.**
Availability differs by AI client and subscription plan. Follow the client-specific steps under [Get started](#get-started), and check the [AI destination docs](https://docs.coupler.io/destinations/categories/ai) for that tool.

## Related Coupler.io MCP integrations

- [Google Ads MCP](https://github.com/coupler-io/google-ads-mcp) — compare paid search and paid social performance
- [Google Analytics 4 MCP](https://github.com/coupler-io/google-analytics-4-mcp) — analyze traffic, engagement, and conversions driven by campaigns
- [Shopify MCP](https://github.com/coupler-io/shopify-mcp) — connect advertising performance with ecommerce sales and orders
- [HubSpot MCP](https://github.com/coupler-io/hubspot-mcp) — analyze leads and deals generated by paid social campaigns

[Explore all Coupler.io MCP integrations](https://github.com/coupler-io)

## FAQ

### What is the Facebook (Meta) Ads MCP server?

It is the Facebook (Meta) Ads integration for the Coupler.io MCP server, an endpoint that lets AI clients query your Facebook (Meta) Ads data in plain language. Coupler.io imports the data, stores it, and answers the AI's SQL queries on its own infrastructure.

### Do I need a Coupler.io account?

Yes. The MCP server serves data from your Coupler.io workspace, so you need an account with a data flow that has Facebook (Meta) Ads as a source and your AI tool as a destination.

### Does this connect directly to my Facebook (Meta) Ads account?

No. Coupler.io connects to Facebook (Meta) Ads, imports the data, and exposes the resulting data set over MCP. Your AI client talks to Coupler.io, never to Facebook (Meta) Ads.

### Which Facebook (Meta) Ads data can AI access?

Whatever your data flow imports. See [Data you can access](#data-you-can-access) for the full catalog of report types and fields. The AI reaches only the data sets in flows that name your AI tool as a destination.

### Is the integration read-only?

Yes. Nothing you or your AI client does through Coupler.io changes your Facebook (Meta) Ads data. Coupler.io only reads from Facebook (Meta) Ads, and the AI only queries the copy Coupler.io imported. It cannot edit, delete, or write anything back to your Facebook (Meta) Ads account.

### Which AI assistants can I use?

Claude, ChatGPT, Cursor, Gemini CLI, OpenClaw, Perplexity, and any client that speaks MCP through the Custom MCP destination. Setup steps for the clients above are under [Get started](#get-started); for the rest, see the [AI destination docs](https://docs.coupler.io/destinations/categories/ai).

### Do I need to write SQL or code?

No. You ask in plain language; the AI writes the SQL and Coupler.io runs it. Writing SQL yourself stays an option if you want a specific transformation.

### How fresh is the data?

As fresh as the last data flow run. Schedules range from monthly to every 15 minutes depending on your plan, and you can ask your AI client to refresh the flow on demand.

## Links

- **Landing page:** [Facebook (Meta) Ads MCP by Coupler.io](https://www.coupler.io/mcp/facebook-ads)
- **Documentation:** [Coupler.io MCP](https://docs.coupler.io/ai/mcp)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`
- **All Coupler.io MCP integrations:** [https://github.com/coupler-io](https://github.com/coupler-io)
