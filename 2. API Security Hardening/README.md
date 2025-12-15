# 2. API Security Hardening (Node.js + Express)

## 🎯 Goal
Harden an Express.js API by implementing:

- Rate limiting to prevent brute-force attacks
- Proper CORS allowlist configuration
- API key–based authentication for protected endpoints

---

## 🛠 Tech Stack
- Node.js + Express
- dotenv
- express-rate-limit
- cors

---

## 🚀 Project Setup

### Install dependencies
```bash
npm init -y
npm install express dotenv express-rate-limit cors
Run the server
bash

node src/server.js
```
🔐 Implemented Security Controls
1️⃣ Rate Limiting (Brute-Force Protection)
A global rate limiter is applied to all requests.

Configuration

Time window: 15 minutes

Limit: 100 requests per IP

Result

Excessive requests return 429 Too Many Requests

Proof

Screenshot showing multiple requests to /health resulting in 429

2️⃣ CORS Allowlist (Unauthorized Origin Blocking)
CORS is configured using a strict allowlist.

Behavior

Requests from allowed origins succeed

Requests from unauthorized origins are blocked
```
Test Command

curl -i -H "Origin: http://evil.com" http://localhost:3000/health
```
Result

Returns 403 Forbidden

Error message: CORS Forbidden: Origin not allowed

Proof

Screenshot showing allowed origin request

Screenshot showing blocked origin (http://evil.com)

3️⃣ API Key Authentication (Protected Endpoints)
Secure endpoints are protected using API key authentication.

Authentication Method

Header: x-api-key

Value loaded from .env

Protected Endpoint
```
http
GET /secure
```
Example Request

```bash
curl -H "x-api-key: internship-secret-key" http://localhost:3000/secure
```
Results

Without API key → 401 Unauthorized

With valid API key → Success response

Proof

Screenshot without API key

Screenshot with valid API key

📡 API Endpoints
Public
```
http
GET /health
```
Response:
```
{ "status": "ok" }
Protected
http

GET /secure
Requires header:

css

x-api-key
```
📸 Evidence Collected
Project setup & folder structure

Rate limiting test (429 Too Many Requests)

CORS allowlist test (allowed vs blocked origin)

API key authentication test (unauthorized vs authorized)

📝 Notes
ICMP traffic (ping) may be blocked on phone hotspot networks.

All verification was performed using HTTP-based testing (curl), which is sufficient for API security validation.
