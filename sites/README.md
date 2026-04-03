# tap-sites

Community site scripts for [tap](https://github.com/vaayne/tap) — turning websites into CLI commands.

Each site adapter is a JS function that runs inside your browser via `tap eval`. The browser is already logged in — no API keys, no cookie extraction, no anti-bot bypass.

[English](README.md) · [中文](README.zh-CN.md)

> **106 adapters** across **44 platforms** — and growing.

## Quick Start

```bash
tap site update                     # install/update site adapters
tap site list                       # list available commands
tap site reddit/me                  # run a command
tap site reddit/thread <url>        # run with args
```

## Available Adapters

### 🔍 Search Engines

| Platform | Command | Description |
|----------|---------|-------------|
| Google | `google/search` | Google search |
| Baidu | `baidu/search` | Baidu search |
| Bing | `bing/search` | Bing search |
| DuckDuckGo | `duckduckgo/search` | DuckDuckGo search (HTML lite) |
| Sogou | `sogou/weixin` | Sogou WeChat article search |

### 📰 News & Media

| Platform | Command | Description |
|----------|---------|-------------|
| BBC | `bbc/news` | BBC News headlines (RSS) or search |
| Reuters | `reuters/search` | Reuters news search |
| Toutiao | `toutiao/search`, `toutiao/hot` | Toutiao (今日头条) search & trending |
| Eastmoney | `eastmoney/news` | Eastmoney (东方财富) financial news |
| 36Kr | `36kr/newsflash` | 36氪 (创业科技新闻) newsflash |

### 💬 Social Media

| Platform | Commands | Description |
|----------|----------|-------------|
| Twitter/X | `twitter/user`, `twitter/thread`, `twitter/search`, `twitter/tweets`, `twitter/notifications` | User profile, tweet threads, search, timeline, notifications |
| Reddit | `reddit/me`, `reddit/posts`, `reddit/thread`, `reddit/context` | User info, posts, discussion trees, comment chains |
| Weibo | `weibo/me`, `weibo/hot`, `weibo/feed`, `weibo/user`, `weibo/user_posts`, `weibo/post`, `weibo/comments` | Full Weibo (微博) support — profile, trending, timeline, posts, comments |
| Hupu | `hupu/hot` | Hupu (虎扑) hot posts |

### 💻 Tech & Dev

| Platform | Commands | Description |
|----------|----------|-------------|
| GitHub | `github/me`, `github/repo`, `github/issues`, `github/issue-create`, `github/pr-create`, `github/fork` | User info, repos, issues, PRs, forks |
| Hacker News | `hackernews/top`, `hackernews/thread` | Top stories, post + comment tree |
| Stack Overflow | `stackoverflow/search` | Search questions |
| CSDN | `csdn/search` | CSDN tech article search |
| cnblogs | `cnblogs/search` | cnblogs (博客园) tech article search |
| npm | `npm/search` | Search npm packages |
| PyPI | `pypi/search`, `pypi/package` | Search & get Python package details |
| arXiv | `arxiv/search` | Search academic papers |
| Dev.to | `devto/search` | Search Dev.to articles |
| V2EX | `v2ex/hot`, `v2ex/latest`, `v2ex/topic` | Hot/latest topics, topic detail + replies |

### 🎬 Entertainment

| Platform | Commands | Description |
|----------|----------|-------------|
| YouTube | `youtube/search`, `youtube/video`, `youtube/comments`, `youtube/channel`, `youtube/feed`, `youtube/transcript` | Search, video details, comments, channels, feed, transcripts |
| Bilibili | `bilibili/me`, `bilibili/popular`, `bilibili/ranking`, `bilibili/search`, `bilibili/video`, `bilibili/comments`, `bilibili/feed`, `bilibili/history`, `bilibili/trending` | Full B站 support — 9 adapters |
| IMDb | `imdb/search` | IMDb movie search |
| Genius | `genius/search` | Song/lyrics search |
| Douban | `douban/search`, `douban/movie`, `douban/movie-hot`, `douban/movie-top`, `douban/top250`, `douban/comments` | Douban (豆瓣) movies — search, details, rankings, Top 250, reviews |
| Qidian | `qidian/search` | Qidian (起点中文网) novel search |

### 💼 Jobs & Career

| Platform | Commands | Description |
|----------|----------|-------------|
| BOSS Zhipin | `boss/search`, `boss/detail` | BOSS直聘 job search & JD details |
| LinkedIn | `linkedin/profile`, `linkedin/search` | LinkedIn profile & post search |

### 💰 Finance

| Platform | Commands | Description |
|----------|----------|-------------|
| Eastmoney | `eastmoney/stock`, `eastmoney/news` | 东方财富 stock quotes & financial news |
| Yahoo Finance | `yahoo-finance/quote` | Stock quotes (AAPL, TSLA, etc.) |
| Xueqiu | `xueqiu/feed`, `xueqiu/hot`, `xueqiu/hot-stock`, `xueqiu/search`, `xueqiu/stock`, `xueqiu/watchlist` | 雪球 — feed, trending, hot stocks, search, quotes, watchlist |

### 📱 Digital & Products

| Platform | Command | Description |
|----------|---------|-------------|
| GSMArena | `gsmarena/search` | Phone specs search |
| Product Hunt | `producthunt/today` | Today's top products |

### 🛍️ Shopping

| Platform | Command | Description |
|----------|---------|-------------|
| SMZDM | `smzdm/search` | 什么值得买 — deal & coupon search |

### 📚 Knowledge & Reference

| Platform | Commands | Description |
|----------|----------|-------------|
| Wikipedia | `wikipedia/search`, `wikipedia/summary` | Search & page summaries |
| Zhihu | `zhihu/me`, `zhihu/hot`, `zhihu/question`, `zhihu/search` | 知乎 — user info, trending, Q&A, search |
| Open Library | `openlibrary/search` | Book search |

### 🌐 Lifestyle & Travel

| Platform | Command | Description |
|----------|---------|-------------|
| Youdao | `youdao/translate` | 有道翻译 — translation & dictionary |
| Ctrip | `ctrip/search` | 携程 — destination & attraction search |

### 🗨️ Social Apps

| Platform | Commands | Description |
|----------|----------|-------------|
| Jike | `jike/feed`, `jike/search` | 即刻 — recommended feed & search |
| Xiaohongshu | `xiaohongshu/me`, `xiaohongshu/feed`, `xiaohongshu/search`, `xiaohongshu/note`, `xiaohongshu/comments`, `xiaohongshu/user_posts` | 小红书 — full support via Pinia store actions |

> All Xiaohongshu (小红书) adapters use **Pinia Store Actions** — calling the page's own Vue store functions, which go through the complete signing + interceptor chain. Zero reverse engineering needed.

## Usage Examples

```bash
# Search the web
tap site google/search "tap"
tap site duckduckgo/search "Claude Code"

# Social media
tap site twitter/search "claude code"
tap site twitter/tweets plantegg
tap site reddit/thread https://reddit.com/r/programming/comments/...
tap site weibo/hot

# Tech research
tap site github/repo vaayne/tap
tap site hackernews/top 10
tap site stackoverflow/search "python async await"
tap site arxiv/search "large language model"
tap site npm/search "react state management"

# Entertainment
tap site youtube/transcript dQw4w9WgXcQ
tap site bilibili/search 编程
tap site douban/top250

# Finance
tap site yahoo-finance/quote AAPL
tap site eastmoney/stock 贵州茅台

# Jobs
tap site boss/search "AI agent"
tap site linkedin/search "AI agent"

# Translate
tap site youdao/translate hello
```

## Writing a Site Adapter

Run `tap guide` for the full development workflow, or read [SKILL.md](SKILL.md).

```javascript
/* @meta
{
  "name": "platform/command",
  "description": "What this adapter does",
  "domain": "www.example.com",
  "args": {
    "query": {"required": true, "description": "Search query"}
  },
  "readOnly": true,
  "example": "tap site platform/command value1"
}
*/

async function(args) {
  if (!args.query) return {error: 'Missing argument: query'};
  const resp = await fetch('/api/search?q=' + encodeURIComponent(args.query), {credentials: 'include'});
  if (!resp.ok) return {error: 'HTTP ' + resp.status, hint: 'Not logged in?'};
  return await resp.json();
}
```

## Contributing

```bash
# Option A: with gh CLI
gh repo fork vaayne/tap-sites --clone
cd tap-sites && git checkout -b feat-mysite
# add adapter files
git push -u origin feat-mysite
gh pr create

# Option B: with tap (no gh needed)
tap site github/fork vaayne/tap-sites
git clone https://github.com/YOUR_USER/tap-sites && cd tap-sites
git checkout -b feat-mysite
# add adapter files
git push -u origin feat-mysite
tap site github/pr-create vaayne/tap-sites --title "feat(mysite): add adapters" --head "YOUR_USER:feat-mysite"
```

## Private Adapters

Put private adapters in `~/.tap/sites/`. They override community adapters with the same name.

```
~/.tap/
├── sites/          # Your private adapters (priority)
│   └── internal/
│       └── deploy.js
└── tap-sites/       # This repo (tap site update)
    ├── reddit/
    ├── twitter/
    ├── github/
    ├── youtube/
    ├── bilibili/
    ├── zhihu/
    ├── weibo/
    ├── douban/
    ├── xiaohongshu/
    ├── google/
    ├── ...          # 44 platform directories
    └── qidian/
```
