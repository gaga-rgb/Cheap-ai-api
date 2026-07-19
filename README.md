# Gemini AI Cloud

A hosted OpenAI-compatible and Google Developer API-compatible gateway for Google's Gemini, Gemma, Imagen,
 OpenAI GPT, DeepSeek, and Anthropic Claude AI models.

## 🚀 API Access & Free Credits

To access the API, simply sign up on our website:
👉 **[Visit the Website](https://ai.nikkco.org/)**

### 🎁 $5 Free Credits on Registering
Every new account receives **$5 in free credits** upon registration!

Because our hosted API pricing is **significantly cheaper than the official provider rates** (often up to 
several times cheaper), your **$5 free credit has massive buying power**—equivalent to a much larger amoun
t of credits if spent directly with the official providers. You can run millions of tokens of high-quality
 queries entirely for free!

---

## 🧭 Model Square & Pricing

Instead of keeping static tables in this document, our active model lineup and pricing are updated live on
 our platform:
👉 **[Explore the Model Square](https://ai.nikkco.org/pricing)**

We support a wide array of state-of-the-art models, including:
- **Google Gemini** (including standard, grounding/search, lite, image, and TTS variants)
- **Gemma** (lightweight instruction-tuned models)
- **Imagen** (cutting-edge image generation)
- **OpenAI GPT**
- **DeepSeek**
- **Anthropic Claude**

---

👉 **Join our [Discord Server](https://discord.gg/b9atsJEmAj)** to stay updated, get support, and connect 
with the community!

---

## 🛠️ Dual API Formats & Integration

Our platform is engineered with a multi-protocol gateway, allowing you to interface with Gemini, Gemma, an
d other models in two distinct formats:

### 1. OpenAI-Compatible API
Perfect for dropping into existing codebases, langchain, or tools designed for OpenAI.
- **Base URL:** `https://ai.nikkco.org/v1`
- **Auth Header:** `Authorization: Bearer <YOUR_API_KEY>`

**cURL Example:**
```bash
curl https://ai.nikkco.org/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-3.5-flash",
    "messages": [{"role": "user", "content": "Explain quantum entanglement in one paragraph."}]
  }'
```

**Python SDK:**
```python
from openai import OpenAI

client = OpenAI(
    base_url="https://ai.nikkco.org/v1",
    api_key="YOUR_API_KEY"
)

response = client.chat.completions.create(
    model="gemini-3.5-flash",                                                                             
    messages=[{"role": "user", "content": "Hello!"}]
)
print(response.choices[0].message.content)
```

**JavaScript SDK:**
```javascript
import OpenAI from 'openai';

const openai = new OpenAI({
    baseURL: 'https://ai.nikkco.org/v1',
    apiKey: 'YOUR_API_KEY'
});

const completion = await openai.chat.completions.create({
    model: 'gemini-3.5-flash',
    messages: [{ role: 'user', content: 'Hello!' }]
});
console.log(completion.choices[0].message.content);
```

---

### 2. Google Developer / Gemini API
Perfect for using official Google SDKs or calling native Gemini endpoints directly.
- **Base URL:** `https://ai.nikkco.org/v1beta`
- **Auth Parameter:** `?key=<YOUR_API_KEY>`

**cURL Example:**
```bash
curl 'https://ai.nikkco.org/v1beta/models/gemini-3.5-flash:generateContent?key=YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{
    "contents": [
      {
        "parts": [
          {"text": "Explain quantum entanglement in one paragraph."}
        ]
      }
    ]
  }'
```

---

## 🌟 Full Official Feature Support

All Gemini, Gemma, and Imagen models running on our platform **support every capability they officially su
pport** out-of-the-box:

- 👁️ **Multimodal & Vision** – Process images, video, and audio payloads.
- 🛠️ **Tool Calling & Advanced Integrations** – Supports official tool structures, custom function calling,
 and advanced built-in tools such as **Google Maps** (supported by `gemini-3.1-pro-preview` and other capa
ble models).
- 🎨 **Image Generation** – High-fidelity generations via official Imagen models.

---

## 🌐 Google Search Grounding & `:search` Models

Google Search grounding can be enabled in two ways depending on the API format you use:

1. **Google Developer API (v1beta):** Search grounding works natively using the standard official structur
e (passing the search tool parameter) on standard models without needing any special suffix.
2. **OpenAI-Compatible API:** Since typical OpenAI clients cannot easily pass custom Google Search paramet
ers, we host dedicated **`:search` suffix models** (such as `gemini-3.5-flash:search`). Simply querying a 
model with the `:search` suffix activates Google Search grounding automatically through standard OpenAI SD
Ks without any extra configuration.

---

## API Endpoints

| Endpoint | Protocol | Description |
|----------|----------|-------------|
| `GET /v1/models` | OpenAI | List all available models |
| `POST /v1/chat/completions` | OpenAI | Create a chat completion |
| `POST /v1beta/models/{model}:generateContent` | Gemini | Generate content via native Gemini protocol |

## Support

For issues, questions, or updates, join our **[Discord Server](https://discord.gg/b9atsJEmAj)**.
