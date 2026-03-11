<div align="center">

# Facebook (Meta) Ads MCP Server by Coupler.io

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Transport](https://img.shields.io/badge/Transport-Streamable_HTTP-blue.svg)](#)
[![Auth](https://img.shields.io/badge/Auth-OAuth_2.0-green.svg)](#)

Coupler.io Facebook (Meta) Ads MCP server for Claude, ChatGPT, Gemini, Cursor, n8n, OpenClaw, and other MCP clients. Query and analyze Facebook (Meta) Ads data with natural language. Requires the Coupler.io account.

</div>

## Data Access

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


## Supported Clients

*Note: You will need to set up a data flow in Coupler.io with Facebook ads as a source and the AI tool of your choice as the destination.*

### Claude

Use with Claude Web, Desktop, Chat, Cowork, or Claude Code.

**Via Web/Desktop:** Go to **Customize**->**Connectors**->**Connect your tools**, search for Coupler.io and add it.

**Via Claude Code CLI:**

```bash
claude mcp add coupler-io --transport streamable-http https://mcp.coupler.io/mcp
```

### ChatGPT

Install from the **ChatGPT Apps** directory — search for "Coupler.io" in the **Apps** section of **Settings**.

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

## Links

- **Landing page:** [Facebook Ads MCP by Coupler.io](https://www.coupler.io/mcp/facebook-ads)
- **Coupler.io:** [https://coupler.io](https://coupler.io)
- **MCP Server endpoint:** `https://mcp.coupler.io/mcp`
