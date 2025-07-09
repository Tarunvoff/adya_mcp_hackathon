# MCP CODE-RESEARCH Server - Credentials & Environment Variables Guide

This guide explains all environment variables required or supported by the CODE-RESEARCH MCP server. Copy the provided `env.example` to `.env` and fill in your actual values.

---

## 🔑 GitHub API Configuration
- **GITHUB_TOKEN**: GitHub Personal Access Token (optional, for higher rate limits)
  - Get from: https://github.com/settings/tokens
  - Scopes needed: `public_repo` (for public repositories)
  - Without token: 60 requests/hour; With token: 5000 requests/hour

## 📦 npm Registry Configuration
- **NPM_TOKEN**: npm Registry Token (optional, for authenticated requests)
  - Get from: https://www.npmjs.com/settings/tokens
  - Search works without authentication, but token provides higher limits

## 💬 Stack Overflow OAuth Configuration
- **STACKOVERFLOW_CLIENT_ID**: Stack Overflow OAuth Client ID
  - Get from: https://stackapps.com/apps/oauth/register
- **STACKOVERFLOW_CLIENT_SECRET**: Stack Overflow OAuth Client Secret
  - Get from: https://stackapps.com/apps/oauth/register
- **STACKOVERFLOW_REDIRECT_URI**: Stack Overflow OAuth Redirect URI
  - Set this in your OAuth app configuration (e.g., http://localhost:3000/oauth/callback)
- **STACKOVERFLOW_ACCESS_TOKEN**: Stack Overflow Access Token
  - Get from: https://stackoverflow.com/users/account
  - Without OAuth: 300 requests/day (anonymous); With OAuth: higher limits

## ⚙️ Optional Configuration
- **NODE_ENV**: Node Environment (`development`/`production`)
- **LOG_LEVEL**: Log Level (`debug`, `info`, `warn`, `error`)
- **CACHE_TTL**: Cache TTL in seconds (default: 3600 = 1 hour)
- **CACHE_CHECK_PERIOD**: Cache check period in seconds (default: 600 = 10 minutes)
- **PORT**: Server port (default: 3000)
- **HOST**: Server host (default: localhost)
- **HTTP_PROXY/HTTPS_PROXY**: Proxy configuration (if needed)
- **RATE_LIMIT_REQUESTS_PER_MINUTE**: Requests per minute (default: 60)
- **RATE_LIMIT_REQUESTS_PER_HOUR**: Requests per hour (default: 1000)

## 📝 Notes
1. **GitHub Token**: Optional but recommended for higher API rate limits.
2. **npm Token**: Optional, search works without authentication.
3. **Stack Overflow OAuth**: Optional but recommended for higher rate limits.
4. **PyPI and MDN**: No authentication required (public APIs).
5. **Security**: Never commit your `.env` file to version control. Add `.env` to your `.gitignore` and use `env.example` for documentation.

---

## 📋 Example `.env` File
```env
# GitHub
GITHUB_TOKEN=your_github_personal_access_token_here

# npm
NPM_TOKEN=your_npm_token_here

# Stack Overflow
STACKOVERFLOW_CLIENT_ID=your_stackoverflow_client_id_here
STACKOVERFLOW_CLIENT_SECRET=your_stackoverflow_client_secret_here
STACKOVERFLOW_REDIRECT_URI=http://localhost:3000/oauth/callback
STACKOVERFLOW_ACCESS_TOKEN=your_stackoverflow_access_token_here

# Optional
NODE_ENV=development
LOG_LEVEL=info
CACHE_TTL=3600
CACHE_CHECK_PERIOD=600
PORT=3000
HOST=localhost
RATE_LIMIT_REQUESTS_PER_MINUTE=60
RATE_LIMIT_REQUESTS_PER_HOUR=1000
```

---

For more details, see the comments in `env.example` in the CODE-RESEARCH server directory.
