# MagicBox Public Posts API

This repository provides documentation and a reference implementation for the **MagicBox Public Posts API**.

The API allows developers, analysts, and researchers to retrieve **public, approved posts** from the MagicBox social platform in a clean, structured, and read-only JSON format.

---

## 🌐 Base URL

https://magicbox.mg/api/


## 📌 Endpoint: Get Public Posts

### URL
GET /public_posts.php


### Description
Returns a paginated list of public posts, ordered from newest to oldest.

---

## 🔎 Query Parameters

| Parameter | Type | Description |
|---------|------|-------------|
| `page` | Integer | Page number (default: `1`) |
| `limit` | Integer | Number of posts per page (default: `20`, max: `100`) |

> ⚠️ Requests with `limit` greater than `100` are automatically capped for performance and stability.

---

## ✅ Example Requests

### Default request
```bash
curl "https://magicbox.mg/api/public_posts.php"
Paginated request
bash
Copy code
curl "https://magicbox.mg/api/public_posts.php?page=2&limit=20"
Maximum allowed limit
bash
Copy code
curl "https://magicbox.mg/api/public_posts.php?page=1&limit=100"
📦 Example Response
json
Copy code
{
  "status": "success",
  "page": 1,
  "limit": 20,
  "total": 15342,
  "total_pages": 768,
  "has_more": true,
  "posts": [
    {
      "id": 9321,
      "post_id": 9321,
      "post_type": "article",
      "time": "2025-12-16 09:45:12",
      "title": "AI in Healthcare",
      "description": "This article discusses recent advances in AI...",
      "tags": ["AI", "Health"]
    }
  ]
}
🧾 Response Fields
Top-Level Fields
Field	Description
status	Request status
page	Current page
limit	Posts per page
total	Total public posts
total_pages	Total pages available
has_more	Indicates more pages
posts	Array of post objects

Post Object Fields
Field	Description
id / post_id	Unique post identifier
post_type	Type of post (e.g., text, article)
time	Post creation timestamp
title	Article title (empty if not an article)
description	Clean text content (HTML removed)
tags	List of tags
