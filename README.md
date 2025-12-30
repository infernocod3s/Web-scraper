# Free Website Scraper API

A simple, free website scraper that extracts:
- Text content (no images/videos)
- All scripts
- **Chatbot integrations** (Intercom, Drift, Zendesk, HubSpot, etc.)
- Other integrations (Analytics, Payment, CMS)

## 🚀 Deploy to Vercel (FREE)

### Step 1: Create GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click **"New repository"**
3. Name it `website-scraper`
4. Keep it **Public**
5. Click **"Create repository"**

### Step 2: Upload Files

Upload these 3 files to your repo:
```
website-scraper/
├── api/
│   └── scrape.py
├── vercel.json
└── requirements.txt
```

**Easy way:** 
- Click "Add file" → "Upload files" 
- Drag all files
- Commit

### Step 3: Deploy on Vercel

1. Go to [vercel.com](https://vercel.com)
2. Sign up with GitHub (free)
3. Click **"Add New Project"**
4. Import your `website-scraper` repo
5. Click **"Deploy"**
6. Wait 1-2 minutes

### Step 4: Get Your API Endpoint

After deploy, Vercel gives you a URL like:
```
https://website-scraper-yourusername.vercel.app
```

Your API endpoint is:
```
https://website-scraper-yourusername.vercel.app/api/scrape?url=WEBSITE_URL
```

---

## 📡 API Usage

### Endpoint
```
GET /api/scrape?url={website_url}
```

### Example
```
https://your-app.vercel.app/api/scrape?url=https://intercom.com
```

### Response
```json
{
  "success": true,
  "url": "https://intercom.com",
  "meta": {
    "title": "Intercom | AI Customer Service",
    "description": "..."
  },
  "text_content": "The page text content...",
  "scripts": [
    "https://widget.intercom.io/widget/abc123",
    "[inline]: var intercom_app_id..."
  ],
  "chatbots": [
    {
      "provider": "Intercom",
      "matched_pattern": "intercom"
    }
  ],
  "has_chatbot": true,
  "other_integrations": ["Google Analytics", "Segment"],
  "html_length": 45832
}
```

---

## 🔗 Use in Clay.com

In Clay, add an **HTTP API** enrichment:

**URL:**
```
https://your-app.vercel.app/api/scrape?url={{company_website}}
```

**Method:** GET

Then use the response fields:
- `has_chatbot` → true/false
- `chatbots[0].provider` → "Intercom", "Drift", etc.
- `text_content` → page text for AI analysis

---

## 🤖 Detected Chatbots

The scraper detects these chatbot providers:
- Intercom
- Drift
- Zendesk / Zopim
- HubSpot
- Freshchat
- Tidio
- Crisp
- Tawk.to
- LiveChat
- Olark
- Chatra
- JivoChat
- Comm100
- Pure Chat
- Smartsupp
- Kayako
- Help Scout
- Gorgias
- Chatlio
- SnapEngage

---

## ⚡ Limits

**Vercel Free Tier:**
- 100,000 requests/month
- 10 second timeout per request
- Unlimited deployments

This is MORE than enough for most Clay workflows!

---

## 🛠️ Local Testing

```bash
cd api
python -c "from scrape import scrape_website; print(scrape_website('https://example.com'))"
```

---

## 📝 Notes

- Some websites may block requests (rare)
- JavaScript-rendered content may not load (use for basic HTML)
- No authentication needed
- CORS enabled (works from anywhere)
# Web-scraper
