# Cheap Ai Api

A hosted OpenAI-compatible and Google Developer API-compatible gateway for Google's Gemini, Gemma, Imagen, OpenAI GPT, DeepSeek, Qwen and Claude AI models.
                                                                                         
## 🚀 API Access & Free Credits

To access the API, simply sign up on our website:
👉 **[Visit the Website](https://ai.nikkco.org/)**

### 🎁 $5 Free Credits on Registering
Every new account receives **$5 in free credits** upon registration!

Because our hosted API pricing is **significantly cheaper than the official provider rate
s** (often up to several times cheaper), your **$5 free credit has massive buying power**
—equivalent to a much larger amount of credits if spent directly with the official provid
ers. You can run millions of tokens of high-quality queries entirely for free!

---

## 🧭 Model Square & Pricing

Instead of keeping static tables in this document, our active model lineup and pricing ar
e updated live on our platform:
👉 **[Explore the Model Square](https://ai.nikkco.org/pricing)**

We support a wide array of state-of-the-art models, including:                           
- **Google Gemini** (including standard, grounding/search, lite, image, and TTS variants)
- **Gemma** (lightweight instruction-tuned models)
- **Imagen** (cutting-edge image generation)
- **OpenAI GPT**
- **DeepSeek**
- **Anthropic Claude**

---

👉 **Join our [Discord Server](https://discord.gg/b9atsJEmAj)** to stay updated, get supp
ort, and connect with the community!                                                     
                                                                                         
---
                                                                                         
## 🛠️ Dual API Formats & Integration                                                      
                                                                                         
Our platform is engineered with a multi-protocol gateway, allowing you to interface with 
Gemini, Gemma, and other models in two distinct formats:

1. **OpenAI-Compatible API** - Perfect for dropping into existing codebases, langchain, o
r tools designed for OpenAI.
2. **Google Developer / Gemini API** - Perfect for using official Google SDKs or calling 
native Gemini endpoints directly.

### 📚 Usage Instructions & Documentation

For complete API documentation, SDK integration guides, supported parameters, and code ex
amples (Python, Node.js, cURL, etc.), please refer to our official platform documentation
:

👉 **[View API Documentation & Usage Instructions](https://ai.nikkco.org/pricing)** *(Check the 
Docs/API section on our platform)*                                                       

---

## 🌟 Full Official Feature Support

All Gemini, Gemma, and Imagen models running on our platform **support every capability t
hey officially support** out-of-the-box:

- 👁️ **Multimodal & Vision** – Process images, video, and audio payloads.
- 🛠️ **Tool Calling & Advanced Integrations** – Supports official tool structures, custom 
function calling, and advanced built-in tools such as **Google Maps** (supported by `gemi
ni-3.1-pro-preview` and other capable models).
- 🎨 **Image Generation** – High-fidelity generations via official Imagen models.

---

## 🌐 Google Search Grounding & `:search` Models

Google Search grounding can be enabled in two ways depending on the API format you use:

1. **Google Developer API (v1beta):** Search grounding works natively using the standard 
official structure (passing the search tool parameter) on standard models without needing
 any special suffix.
2. **OpenAI-Compatible API:** Since typical OpenAI clients cannot easily pass custom Goog
le Search parameters, we host dedicated **`:search` suffix models** (such as `gemini-3.5-
flash:search`). Simply querying a model with the `:search` suffix activates Google Search
 grounding automatically through standard OpenAI SDKs without any extra configuration.

---

## Support

For issues, questions, or updates, join our **[Discord Server](https://discord.gg/b9atsJEmAj)**.
