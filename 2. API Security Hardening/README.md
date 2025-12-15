# 2. API Security Hardening (Node.js + Express)

## Goal
Harden an Express API by implementing:
1) Rate limiting (express-rate-limit)
2) Proper CORS allowlist configuration
3) API key protection for secure endpoints

---

## Tech Stack
- Node.js + Express
- dotenv
- express-rate-limit
- cors

---

## Project Setup
### Install dependencies
```bash
npm init -y
npm i express dotenv express-rate-limit cors
```

Run server
node src/server.js

Implemented Security Controls
1) Rate Limiting (Brute-force protection)

Added a global limiter:

Window: 15 minutes

Max: 100 requests per IP

Proof (screenshot):

Multiple requests to /health eventually return 429 Too Many Requests

2) CORS Allowlist (Block unauthorized origins)

Configured CORS allowlist (allowed origins only)

Tested by sending a fake Origin header

Proof (screenshots):

Allowed origin request succeeds

Blocked origin (example: http://evil.com) is rejected with CORS blocked: origin not allowed

3) API Key Authentication (Protect secure endpoints)

Implemented API key middleware using request header x-api-key

Protected route: /secure

How it works

Request must include:

x-api-key: internship-secret-key (matches .env)

Proof (screenshots):

Without API key → Unauthorized

With API key → Success response

API Endpoints
Public

GET /health

Returns { "status": "ok" }

Protected

GET /secure

Requires header x-api-key

Example:

curl -H "x-api-key: internship-secret-key" http://localhost:3000/secure

Screenshots Collected (Evidence)

Setup commands & folder structure

Rate limit test (429)

CORS allowlist config (allowed vs blocked origin)

API key test (unauthorized vs authorized)

Notes

Using a phone hotspot may block ICMP (ping), so HTTP-based tests (curl) were used for verification.
