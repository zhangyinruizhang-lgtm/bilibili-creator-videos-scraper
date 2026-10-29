Extract all historical uploaded videos (`user_videos`) with complete 7-metric engagement stats (`views`, `likesCount`, `coinsCount`, `favoritesCount`, `sharesCount`, `danmakuCount`, `commentsCount`) and KOL account profiles (`user_profile`) from any **Bilibili UP creator (哔哩哔哩 UP主 / space.bilibili.com)** — **with 100% no login, no cookies, and zero `-352` risk-control blocks**.

Built for **KOL & influencer marketing agencies, brand sponsorship due diligence, competitor channel monitoring, and AI/LLM creator analytics** (n8n, Make, Dify, Claude MCP). Users on the **Apify Free plan ($5 monthly credit) can extract up to 1,111 Bilibili creator videos or profiles per month for free**.

---

## What Can This Bilibili Creator Scraper Do? (Features)

| Bilibili Creator & KOL Capability | Built-In Advantage |
| :--- | :--- |
| **3-Stage Anti-`-352` Creator Video Engine (`user_videos`)** | Bypasses Bilibili space risk-control blocks without login cookies using archive series endpoints, WebGL-fingerprinted WBI space queries, and exact-MID search verification. |
| **Complete 7-Metric Video Enrichment** | Automatically enriches every uploaded video via `/x/web-interface/view` so you get real `views`, `likesCount`, `coinsCount` (投币), `favoritesCount` (收藏), `sharesCount`, `danmakuCount`, and `commentsCount`—never empty `0`s. |
| **Exclusive KOL Sponsorship Vetting KPIs** | Automatically computes **`coinPerViewRatio`** (real user coin endorsement per view) and **`engagementRate`** (triple-combo interaction rate) to spot fake traffic vs. high-converting creators. |
| **Full UP Creator Profile Card (`user_profile`)** | Extracts `followersCount`, `followingCount`, total uploaded videos (`videosCount`), cumulative channel likes (`likesCount`), account level (`LV0–LV6`), VIP status, and official verification title (`officialVerify`). |
| **Free Inline Danmaku & Cascade Comments** | Optionally attach each video's `peakMinute` and `danmakuSamples` for free (`scrapeDanmaku`), or cascade-extract top reader comments (`scrapeComments`). |
| **256 MB RAM Real-Time Streaming** | Streams records into your Apify Dataset in real-time batches of 10 rows on just **256 MB RAM**, supporting scheduled runs (`deltaMode`) and **JSON, CSV, Excel, or Parquet** exports. |

---

## How to Scrape Bilibili Creators & UP Channels in 3 Easy Steps

1. **Select a Creator `mode`** — Choose **`user_videos`** (to extract a creator's uploaded video list and full stats) or **`user_profile`** (to extract follower, total like, and verification metrics).
2. **Paste Creator MIDs or URLs (`userIds`)** — Enter one or more numeric MIDs (e.g., `946974` for MediaStorm 影视飓风) or full space URLs (`https://space.bilibili.com/946974`).
3. **Click "Start"** — Download your KOL analysis dataset in **JSON, CSV, Excel, or Parquet**, or connect via REST API, n8n, Make, or Claude MCP.

---

## Bilibili Creator Scraper Use Cases

| Buyer Profile | Bilibili KOL & Channel Intelligence Use Case |
| :--- | :--- |
| **Influencer & KOL Marketing Agencies** | Vet Bilibili UP creators before sponsorship deals by auditing their recent 50 videos' `coinPerViewRatio`, `engagementRate`, and `followersCount` |
| **Competitive Intelligence & Brand Teams** | Track official competitor Bilibili channels (`官方号`) to monitor product launch videos, upload frequency, and viewer reception |
| **MCNs & Talent Scouts** | Discover fast-growing gaming, tech, ACG, and lifestyle creators and benchmark their coin-to-view conversion rates |
| **Hedge Funds & Equity Analysts** | Monitor upload cadence and viewership momentum across official brand and CEO channels in China |

---

## Input

All parameters are configured in the **Input** tab. Below is the complete input parameter reference table matching the schema and JSON input examples:

| Input Field | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| **`mode`** | `string` | `"user_videos"` | `"user_videos"` (extract creator's uploaded videos with full 7-metric stats) or `"user_profile"` (extract creator follower & verification card). |
| **`userIds`** | `array` | `["946974"]` | Target Bilibili creator numeric MIDs (`"946974"`) or space URLs (`"https://space.bilibili.com/946974"`). Duplicate MIDs are automatically deduplicated. |
| **`maxResults`** | `integer` | `30` | Maximum number of primary video or profile records to return (`1` to `10,000`). |
| **`dateStart` / `dateEnd`** | `string` | `""` | Optional `YYYY-MM-DD` publication date filter for `user_videos`. Videos outside this range are skipped and unbilled. |
| **`scrapeDanmaku`** | `boolean` | `false` | Inline enrichment: attaches `peakMinute` and representative `danmakuSamples` directly onto each creator video row at zero extra row cost. |
| **`scrapeComments`** | `boolean` | `false` | Cascade add-on: extracts top `maxCommentsPerVideo` comments under each creator video (billed as 1 item per comment row). |
| **`maxCommentsPerVideo`** | `integer` | `10` | Maximum comments to extract per video when `scrapeComments` is enabled (`1` to `200`). |
| **`deltaMode`** | `boolean` | `false` | Remembers scraped `bvid` values across scheduled runs so you only pay when a creator uploads a brand-new video. |

### 1. Extract Creator Uploaded Videos + Full 7-Metric Stats (JSON)
```json
{
  "mode": "user_videos",
  "userIds": [
    "946974",
    "https://space.bilibili.com/642389251"
  ],
  "dateStart": "2026-01-01",
  "maxResults": 30,
  "scrapeDanmaku": true,
  "scrapeComments": false,
  "deltaMode": false
}
```

### 2. Batch Vet KOL Account Profiles & Follower Counts (JSON)
```json
{
  "mode": "user_profile",
  "userIds": [
    "946974",
    "642389251"
  ],
  "maxResults": 20
}
```

---

## Output

All scraped records are stored in your Apify **Dataset** and can be exported to JSON, CSV, Excel, XML, or Parquet. Below are sample JSON outputs matching the `"946974"` (影视飓风 MediaStorm) input above:

### 1. Creator Uploaded Video Row (`mode: "user_videos"`)
```json
{
  "mode": "user_videos",
  "bvid": "BV1xrnz6gEVD",
  "aid": 117478344627500,
  "cid": 1689123456,
  "title": "折1万次，会坏吗？iPhone Duo深度评测",
  "text": "相信各位和我们一样，对苹果的第一台折叠屏手机充满了好奇，这次我们为iPhone Duo准备了一系列特别的测试...",
  "description": "相信各位和我们一样，对苹果的第一台折叠屏手机充满了好奇，这次我们为iPhone Duo准备了一系列特别的测试...",
  "authorName": "影视飓风",
  "authorId": "946974",
  "authorAvatar": "https://i0.hdslb.com/bfs/face/c1733474892caa45952b2c09a89323157df7129a.jpg",
  "views": 9605258,
  "likesCount": 684200,
  "coinsCount": 512000,
  "favoritesCount": 389000,
  "sharesCount": 142000,
  "danmakuCount": 48920,
  "commentsCount": 21540,
  "coinPerViewRatio": 0.0533,
  "engagementRate": 0.1798,
  "duration": 1492,
  "videoTimeFormatted": "24:52",
  "category": "数码",
  "tags": ["数码", "评测", "影视飓风", "科技"],
  "peakMinute": "14:00-14:59",
  "danmakuSamples": [
    "[14:12] 真就硬折一万次啊，太狠了！",
    "[14:35] 影视飓风出品必属精品，三连了"
  ],
  "coverUrl": "https://i0.hdslb.com/bfs/archive/ccacc1c956715cf06db7a29b634c3c269654acea.jpg",
  "videoUrl": "https://www.bilibili.com/video/BV1xrnz6gEVD",
  "authorUrl": "https://space.bilibili.com/946974",
  "createdAtIso": "2026-10-21T12:00:00Z",
  "scrapedAtIso": "2026-10-28T10:40:00Z"
}
```

### 2. Creator Profile Row (`mode: "user_profile"`)
```json
{
  "mode": "user_profile",
  "authorId": "946974",
  "authorName": "影视飓风",
  "title": "影视飓风",
  "text": "无限进步！商务合作请联系：bd@mediastorm.cn",
  "description": "无限进步！商务合作请联系：bd@mediastorm.cn",
  "authorAvatar": "https://i0.hdslb.com/bfs/face/c1733474892caa45952b2c09a89323157df7129a.jpg",
  "authorLevel": 6,
  "followersCount": 11250000,
  "followingCount": 412,
  "videosCount": 685,
  "likesCount": 98400000,
  "officialVerify": "bilibili 2023百大UP主、知名科技UP主",
  "vipLabel": "年度大会员",
  "authorUrl": "https://space.bilibili.com/946974",
  "scrapedAtIso": "2026-10-28T10:40:05Z"
}
```

### Output Field Definitions
* **`bvid` / `aid` / `cid`**: Unique Bilibili video BV ID, numeric archive ID, and player cid.
* **`views` / `likesCount` / `coinsCount` / `favoritesCount` / `sharesCount`**: Complete playback and One-Click Triple Combo engagement counts.
* **`coinPerViewRatio` / `engagementRate`**: Derived KOL vetting ratios (`coins / views` and `(likes + coins + favorites + shares) / views`).
* **`followersCount` / `videosCount` / `likesCount` (on profile)**: Creator total subscribers, uploaded video count, and cumulative channel likes.
* **`officialVerify` / `authorLevel` / `vipLabel`**: Creator verification title, community level (`LV0–LV6`), and VIP badge.

---

## Automated Daily Creator Upload Monitoring (Schedules & Delta Mode)

Get alerted whenever a tracked Bilibili UP creator uploads a new video:
1. Go to **Apify Console → Schedules → Create new schedule** and select **`axon-studio/bilibili-creator-videos-scraper`**.
2. Set **`deltaMode: true`** in your input configuration. Previously delivered `bvid` records are stored in your Key-Value Store and skipped on future runs—so you are only billed when a creator publishes a brand-new video.

### Python & Synchronous REST API Integration

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_API_TOKEN")
run = client.actor("axon-studio/bilibili-creator-videos-scraper").call(run_input={
    "mode": "user_videos",
    "userIds": ["946974"],
    "maxResults": 20,
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item["bvid"], item["views"], item["coinPerViewRatio"], item["title"])
```

```bash
curl -X POST "https://api.apify.com/v2/acts/axon-studio~bilibili-creator-videos-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"mode":"user_videos","userIds":["946974"],"maxResults":20}'
```

---

## How Much Does It Cost to Scrape Bilibili Creators? (Pricing)

**$4.50 per 1,000 results (`$0.0045` per video or profile) + `$0.02` per Actor start (Pay-Per-Event)**

* **Free Plan Credits**: Every Apify account includes **$5.00 in free monthly credits**, covering up to **1,111 Bilibili creator videos or profiles every month for free**.
* **Volume Discounts**: Automatic lower unit prices for Apify **Bronze / Starter**, **Silver / Scale**, and **Gold / Business** plan subscribers.
* **No Extra Server Compute Fees**: Runs on just 256 MB RAM with platform compute usage fully included.
* **Typical Run Costs**: 30 creator videos = **`$0.155`** · 100 creator videos = **`$0.47`** · 50 KOL profiles = **`$0.245`**.

---

## FAQ & Legal Compliance

### How does this scraper avoid Bilibili `-352` risk control on `user_videos` without cookies?
Unlike basic scrapers that fail on creator space pages or guess via general keyword search, our 3-stage engine queries Bilibili's unblocked archive series API first, falls back to WebGL-fingerprinted WBI space requests, and enriches every video via `/x/web-interface/view`.

### Is it legal to scrape public Bilibili creator channels?
This Actor extracts publicly visible creator profiles and video metadata on `bilibili.com` and cannot access private accounts. Under **GDPR** and **PIPL**, ensure you have a lawful basis for influencer due diligence or market research. *Not affiliated with Bilibili Inc.*

---

## More Chinese Social Intelligence Scrapers by Axon Studio

* **[Bilibili Scraper 哔哩哔哩 (No Cookie) — All-in-One Videos, Danmaku, Comments & Creators](https://apify.com/axon-studio/bilibili-scraper)** — Full 8-mode Bilibili intelligence suite.
* **[Bilibili Danmaku Scraper — XML Bullet Comments & Peak Minute Extractor](https://apify.com/axon-studio/bilibili-danmaku-scraper)** — Extract time-aligned XML bullet comments (`list.so`).
* **[Bilibili Comments & IP Geolocation Scraper](https://apify.com/axon-studio/bilibili-comments-scraper)** — Extract Bilibili comment threads and English IP province locations (`regionEn`).
* **[Weibo Scraper 微博 (No Cookie) — Search, Posts, Comments & BlackCat](https://apify.com/axon-studio/weibo-scraper)** — 9-mode Sina Weibo & BlackCat social listening suite.
