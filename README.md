# QR Code Generator API

REST API to generate QR codes in PNG, JPG, SVG, and EPS formats. Simple, fast, and reliable.

## Features

- Generate QR codes from URLs, text, emails, or phone numbers
- Multiple output formats: PNG, JPG, SVG, EPS
- Customizable size (default 300px)
- 100 requests/month on free tier
- 99.99% uptime, 780ms average latency
- Example Response:

![QR Code Sample](https://raw.githubusercontent.com/omkarcloud/assets/master/images/qrcode-api/qrcode.png)

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key, and use it in requests. 100 requests are free every month.

## Quick Start

```bash
curl -X GET "https://qrcode-api.omkar.cloud/qrcode?data=https://github.com&format=png" \
  -H "API-Key: YOUR_API_KEY" \
  --output qrcode.png
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://qrcode-api.omkar.cloud/qrcode",
    params={"data": "https://github.com", "format": "png"},
    headers={"API-Key": "YOUR_API_KEY"}
)

with open("qrcode.png", "wb") as f:
    f.write(response.content)
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";
import fs from "fs";

const response = await axios.get("https://qrcode-api.omkar.cloud/qrcode", {
    params: { data: "https://github.com", format: "png" },
    headers: { "API-Key": "YOUR_API_KEY" },
    responseType: "arraybuffer"
});

fs.writeFileSync("qrcode.png", response.data);
```

## API Reference

### Endpoint

```
GET https://qrcode-api.omkar.cloud/qrcode
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `data` | Yes | Content to encode (URL, text, email, phone number) |
| `format` | Yes | Output format: `png`, `jpg`, `jpeg`, `svg`, `eps` |
| `size` | No | Image size in pixels (default: 300, minimum: 1) |

### Supported Data Types

| Type | Example |
|------|---------|
| URL | `https://github.com` |
| Plain text | `Hello World` |
| Email | `mailto:email@example.com` |
| Phone | `tel:+1234567890` |

Max content length: ~2,900 characters. Shorter content = faster scanning.

## Examples

### Generate PNG QR code

```python
response = requests.get(
    "https://qrcode-api.omkar.cloud/qrcode",
    params={"data": "https://example.com", "format": "png"},
    headers={"API-Key": "YOUR_API_KEY"}
)

with open("website_qr.png", "wb") as f:
    f.write(response.content)
```

### Generate SVG for print

```python
response = requests.get(
    "https://qrcode-api.omkar.cloud/qrcode",
    params={"data": "https://example.com", "format": "svg"},
    headers={"API-Key": "YOUR_API_KEY"}
)

with open("website_qr.svg", "wb") as f:
    f.write(response.content)
```

### Custom size QR code

```python
response = requests.get(
    "https://qrcode-api.omkar.cloud/qrcode",
    params={"data": "https://example.com", "format": "png", "size": 500},
    headers={"API-Key": "YOUR_API_KEY"}
)

with open("large_qr.png", "wb") as f:
    f.write(response.content)
```

## Error Handling

```python
response = requests.get(
    "https://qrcode-api.omkar.cloud/qrcode",
    params={"data": "https://example.com", "format": "png"},
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    with open("qrcode.png", "wb") as f:
        f.write(response.content)
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 100 |
| Starter | $16 | 3,000 |
| Grow | $48 | 15,000 |
| Scale | $148 | 75,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about QR Code API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://www.omkar.cloud/l/qrcode-generator-api-github-whatsapp)

[![Contact Us on Email about QR Code API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](https://www.omkar.cloud/l/qrcode-generator-api-github-email)
