---
description: Find trending tweets and generate engaging content for posting or replying via X/Twitter API
trigger: When user wants to find hot tweets, write engaging tweets, or post/reply via Twitter API
---

# Twitter Engage

## Purpose

Help users find trending high-engagement tweets in their area of interest, craft viral tweet content or strategic replies, and optionally post them via the X/Twitter API.

## Instructions

### Phase 1: Clarify Requirements

1. Ask the user for their **topic of interest** (AI/Tech, Crypto/Web3, Business, General trending)
2. Ask whether they want to:
   - **Write a new tweet** (find hot topics to reference)
   - **Reply to an existing tweet** (find high-exposure tweets to comment on)
   - **Both**
3. Ask if they have Twitter API credentials for automated posting

### Phase 2: Find Trending Content

1. Use **WebSearch** to find current trending topics and viral tweets in the user's area of interest
2. Search multiple sources:
   - `site:x.com` for direct tweet links
   - Tech news sites (TechCrunch, The Verge, 36Kr, etc.) for context
   - Search for specific high-follower accounts in the relevant domain
3. Prioritize tweets/topics that are:
   - **Time-sensitive** (happened today or yesterday)
   - **Controversial** (generates debate and replies)
   - **High engagement** (from accounts with large followings)
4. Try to find **direct tweet URLs** (x.com/user/status/ID) whenever possible

### Phase 3: Craft Content

#### For new tweets (reference/quote style):
- Use a **hook → context → hot take → CTA** structure
- Include a controversial or thought-provoking angle
- End with an open question to drive replies
- Keep under 280 characters if possible, or use thread format
- Suggest relevant hashtags

#### For replies/comments:
- Use **"acknowledge → add value → provoke discussion"** pattern
- Add technical details or insider knowledge to stand out
- Include a question at the end to drive sub-threads
- Avoid pure criticism — "first praise, then challenge" works best

### Phase 4: Post via API (if credentials available)

#### Authentication Requirements

Twitter API requires **OAuth 1.0a User Context** for posting. A Bearer Token alone is NOT sufficient.

**Required credentials (all 4):**
- API Key (Consumer Key)
- API Secret (Consumer Secret)
- Access Token (user-level)
- Access Token Secret (user-level)

**Important checks before posting:**
- App permissions must be set to **"Read and Write"** (not Read Only)
- After changing permissions, Access Token must be **regenerated**
- Free tier API may NOT support posting (returns 402 CreditsDepleted)

#### Posting Code

Use Python with `requests_oauthlib`:

```python
from requests_oauthlib import OAuth1Session
import json

oauth = OAuth1Session(
    consumer_key,
    client_secret=consumer_secret,
    resource_owner_key=access_token,
    resource_owner_secret=access_token_secret,
)

# Post a new tweet
payload = {"text": "Your tweet content here"}

# Reply to an existing tweet
payload = {
    "text": "Your reply content here",
    "reply": {
        "in_reply_to_tweet_id": "TARGET_TWEET_ID"
    }
}

response = oauth.post("https://api.twitter.com/2/tweets", json=payload)
```

#### Environment Setup

```bash
python3 -m venv /tmp/twitter_env
source /tmp/twitter_env/bin/activate
pip install requests requests_oauthlib
```

#### Common Errors and Solutions

| HTTP Code | Error | Solution |
|-----------|-------|----------|
| 403 | `Unsupported Authentication` | Need OAuth 1.0a, not Bearer Token |
| 403 | `oauth1-permissions` | App is Read Only — change to Read and Write, then regenerate Access Token |
| 402 | `CreditsDepleted` | Free tier limit reached — upgrade to Basic ($100/mo) or wait for monthly reset |
| 429 | `Too Many Requests` | Rate limited — wait and retry |

### Phase 5: Confirm Before Posting

**ALWAYS show the user the final content and target tweet before posting.** Never auto-post without explicit confirmation. Present:

1. The target tweet URL (for replies)
2. The exact text to be posted
3. Ask for approval or modifications

## X/Twitter API Tier Comparison

| Feature | Free | Basic ($100/mo) |
|---------|------|-----------------|
| Read tweets | Limited | 10,000/mo |
| Post tweets | ~1,500/mo (often unavailable) | 3,000/mo |
| Search | Not available | Available |
| Trends | Not available | Available |

## Content Strategy Tips

- **Best posting times**: 9-11 AM EST (US morning) for global reach
- **Controversy drives engagement**: Pick a side on hot debates
- **Technical details add credibility**: Include specific facts (model names, parameter counts, config files)
- **Questions drive replies**: Always end with an open question
- **"First praise, then challenge"**: More effective than pure criticism

## Example Usage

```
/twitter-engage
```

Then follow the interactive prompts to:
1. Choose your topic area
2. Get trending tweet recommendations with links
3. Get draft content for posting or replying
4. Optionally post via API

## Notes

- Twitter API free tier is very limited; manual posting may be more practical
- Always comply with X's automation rules: no bulk posting, no spam, no fake engagement
- Credentials should never be hardcoded in shared code — use environment variables
- Tweet URLs format: `https://x.com/{username}/status/{tweet_id}`
- Monthly credit reset day can be checked via `GET /2/usage/tweets`
