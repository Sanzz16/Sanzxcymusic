# Spotify Scraper (`automation-lab/spotify-scraper`) Actor

Extract Spotify artists, tracks, albums, and playlists from search terms or URLs. Get monthly listeners, play counts, followers, world rank, biographies, and top tracks — no API key needed.

- **URL**: https://apify.com/automation-lab/spotify-scraper.md
- **Developed by:** [Automation Lab](https://apify.com/automation-lab) (community)
- **Categories:** Social media, MCP servers
- **Stats:** 702 total users, 108 monthly users, 100.0% runs succeeded, 6 bookmarks
- **User rating**: No ratings yet

## Pricing

from $2.61 / 1,000 item scrapeds

This Actor is paid per event. You are not charged for the Apify platform usage, but only a fixed price for specific events.
Since this Actor supports Apify Store discounts, the price gets lower the higher subscription plan you have.

Learn more: https://docs.apify.com/actors/running/actors-in-store.md#pay-per-event

## What's an Apify Actor?

An Actor is a serverless cloud program that runs on the Apify platform. It has two run modes.
In Batch mode, an Actor accepts a well-defined JSON input, performs an action which can take anything from a few seconds to a few hours,
and optionally produces a well-defined JSON output, datasets with results, or files in key-value store.
In Standby mode, an Actor provides a web server which can be used as a website, API, or an MCP server.

Apify vocabulary and the platform model are defined once, in the agent quickstart at https://apify.com/agents.md.

## How to integrate an Actor?

If asked about integration, you help developers integrate Actors into their projects.
You adapt to their stack and deliver integrations that are safe, well-documented, and production-ready.

Do not guess an integration path. Every one of them is in the agent quickstart at https://apify.com/agents.md: the Apify MCP server, Agent Skills with the Apify CLI, the JavaScript and Python clients, the REST API, and the account-free path for an agent with no human to sign in. It also carries the rule on stating cost before the first paid run.

For examples already wired to this Actor's own input schema, see the [API](#api) section below.

Each client library has reference documentation the quickstart does not restate: [JavaScript/TypeScript](https://docs.apify.com/api/client/js/docs.md) (`npm install apify-client`) and [Python](https://docs.apify.com/api/client/python/docs.md) (`pip install apify-client`).

# README

## Spotify Scraper for Music, Podcast Shows & Episodes

Search [Spotify](https://open.spotify.com) by keyword or scrape artist, album, track, playlist, podcast show, and episode URLs. Get music analytics plus podcast titles, descriptions, publishers, show links, release dates, durations, playability, and previews in JSON, CSV, or Excel — no Spotify API key needed.

### What does Spotify Scraper do?

Spotify Scraper extracts rich metadata from Spotify using its internal GraphQL API and public embed pages. Two modes:

- **Search mode** — Search by keyword and get tracks, artists, albums, or playlists matching your query
- **URL mode** — Provide direct Spotify URLs for detailed data extraction

#### What data you get

- **Artists** — Monthly listeners, followers, world rank, biography, top tracks with play counts, related artists, external links (Wikipedia, Instagram, etc.)
- **Albums** — Cover art, track listing with per-track play counts, release date, label
- **Tracks** — Play count, artists, album name, duration, release date, explicit flag, audio preview URL
- **Playlists** — Owner, description, track listing with durations, cover image
- **Podcast shows** — Show name, publisher, description, cover image, and canonical Spotify URL
- **Podcast episodes** — Episode title and description, show linkage, release date, duration, explicit/playability/video flags, cover image, and audio preview when Spotify exposes one

### Why scrape Spotify?

Spotify is the world's largest music streaming platform with 600M+ users and 100M+ tracks. Structured Spotify data is valuable for:

- 🎵 **Music analytics** — Monthly listeners, play counts, and follower trends
- 📊 **Playlist research** — Analyze editorial and user playlists for genre trends
- 🎤 **Artist monitoring** — Track world rank, top songs, new releases, and related artists
- 📰 **Content creation** — Build data-driven playlists, reviews, and music newsletters
- 🎧 **App development** — Power music recommendation engines and discovery tools
- 📈 **Market research** — Study music industry trends and playlist curation patterns

### Who is it for?

Spotify Scraper is for music marketers, playlist researchers, artist managers, data teams, and developers who need structured Spotify catalog and popularity data without building a custom crawler.

### Use cases

- **Music journalists** tracking new releases and artist popularity changes
- **Record labels** monitoring artist metrics (monthly listeners, world rank, play counts)
- **Data scientists** building music recommendation datasets
- **Playlist curators** researching top-performing tracks and artists
- **Developers** building music apps that need structured artist/track data
- **Marketers** analyzing playlist trends for brand partnerships

### How to scrape Spotify

1. Go to [Spotify Scraper](https://apify.com/automation-lab/spotify-scraper) on Apify Store
2. Choose a mode: **Search by keyword** or **Scrape by URL**
3. For search: enter keywords and select result type (tracks, artists, albums, or playlists)
4. For URLs: paste one or more Spotify URLs (artists, albums, tracks, playlists, shows, or episodes)
5. Set the max results limit
6. Click **Start** and wait for results
7. Download data as JSON, CSV, or Excel

### Data you can extract

#### Artist data

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Artist name |
| `monthlyListeners` | number | Current monthly listener count |
| `followers` | number | Total follower count |
| `worldRank` | number | Spotify global rank |
| `biography` | string | Artist biography text |
| `imageUrl` | string | Profile image (high-res) |
| `topTracks` | array | Top 10 tracks with play counts and durations |
| `relatedArtists` | array | Related artist names and IDs |
| `externalLinks` | array | Links to Wikipedia, Instagram, Facebook, etc. |
| `genres` | array | Associated music genres |

#### Album data

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Album name |
| `artist` | string | Artist name |
| `imageUrl` | string | Album cover art |
| `releaseDate` | string | Release date |
| `trackCount` | number | Number of tracks |
| `tracks` | array | All tracks with play counts and durations |

#### Track data

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Track name |
| `artists` | string | Artist name(s) |
| `playCount` | number | Total play count |
| `albumName` | string | Album name |
| `albumArt` | string | Album cover image URL |
| `releaseDate` | string | Release date |
| `duration` | number | Duration in milliseconds |
| `durationFormatted` | string | Duration (e.g., `3:46`) |
| `isExplicit` | boolean | Explicit content flag |
| `audioPreviewUrl` | string | 30-second audio preview URL |

#### Playlist data

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Playlist name |
| `owner` | string | Playlist owner |
| `description` | string | Playlist description |
| `imageUrl` | string | Playlist cover image |
| `trackCount` | number | Number of tracks |
| `tracks` | array | All tracks with titles, artists, durations |

#### Podcast show and episode data

| Field | Applies to | Description |
|-------|------------|-------------|
| `name` | show, episode | Show name or episode title |
| `publisher` | show | Public show publisher |
| `showName`, `showId`, `showUrl` | episode | Parent-show linkage |
| `description` | show, episode | Public Spotify description |
| `imageUrl` | show, episode | Show or episode artwork |
| `releaseDate` | episode | Episode release timestamp |
| `duration`, `durationFormatted` | episode | Duration in milliseconds and readable form |
| `isExplicit`, `isPlayable`, `hasVideo` | episode | Public content and playback flags |
| `audioPreviewUrl` | episode | Preview URL when Spotify exposes one |

### Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `mode` | string | `urls` | `search` for keyword search, `urls` for direct URL scraping |
| `urls` | array | — | Spotify URLs to scrape (URL mode) |
| `searchTerms` | array | — | Keywords to search on Spotify (search mode) |
| `searchType` | string | `tracks` | Result type for search: `tracks`, `artists`, `albums`, `playlists` |
| `maxResults` | integer | `50` | Max items to scrape |

#### Search mode example

```json
{
    "mode": "search",
    "searchTerms": ["arctic monkeys", "indie rock"],
    "searchType": "artists",
    "maxResults": 10
}
```

#### URL mode example

```json
{
    "mode": "urls",
    "urls": [
        "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
        "https://open.spotify.com/album/78bpIziExqiI9qztvNFlQu",
        "https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M",
        "https://open.spotify.com/show/2MAi0BvDc6GTFvKFPXnkCL",
        "https://open.spotify.com/episode/45lhw2Adbrsw0xSCOgIeg3"
    ],
    "maxResults": 50
}
```

### Output example

#### Artist (URL mode — full data)

```json
{
    "type": "artist",
    "id": "06HL4z0CvFAxyc27GXpf02",
    "name": "Taylor Swift",
    "url": "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
    "imageUrl": "https://i.scdn.co/image/ab6761610000e5ebe2e8e7ff002a4afda1c7147e",
    "monthlyListeners": 54700000,
    "followers": 33600000,
    "worldRank": 3,
    "biography": "Taylor Alison Swift is an American singer-songwriter...",
    "topTracks": [
        {
            "trackId": "1BxfuPKGuaTgP7aM0Bbdwr",
            "title": "Cruel Summer",
            "artists": "Taylor Swift",
            "duration": 178427,
            "durationFormatted": "2:58",
            "playCount": 3600000000,
            "isExplicit": false
        }
    ],
    "relatedArtists": [
        { "name": "Ed Sheeran", "id": "6eUKZXaKkcviH0Ku9w2n3V", "url": "https://open.spotify.com/artist/6eUKZXaKkcviH0Ku9w2n3V" }
    ],
    "externalLinks": [
        { "name": "Wikipedia", "url": "https://en.wikipedia.org/wiki/Taylor_Swift" }
    ],
    "scrapedAt": "2026-03-10T17:00:00.000Z"
}
```

#### Podcast episode

```json
{
    "type": "episode",
    "id": "45lhw2Adbrsw0xSCOgIeg3",
    "name": "Example podcast episode",
    "showName": "Example Podcast",
    "showId": "2MAi0BvDc6GTFvKFPXnkCL",
    "showUrl": "https://open.spotify.com/show/2MAi0BvDc6GTFvKFPXnkCL",
    "description": "An example public episode description.",
    "releaseDate": "2026-08-26T21:47:00Z",
    "duration": 3600000,
    "durationFormatted": "60:00",
    "isExplicit": false,
    "isPlayable": true,
    "hasVideo": false,
    "audioPreviewUrl": "https://p.scdn.co/mp3-preview/...",
    "url": "https://open.spotify.com/episode/45lhw2Adbrsw0xSCOgIeg3",
    "scrapedAt": "2026-08-31T18:00:00.000Z"
}
```

#### Track

```json
{
    "type": "track",
    "id": "5XeFesFbtLpXzIVDNQP22n",
    "name": "I Wanna Be Yours",
    "artists": "Arctic Monkeys",
    "albumName": "AM",
    "albumArt": "https://i.scdn.co/image/ab67616d0000b2734ae1c4c5c45aabe565499163",
    "releaseDate": "2013-09-09T00:00:00Z",
    "duration": 183066,
    "durationFormatted": "3:03",
    "playCount": null,
    "isExplicit": false,
    "audioPreviewUrl": "https://p.scdn.co/mp3-preview/...",
    "url": "https://open.spotify.com/track/5XeFesFbtLpXzIVDNQP22n",
    "scrapedAt": "2026-03-10T17:00:00.000Z"
}
```

### How much does it cost to scrape Spotify?

Spotify Scraper uses pay-per-event pricing:

| Event | Price |
|-------|-------|
| Run started | $0.005 |
| Item scraped | $0.005 FREE / $0.00435 BRONZE per artist/album/track/playlist/show/episode |

For large inputs, set **Maximum charge per run** in Apify before starting. This actor now checks that PPE limit while running and stops cleanly when the cap is reached.

#### Cost examples

| Scenario | Items | Cost |
|----------|-------|------|
| Search 10 artists | 10 | ~$0.055 |
| 1 artist + 1 playlist by URL | 2 | ~$0.015 |
| 5 albums by URL | 5 | ~$0.030 |
| Search 50 tracks | 50 | ~$0.255 |

Apify's free plan includes $5/month — enough for ~330 Spotify items.

### API usage

#### Node.js

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

// Search mode
const run = await client.actor('automation-lab/spotify-scraper').call({
    mode: 'search',
    searchTerms: ['arctic monkeys'],
    searchType: 'artists',
    maxResults: 5,
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => {
    console.log(`${item.name} — ${item.monthlyListeners?.toLocaleString() || '?'} monthly listeners`);
});
```

#### Python

```python
from apify_client import ApifyClient

client = ApifyClient('YOUR_API_TOKEN')

## URL mode
run = client.actor('automation-lab/spotify-scraper').call(run_input={
    'mode': 'urls',
    'urls': [
        'https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02',
        'https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M',
    ],
    'maxResults': 50,
})

dataset = client.dataset(run['defaultDatasetId']).list_items().items
for item in dataset:
    print(f"{item['type']}: {item['name']}")
```

#### cURL

```bash
curl "https://api.apify.com/v2/acts/automation-lab~spotify-scraper/run-sync-get-dataset-items?token=YOUR_API_TOKEN" \
  -X POST -H "Content-Type: application/json" \
  -d '{"mode": "search", "searchTerms": ["taylor swift"], "searchType": "tracks", "maxResults": 10}'
```

### 🤖 Agent and LLM workflow (Apify API / MCP-ready)

Use this actor as an agent-ready music intelligence source for artist monitoring, playlist research, and catalog enrichment. It does **not** expose a native Spotify MCP endpoint; AI assistants can run it through Apify's API, Apify Integrations, or the Apify MCP server and then analyze the dataset results.

**Example agent task:** "Find Arctic Monkeys' current monthly listeners, top tracks, and related artists, then summarize changes I should watch in a weekly music-market report."

#### Call from an agent via API

```bash
curl "https://api.apify.com/v2/acts/automation-lab~spotify-scraper/runs?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"mode":"urls","urls":["https://open.spotify.com/artist/7Ln80lUS6He07XvHI8qqHH"],"maxResults":10}'

## After the run finishes, let the agent fetch and summarize the dataset
curl "https://api.apify.com/v2/datasets/DATASET_ID/items?format=json" \
  -H "Authorization: Bearer YOUR_APIFY_TOKEN"
```

#### Use through Apify MCP server

If your AI client supports MCP, connect the Apify MCP server and allow only this actor:

```bash
claude mcp add --transport http apify "https://mcp.apify.com?tools=automation-lab/spotify-scraper"
```

Claude Desktop, Cursor, and VS Code can use the same actor-scoped endpoint in their MCP configuration:

```json
{
    "mcpServers": {
        "spotify-scraper": {
            "url": "https://mcp.apify.com?tools=automation-lab/spotify-scraper"
        }
    }
}
```

Example prompts:

- "Scrape this Spotify show and episode URL, then summarize the episode and include its release date and duration."
- "Get the current monthly listeners and top tracks for these Spotify artist URLs."
- "Extract this playlist and compare its artists with the linked podcast episode."

Then ask your assistant to run `automation-lab/spotify-scraper` with artist, album, track, playlist, show, or episode URLs (or music search terms), wait for the Apify run to finish, and work with fields such as monthly listeners, play counts, podcast descriptions, release dates, and show linkage.

### Integrations

- **Scheduled runs** — Monitor artist metrics or playlist changes daily
- **Webhooks** — Trigger actions when new data is available
- **Google Sheets** — Export track listings and play counts to spreadsheets
- **Slack** — Notify your team about artist ranking changes
- **Zapier / Make** — Automate music data workflows

### Tips

- 🔍 **Search first** — Use search mode to discover artists/tracks, then scrape specific URLs for full details
- 🎤 **Rich artist data** — URL mode for artists returns monthly listeners, followers, world rank, biography, and related artists
- 💿 **Album play counts** — Album tracks include per-track play counts (billions of plays for top songs)
- 🔗 **Copy URLs from Spotify** — Use "Share > Copy link" in the Spotify app or web player
- 📋 **Playlist monitoring** — Schedule daily runs on editorial playlists to track additions/removals
- 🎵 **Mix URL types** — Scrape artists, albums, tracks, playlists, shows, and episodes in a single run
- 🎙️ **Podcast enrichment** — Scrape a show URL for publisher-level metadata and episode URLs for detailed release, duration, and playback fields

### Limitations

- **Search results have limited data** — Search mode returns basic fields. For full data (monthly listeners, play counts, biography), use URL mode with artist/album URLs
- **Top tracks only** — Artist pages show top ~10 tracks, not the full discography
- **Playlist limit** — Embed pages show up to 100 tracks per playlist
- **Public podcast metadata only** — Show and episode fields come from Spotify's anonymous public pages and embeds. Descriptions, previews, publisher names, and playback flags may be unavailable for some catalog items or markets
- **Podcast search is not included** — Show and episode extraction currently requires direct Spotify URLs; keyword search remains available for tracks, artists, albums, and playlists
- **Residential proxy required** — Spotify blocks datacenter IPs; this actor uses residential proxies

### Diagnostic privacy

Failed operations send sanitized diagnostic input, exceptions, and Actor/build/run IDs to our private GlitchTip service for repair. Secret fields and URL queries are removed; reports are retained for 30 days. The Actor does not use AI or send data to model providers. Public Spotify pages and Apify residential proxies provide extraction; their operating costs are included in the listed Actor charges. Output remains in your Apify run storage under your account's retention settings until deleted; the Actor does not create a separate persistent customer database. Use only public URLs and non-sensitive search terms: these can appear in run logs. This independently developed tool is not affiliated with or endorsed by Spotify.

### Legality

This scraper accesses Spotify's publicly available pages and internal APIs — the same data shown to any Spotify visitor. It does not bypass authentication, use private API keys, or download copyrighted audio content. Always review [Spotify's Terms of Service](https://www.spotify.com/legal/end-user-agreement/) before use.

### FAQ

**Do I need a Spotify account?**
No. The scraper uses Spotify's anonymous access tokens — no account required.

**Can I get monthly listeners and play counts?**
Yes! Artist pages include monthly listeners, followers, world rank, and top track play counts. Album tracks also include per-track play counts.

**What's the difference between search and URL mode?**
Search mode finds content by keyword with basic metadata. URL mode extracts full details including monthly listeners, play counts, biography, and related artists.

**What URL formats are supported?**
Standard Spotify URLs (`open.spotify.com/...`), short URLs, and Spotify URIs (`spotify:track:...`).

**Can I scrape podcast shows and episodes?**
Yes. Use URL mode with `open.spotify.com/show/...` or `open.spotify.com/episode/...` URLs. Each URL emits one typed parent record and one `item` charge. Episode records include their parent show ID and URL when Spotify exposes them.

**How often does the data update?**
Spotify updates metrics like monthly listeners and play counts in near-real-time. Each scrape returns the latest available data.

**The scraper is failing with proxy errors or timeouts.**
Spotify blocks datacenter IP addresses, so residential proxies are required. The actor uses Apify's residential proxy pool automatically. If you are on a plan without residential proxy access, you may see failures. Upgrade your Apify plan or ensure residential proxy is enabled.

**Why is playCount null for some tracks in search mode?**
Search mode uses Spotify's search API which returns limited metadata. Play counts are only available in URL mode when scraping a specific artist or album page. Use URL mode with the artist/album URL for full play count data.

### How do I track Spotify artist growth over time?

To monitor an artist's monthly listeners, follower count, or world rank over time, use Apify's built-in scheduling to run the scraper automatically on a recurring basis:

1. Set up a run with the artist's Spotify URL in URL mode
2. Go to **Schedules** in Apify Console and create a daily or weekly trigger
3. Export each run's results to Google Sheets or a database to build a historical dataset

This is particularly useful for record labels, artist managers, and music journalists tracking emerging artists or charting campaigns.

### What is the difference between the Spotify Web API and scraping?

The official [Spotify Web API](https://developer.spotify.com/documentation/web-api) requires developer credentials, OAuth authentication, and has strict rate limits. It also does not expose all the same data — for example, **monthly listeners, world rank, and play counts** are not available through the official API, only on the public Spotify web pages.

This scraper accesses Spotify's internal GraphQL API and public embed pages — the same data any browser sees — without requiring a Spotify account or developer credentials. It's the only way to programmatically access monthly listener counts and global rank data.

### How do I get monthly listener data for multiple artists at once?

Provide multiple artist URLs in the `urls` field in a single run:

```json
{
    "mode": "urls",
    "urls": [
        "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
        "https://open.spotify.com/artist/3TVXtAsR1Inumwj472S9r4",
        "https://open.spotify.com/artist/1Xyo4u8uXC1ZmMpatF05PJ"
    ],
    "maxResults": 50
}
```

Each artist result includes `monthlyListeners`, `followers`, `worldRank`, `biography`, `topTracks`, and `relatedArtists`. You can scrape dozens of artists in a single run.

### Can I scrape Spotify playlist data for research?

Yes. Provide a playlist URL in URL mode to extract the full track listing with titles, artists, durations, and cover art. This is useful for:

- Analyzing what tracks appear on editorial playlists (e.g., "Today's Top Hits")
- Monitoring playlist additions and removals over time with scheduled runs
- Building datasets of genre-specific playlists for music recommendation research
- Tracking user-curated playlists for content strategy

Playlists return up to 100 tracks per playlist via the embed API.

### Related scrapers

- [YouTube Scraper](https://apify.com/automation-lab/youtube-scraper) — Scrape YouTube videos, channels, and playlists
- [Podcast Scraper](https://apify.com/automation-lab/podcast-scraper) — Extract podcast episodes and metadata
- [iTunes Scraper](https://apify.com/automation-lab/itunes-scraper) — Scrape iTunes app and media data

### Use with AI agents via x402 (no Apify account)

Agent workflows can run this actor through Apify MCP without an Apify account when the MCP client uses a funded x402 wallet. Use the actor-specific MCP endpoint:

`https://mcp.apify.com?tools=automation-lab/spotify-scraper&payment=x402`

This keeps existing Apify MCP/API usage unchanged; x402 only changes payment/authentication for clients that support it. Learn more in Apify's [x402 integration docs](https://docs.apify.com/platform/integrations/x402).

# Changelog

This Actor's version history is a separate document: https://apify.com/automation-lab/spotify-scraper/changelog.md

# Actor input Schema

## `mode` (type: `string`):

Choose the active input mode. In URL mode, fill Spotify URLs. In search mode, fill search queries and a search result type.

## `urls` (type: `array`):

Spotify URLs to scrape in URL mode. Supports artist, album, track, playlist, show, and episode URLs, for example https://open.spotify.com/show/2MAi0BvDc6GTFvKFPXnkCL.

## `searchTerms` (type: `array`):

Keywords to search on Spotify in search mode. Each query returns results of the selected search type.

## `searchType` (type: `string`):

What type of Spotify results to return when mode is Search by keyword.

## `maxResults` (type: `integer`):

Maximum number of Spotify items to scrape per search query, or total URL records to process in URL mode.

## Actor input object example

```json
{
  "mode": "urls",
  "urls": [
    "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
    "https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M"
  ],
  "searchTerms": [
    "arctic monkeys"
  ],
  "searchType": "tracks",
  "maxResults": 10
}
```

# Actor output Schema

## `overview` (type: `string`):

Table view of scraped artists, albums, tracks, playlists, shows, and episodes.

# API

You can run this Actor programmatically using our API. Below are code examples in JavaScript, Python, and CLI, as well as the OpenAPI specification and MCP server setup.

## JavaScript example

```javascript
import { ApifyClient } from 'apify-client';

// Initialize the ApifyClient with your Apify API token
// Replace the '<YOUR_API_TOKEN>' with your token
const client = new ApifyClient({
    token: '<YOUR_API_TOKEN>',
});

// Prepare Actor input
const input = {
    "mode": "urls",
    "urls": [
        "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
        "https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M"
    ],
    "searchTerms": [
        "arctic monkeys"
    ],
    "maxResults": 10
};

// Run the Actor and wait for it to finish
const run = await client.actor("automation-lab/spotify-scraper").call(input);

// Fetch and print Actor results from the run's dataset (if any)
console.log('Results from dataset');
console.log(`💾 Check your data here: https://console.apify.com/storage/datasets/${run.defaultDatasetId}`);
const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach((item) => {
    console.dir(item);
});

// 📚 Want to learn more 📖? Go to → https://docs.apify.com/api/client/js/docs

```

## Python example

```python
from apify_client import ApifyClient

# Initialize the ApifyClient with your Apify API token
# Replace '<YOUR_API_TOKEN>' with your token.
client = ApifyClient("<YOUR_API_TOKEN>")

# Prepare the Actor input
run_input = {
    "mode": "urls",
    "urls": [
        "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
        "https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M",
    ],
    "searchTerms": ["arctic monkeys"],
    "maxResults": 10,
}

# Run the Actor and wait for it to finish
run = client.actor("automation-lab/spotify-scraper").call(run_input=run_input)

# Fetch and print Actor results from the run's dataset (if there are any)
print(f"💾 Check your data here: https://console.apify.com/storage/datasets/{run.default_dataset_id}")
for item in client.dataset(run.default_dataset_id).iterate_items():
    print(item)

# 📚 Want to learn more 📖? Go to → https://docs.apify.com/api/client/python/docs/quick-start

```

## CLI example

```bash
echo '{
  "mode": "urls",
  "urls": [
    "https://open.spotify.com/artist/06HL4z0CvFAxyc27GXpf02",
    "https://open.spotify.com/playlist/37i9dQZF1DXcBWIGoYBM5M"
  ],
  "searchTerms": [
    "arctic monkeys"
  ],
  "maxResults": 10
}' |
apify call automation-lab/spotify-scraper --silent --output-dataset

```

## MCP server setup

```json
{
    "mcpServers": {
        "apify": {
            "type": "http",
            "url": "https://mcp.apify.com/?tools=fetch-actor-details,automation-lab/spotify-scraper"
        }
    }
}
```

The hosted server signs you in with OAuth on first connect, so no API token belongs in this config. Clients without OAuth support can send an `Authorization: Bearer <APIFY_API_TOKEN>` header instead, using a token from API & Integrations in Apify Console (https://console.apify.com/settings/integrations).

## OpenAPI specification

Download the OpenAPI definition: https://api.apify.com/v2/actors/PIJgVEhbc8dGehrsP/builds/uMvIpseJbQbfoXJif/openapi.json
