# PRD: AGI Era Podcast Intelligence Hub

## 1. Project Overview
**Project Name:** AGI Era Web Hub  
**Objective:** Create a mobile-first, high-performance static website to host and automate three YouTube podcast series. The site must be data-driven for easy expansion and optimized for Google AdSense through AI-generated text summaries.  
**Core Philosophy:** Automation-first. Once the site is deployed, it should update its content and layout based solely on changes to a data file, triggered by an external automation (n8n).

---

## 2. Tech Stack Requirements
* **Framework:** Astro (Static Site Generator) or Next.js (Static Export).
* **Styling:** Tailwind CSS.
* **Hosting:** Netlify (using Build Hooks for automated deployments).
* **Data Source:** Local `src/data/podcasts.json` file.
* **Monetization:** Google AdSense (Auto-ads and manual placement).

---

## 3. Functional Requirements

### 3.1 Data-Driven UI (Expansion Ready)
* The application must use a `map()` function to iterate through the `podcasts.json` file.
* The UI must generate a new section automatically whenever a new entry is added to the JSON array.
* All podcast sections must have equal visual priority and weight.

### 3.2 YouTube Playlist Integration
* **Player Type:** YouTube IFrame Player (Playlist Embed).
* **Continuous Play:** Embeds must use the `listType=playlist` and `list={playlistId}` parameters.
* **Behavior:** Must support native YouTube continuous play (top-to-bottom/newest-to-oldest within the playlist).
* **Responsiveness:** Use the "Intrinsic Ratio" CSS method (16:9) to ensure players are responsive on mobile.

### 3.3 The "AdSense Booster" (Content Section)
To prevent "Thin Content" rejection from AdSense, each podcast card must include a text-heavy section:
* **Daily Brief:** A list of 3–5 AI-generated bullet points summarizing the latest video.
* **Metadata:** Display the "Last Updated" date and a set of SEO-friendly hashtag chips (e.g., #AI, #Markets).
* **SEO:** Ensure this text is rendered as static HTML (SSR/SSG) for search engine indexing.

### 3.4 Mobile-First UX
* **Layout:** Single-column vertical stack for mobile devices.
* **Touch Targets:** Optimized play buttons and navigation.
* **Performance:** Minimize JavaScript bundle size to ensure fast "Time to Interactive" (TTI) on mobile data.

---

## 4. UI/UX Design Specifications
* **Theme:** Dark Mode (Background: `#0D1117`, Card Background: `#161B22`, Accent: Blue/Cyan).
* **Typography:** Professional Sans-serif (e.g., Inter, Roboto).
* **Aesthetic:** Clean, minimalist, "Tech Command Center" feel with subtle borders and shadows.
* **Layout Hierarchy:** 1. Header (Site Title/Logo)
    2. AdSense Banner Placeholder
    3. Podcast Card 1 (Title -> Video Player -> Summary)
    4. Podcast Card 2 (Title -> Video Player -> Summary)
    5. ... (Iterated for all items in JSON)
    6. Footer with Credits and Links.

---

## 5. Data Schema (`podcasts.json`)
The AI coder must build the site to consume the following structure:

```json
[
  {
    "id": "ai-tech-biz",
    "title": "AI/Tech, Biz, World",
    "playlistId": "PL_YOUR_PLAYLIST_ID_1",
    "description": "Analysis of the AGI transition and global tech trends.",
    "latestSummary": [
      "Key insight regarding Agentic AI workflows.",
      "Market impact of the latest Model Context Protocol (MCP).",
      "Strategic shifts in enterprise architecture."
    ],
    "tags": ["AI", "Tech", "Business"],
    "lastUpdated": "2025-12-30"
  },
  {
    "id": "overnight-market",
    "title": "Overnight Market Brief",
    "playlistId": "PL_YOUR_PLAYLIST_ID_2",
    "description": "Daily pre-market analysis for global financial markets.",
    "latestSummary": [
      "Asian market trends and overnight movers.",
      "Key economic indicators to watch for today's session.",
      "Currency pair volatility updates."
    ],
    "tags": ["Finance", "Markets", "Macro"],
    "lastUpdated": "2025-12-30"
  }
]