# Tokonomics — Integration Examples

Code examples showing how to use [Tokonomics](https://tokonomics.ca) as an AI cost metering proxy with any language and any LLM provider.

## What is Tokonomics?

[Tokonomics](https://tokonomics.ca) is a budget-first AI cost metering proxy. One URL change gives you real-time cost tracking, budget alerts, and hard spending caps across OpenAI, Anthropic, DeepSeek, Gemini, Mistral, and more.

**Free plan:** 100 API calls/month, basic analytics
**Pro plan:** $49/mo — unlimited calls, hard caps, Slack/Teams alerts

## Quick Start

Replace your LLM base URL with Tokonomics and add your metering key:

### Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://tokonomics.ca/proxy/openai",
    api_key="mk_your_metering_key_here",
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hello!"}],
    extra_headers={"X-Metering-Tags": '{"team":"growth","feature":"chatbot"}'}
)

import OpenAI from "openai";

const client = new OpenAI({
  baseURL: "https://tokonomics.ca/proxy/openai",
  apiKey: "mk_your_metering_key_here",
});

const response = await client.chat.completions.create({
  model: "gpt-4o",
  messages: [{ role: "user", content: "Hello!" }],
});

curl https://tokonomics.ca/proxy/openai/chat/completions \
  -H "Authorization: Bearer mk_your_metering_key_here" \
  -H "X-Metering-Tags: {\"team\":\"growth\"}" \
  -H "Content-Type: application/json" \
  -d '{"model":"gpt-4o","messages":[{"role":"user","content":"Hello!"}]}'

$ch = curl_init('https://tokonomics.ca/proxy/openai/chat/completions');
curl_setopt_array($ch, [
    CURLOPT_POST => true,
    CURLOPT_HTTPHEADER => [
        'Authorization: Bearer mk_your_metering_key_here',
        'Content-Type: application/json',
        'X-Metering-Tags: {"team":"backend"}',
    ],
    CURLOPT_POSTFIELDS => json_encode([
        'model' => 'gpt-4o',
        'messages' => [['role' => 'user', 'content' => 'Hello!']],
    ]),
    CURLOPT_RETURNTRANSFER => true,
]);
$response = curl_exec($ch);


Supported Providers
Provider	Proxy URL
OpenAI	https://tokonomics.ca/proxy/openai
Anthropic	https://tokonomics.ca/proxy/anthropic
DeepSeek	https://tokonomics.ca/proxy/deepseek
Google Gemini	https://tokonomics.ca/proxy/gemini
Mistral	https://tokonomics.ca/proxy/mistral
Groq	https://tokonomics.ca/proxy/groq
xAI (Grok)	https://tokonomics.ca/proxy/xai
Features
Budget alerts — Email, Slack, or Teams notifications before you overspend
Hard spending caps — Block requests when budget is hit (429 response)
Per-feature cost breakdown — Custom tags for team, feature, environment
Works with any language — Python, Node.js, PHP, Go, Rust, Ruby, cURL
No SDK required — Just change your base URL
Links
Website: tokonomics.ca
Documentation: tokonomics.ca/docs
Blog: tokonomics.ca/blog
Status: tokonomics.ca/status
