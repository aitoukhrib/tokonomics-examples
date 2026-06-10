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
