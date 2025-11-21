# DecoyAI

**Stop bot scrapers in 5 minutes. One-line JavaScript. Invisible honeypots. Real-time alerts.**

![Status](https://img.shields.io/badge/status-beta-yellow) ![License](https://img.shields.io/badge/license-MIT-green)

---

## What is DecoyAI?

DecoyAI deploys invisible honeypot traps on your website to detect and analyze bot activity—without impacting real users or breaking your site.

Paste a single line of JavaScript. Watch bots trigger your traps. Get alerts via email, Slack, or webhook. Export reports. That's it.

Perfect for:
- **E-commerce sites** protecting against price scrapers and credential stuffing
- **SaaS platforms** monitoring automated attacks and suspicious behavior  
- **Content sites** tracking AI crawlers and unauthorized bots
- **Developers** building secure applications with minimal overhead

---

## Quick Start

### 1. Sign up (free)
[Start free at DecoyAI](https://decoyai.app) — no credit card required.

### 2. Copy your snippet
In your dashboard, copy your unique JavaScript snippet:

```html
<script src="https://cdn.decoyai.app/trap.min.js" data-site-id="your-site-id"></script>
```

### 3. Paste into your website
Add the snippet to your HTML (footer or `<head>`):

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Your existing code -->
  </head>
  <body>
    <!-- Your existing code -->
    
    <!-- DecoyAI snippet -->
    <script src="https://cdn.decoyai.app/trap.min.js" data-site-id="your-site-id"></script>
  </body>
</html>
```

### 4. View detections
Real-time dashboard shows every bot triggered, with:
- Bot type & behavior
- Timestamp & location
- User agent & IP
- Decoy type (login trap, hidden link, form field)

### 5. Get alerts
Configure notifications:
- **Email** — immediate or daily digest
- **Slack** — real-time alerts in your workspace
- **Webhooks** — integrate with your own tools

---

## How It Works

DecoyAI injects invisible honeypot traps into your page:

1. **Hidden form fields** — bots auto-fill; real users don't see them
2. **Invisible links** — crawler-only URLs trigger when accessed
3. **Fake login forms** — credential stuffing attempts captured
4. **Mouse/focus events** — detects non-human interaction patterns

When a bot interacts with a trap, DecoyAI logs it with full context (timestamp, user agent, behavior). Real users never know it's there.

---

## Features

✅ **Zero UX Impact** — Invisible traps, CSS-hidden, zero disruption  
✅ **One-Line Install** — Copy/paste snippet, works everywhere  
✅ **Real-Time Dashboard** — See what bots do, when, and where  
✅ **Flexible Alerts** — Email, Slack, webhooks, scheduled reports  
✅ **CSV Export** — Download raw data for analysis  
✅ **Multiple Decoys** — Login honeypots, hidden links, fake forms  
✅ **Observe-Only Mode** — No blocking, no IP collection (GDPR compliant)  

---

## Pricing

Start free. Pay only when you scale.

| Plan | Price | Decoys | Domains | Best For |
|------|-------|--------|---------|----------|
| **Free** | $0/mo | 5 | 2 | Testing + case studies |
| **Starter** | $79/mo | 25 | 3 | SMBs, solo sites |
| **Pro** | $199/mo | 100 | 10 | Growing SMBs, agencies |
| **Agency** | $699/mo | Unlimited | 50+ | Agencies, enterprises |

**Annual discount:** Save 20% when paying yearly.
- Starter: $760.80/year (save $190.20)
- Pro: $1,912.80/year (save $478.20)
- Agency: $6,710.40/year (save $1,677.60)

[View pricing →](https://decoyai.app/pricing)

---

## FAQ

**Q: Will this affect my real users?**  
A: No. Traps are invisible, CSS-hidden, and only triggered by bot behavior. Real users never interact with them.

**Q: Can I upgrade anytime?**  
A: Yes. Free → Starter → Pro → Agency. Upgrade instantly, no lock-in.

**Q: What if I hit my detection limit?**  
A: We'll alert you. Auto-upgrade or pause alerts—your choice.

**Q: What about privacy?**  
A: Observe-only by default. We anonymize PII, comply with GDPR. No blocking, no unsolicited IP collection.

**Q: Does it work on Shopify/WordPress?**  
A: Yes. Paste the snippet anywhere. Native plugins coming Phase 2.

**Q: Can I export data?**  
A: CSV export on Starter+. Email/Slack alerts built-in.

**Q: Money-back guarantee?**  
A: 30 days, no questions asked (paid tiers).

---

## Installation Guides

### Standard HTML

Paste this in your `<head>` or before `</body>`:

```html
<script src="https://cdn.decoyai.app/trap.min.js" data-site-id="your-site-id"></script>
```

### WordPress

1. Go to **Settings → DecoyAI** (plugin coming Phase 2)
2. Enter your **Site ID** from your dashboard
3. Activate — honeypots live immediately

For now, use the snippet method in **Appearance → Theme File Editor** or **Code Snippets** plugin.

### Shopify

1. Go to **Online Store → Themes**
2. Click **Edit code**
3. Find `theme.liquid` or your main layout file
4. Paste the DecoyAI snippet in the `<head>` section
5. Save — traps activate on next store load

### React / Next.js

```jsx
useEffect(() => {
  const script = document.createElement('script');
  script.src = 'https://cdn.decoyai.app/trap.min.js';
  script.setAttribute('data-site-id', 'your-site-id');
  document.head.appendChild(script);
}, []);
```

### Vue.js

```vue
<template>
  <div></div>
</template>

<script>
export default {
  mounted() {
    const script = document.createElement('script');
    script.src = 'https://cdn.decoyai.app/trap.min.js';
    script.setAttribute('data-site-id', 'your-site-id');
    document.head.appendChild(script);
  }
}
</script>
```

---

## API Reference

### Dashboard API

Access your bot detection data programmatically.

**Base URL:** `https://api.decoyai.app/v1`

**Authentication:**
```
Authorization: Bearer YOUR_API_KEY
```

Get your API key from **Settings → API Keys** in your dashboard.

### Get Detections

```bash
curl -X GET "https://api.decoyai.app/v1/detections?siteId=your-site-id&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "data": [
    {
      "id": "det_abc123",
      "siteId": "site_xyz",
      "timestamp": "2025-01-15T10:32:15Z",
      "botType": "scraper",
      "decoyType": "hidden_link",
      "userAgent": "Mozilla/5.0 (Linux; compatible; Googlebot/2.1)",
      "ip": "66.249.66.1",
      "country": "US",
      "action": "triggered"
    }
  ],
  "pagination": {
    "limit": 50,
    "offset": 0,
    "total": 342
  }
}
```

### Get Stats

```bash
curl -X GET "https://api.decoyai.app/v1/stats?siteId=your-site-id&dateRange=7d" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "period": "7d",
  "totalDetections": 342,
  "uniqueBots": 18,
  "topBotTypes": ["scraper", "crawler", "bot"],
  "topDecoys": ["hidden_link", "login_honeypot", "form_field"],
  "detectionsByDay": [
    { "date": "2025-01-15", "count": 52 },
    { "date": "2025-01-14", "count": 48 }
  ]
}
```

### Webhooks

Forward detections to your own webhook in real-time.

**Setup:**
1. Go to **Settings → Webhooks**
2. Add endpoint (e.g., `https://yourapp.com/webhooks/decoyai`)
3. Choose events: `detection.triggered`, `detection.summary`

**Example payload:**
```json
{
  "event": "detection.triggered",
  "timestamp": "2025-01-15T10:32:15Z",
  "data": {
    "id": "det_abc123",
    "siteId": "site_xyz",
    "botType": "scraper",
    "decoyType": "hidden_link",
    "userAgent": "...",
    "ip": "..."
  }
}
```

[Full API docs →](https://docs.decoyai.app/api)

---

## Examples

### Example: Slack Alerts

Set up Slack notifications for detected scrapers:

1. Go to **Settings → Alerts**
2. Click **Add Slack Workspace**
3. Authorize DecoyAI
4. Choose channel & alert type (real-time or daily digest)
5. Done — get alerts as bots trigger

### Example: Export & Analyze

Export detection data for deeper analysis:

1. Go to **Dashboard**
2. Click **Export → CSV**
3. Select date range, decoy type, bot type
4. Download & analyze in Excel/Google Sheets

### Example: Custom Integration

Send detections to your own database:

```javascript
// In your webhook receiver (Node.js example)
app.post('/webhooks/decoyai', (req, res) => {
  const detection = req.body.data;
  
  // Log to your database
  db.detections.insert({
    timestamp: detection.timestamp,
    botType: detection.botType,
    ip: detection.ip,
    source: 'decoyai'
  });
  
  // Trigger custom action (e.g., block IP, alert team)
  if (detection.botType === 'credential_stuffer') {
    notifySecurityTeam(detection);
  }
  
  res.status(200).json({ success: true });
});
```

---

## Configuration

### Advanced Settings

Access configuration via dashboard:

**Decoy Types** — Enable/disable specific honeypots:
- ✅ Hidden form fields (catches auto-fillers)
- ✅ Invisible links (catches crawlers)
- ✅ Login honeypots (catches credential stuffing)
- ✅ Focus/click events (catches browser automation)

**Alert Rules** — Customize when you're notified:
- Minimum bot count per hour (e.g., alert if >10 detections)
- Specific bot types (e.g., only scrapers, not all bots)
- Quiet hours (e.g., no alerts 1am-6am)

**Observe-Only Mode** — Default. Change to:
- **Active Mode** (Phase 2) — block detected bots
- **Custom Mode** — return 403, redirect, or serve rate-limit

---

## Troubleshooting

**Q: I don't see any detections**
- Make sure snippet is deployed (check page source for `data-site-id`)
- Wait 5-10 minutes (initial sync can be slow)
- Check that site has actual bot traffic (test with curl or Postman)
- [Debug guide →](https://docs.decoyai.app/troubleshooting)

**Q: High false positives**
- Decoys may be catching legitimate scrapers (data aggregators, etc.)
- Adjust alert rules to filter bot types
- Use observe-only mode to monitor without blocking
- Open an issue with examples—we'll help tune

**Q: Snippet not loading**
- Check browser console for CORS errors
- Verify Site ID is correct (copy from dashboard)
- Clear cache & hard refresh (Ctrl+Shift+R)
- Try from a different network (check if corporate firewall blocking)

**Q: Performance impact?**
- Snippet is ~2KB minified. No noticeable page load impact.
- Bots reported asynchronously; no request blocking.

[More troubleshooting →](https://docs.decoyai.app/troubleshooting)

---

## Roadmap

**Phase 1 (Now):**
- ✅ JS snippet & honeypot traps
- ✅ Real-time dashboard
- ✅ Email/Slack alerts
- ✅ CSV export

**Phase 2 (Month 2-3):**
- 🔄 WordPress plugin
- 🔄 Scheduled PDF reports
- 🔄 Active blocking mode
- 🔄 Bot categorization (scraper, crawler, headless browser, etc.)

**Phase 3 (Month 4+):**
- 🔄 Shopify app
- 🔄 ML-powered bot detection
- 🔄 Enterprise features (custom SLAs, dedicated support)
- 🔄 IP blocklist integration (auto-feed to firewall)

---

## Contributing

We welcome bug reports, feature requests, and discussions!

- **Found a bug?** [Open an issue](https://github.com/decoyai/decoyai/issues)
- **Have an idea?** [Start a discussion](https://github.com/decoyai/decoyai/discussions)
- **Want to contribute?** We're not accepting PRs yet (beta phase), but reach out—we'd love your input.

---

## Status

🔧 **Beta** — Actively testing with early users. We'd love your feedback.

---

## License

MIT © 2025 DecoyAI. See [LICENSE](LICENSE) for details.

---

## Support

- **Docs:** [docs.decoyai.app](https://docs.decoyai.app)
- **Email:** support@decoyai.app
- **Twitter:** [@decoyai](https://twitter.com/decoyai)
- **Community:** [Slack](https://slack.decoyai.app)
- **Issues:** [GitHub Issues](https://github.com/decoyai/decoyai/issues)
