2. API Security Hardening (Node.js + Express)
🎯 Goal

Harden an Express.js API by implementing:

Rate limiting to prevent brute-force attacks

Proper CORS allowlist configuration

API key–based authentication for protected endpoints

🛠 Tech Stack

Node.js + Express

dotenv

express-rate-limit

cors

🚀 Project Setup

Install dependencies:

npm init -y
npm install express dotenv express-rate-limit cors


Run the server:

node src/server.js

🔐 Implemented Security Controls
1️⃣ Rate Limiting (Brute-Force Protection)

A global rate limiter is applied to all requests.

Configuration

Time window: 15 minutes

Limit: 100 requests per IP

Result

Excessive requests return HTTP 429 – Too Many Requests

Evidence

Screenshot showing repeated requests to /health resulting in 429

2️⃣ CORS Allowlist (Unauthorized Origin Blocking)

CORS is configured using a strict allowlist.

Behavior

Requests from allowed origins succeed

Requests from unauthorized origins are blocked

Test Case

curl -i -H "Origin: http://evil.com" http://localhost:3000/health


Result

Returns HTTP 403 – Forbidden

No stack trace or internal error leakage

Evidence

Screenshot showing allowed origin access

Screenshot showing blocked origin (http://evil.com)

3️⃣ API Key Authentication (Protected Endpoints)

Secure endpoints are protected using an API key middleware.

Authentication Method

Header: x-api-key

Value loaded from .env

Protected Endpoint

GET /secure


Example Request

curl -H "x-api-key: internship-secret-key" http://localhost:3000/secure


Results

Without API key → 401 Unauthorized

With valid API key → Success response

Evidence

Screenshot without API key

Screenshot with valid API key

📡 API Endpoints
Public
GET /health
Response: { "status": "ok" }

Protected
GET /secure
Requires header: x-api-key

📸 Evidence Collected

Project setup & folder structure

Rate limiting test (429 response)

CORS allowlist test (allowed vs blocked origin)

API key authentication (unauthorized vs authorized)

📝 Notes

ICMP traffic (ping) was blocked due to phone hotspot networking.

All verification was performed using HTTP-based testing (curl), which is sufficient for API security validation.
