# Collmbo

<p align="center">
  <img src="https://github.com/user-attachments/assets/b13da1c7-5d2f-4ad3-8c5b-9ef4e500deb8">
</p>

**A Slack bot that lets you choose your preferred LLM using LiteLLM.** Pronounced the same as "Colombo".

> ![](https://github.com/user-attachments/assets/a377b868-3673-4798-b415-44e674cf7ae6)

## Quick Start

Before running Collmbo, you need to [create a Slack app](https://github.com/iwamot/collmbo/wiki/Creating-a-Slack-App) and obtain the required tokens:

- App-level token (`xapp-1-...`)
- Bot token (`xoxb-...`)

Then, pick your favorite model from [LiteLLM's supported models](https://docs.litellm.ai/docs/providers) and run Collmbo. Here are some examples:

### OpenAI (gpt-4o)

```sh
$ cat env
SLACK_APP_TOKEN=xapp-1-...
SLACK_BOT_TOKEN=xoxb-...
OPENAI_API_KEY=sk-...
LITELLM_MODEL=gpt-4o

$ docker run -it --env-file ./env ghcr.io/iwamot/collmbo:latest-slim
```

### Azure OpenAI (gpt-4-0613)

```sh
$ cat env
SLACK_APP_TOKEN=xapp-1-...
SLACK_BOT_TOKEN=xoxb-...
AZURE_API_KEY=...
AZURE_API_BASE=...
AZURE_API_VERSION=...
LITELLM_MODEL=azure/<your_deployment_name>
LITELLM_MODEL_TYPE=azure/gpt-4-0613

$ docker run -it --env-file ./env ghcr.io/iwamot/collmbo:latest-slim
```

### Gemini - Google AI Studio (Gemini 1.5 Flash)

```sh
$ cat env
SLACK_APP_TOKEN=xapp-1-...
SLACK_BOT_TOKEN=xoxb-...
GEMINI_API_KEY=...
LITELLM_MODEL=gemini/gemini-1.5-flash

$ docker run -it --env-file ./env ghcr.io/iwamot/collmbo:latest-slim
```

### Amazon Bedrock (Claude 3.5 Sonnet v2)

```sh
$ cat env
SLACK_APP_TOKEN=...
SLACK_BOT_TOKEN=...
LITELLM_MODEL=bedrock/anthropic.claude-3-5-sonnet-20241022-v2:0

# You can specify a Bedrock region if it's different from your default AWS region
AWS_REGION_NAME=us-west-2

# You can use your access key for authentication, but IAM roles are recommended
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...

$ docker run -it --env-file ./env ghcr.io/iwamot/collmbo:latest-full
```

*Note: `full` flavor images include boto3.*

## Features

- **[Tools (Function Calling)](https://github.com/iwamot/collmbo/wiki/Tools-(Function-Calling))** – Extends functionality with function calling.
- **[Custom callbacks](https://github.com/iwamot/collmbo/wiki/Custom-callbacks)** – Hooks into requests and responses for custom processing.
- **[Redaction](https://github.com/iwamot/collmbo/wiki/Redaction)** – Masks sensitive information before sending requests.
- **[Slack-friendly formatting](https://github.com/iwamot/collmbo/wiki/Slack%E2%80%90friendly-formatting)** – Formats messages for better readability in Slack.
- **[Image input](https://github.com/iwamot/collmbo/wiki/Image-input)** – Enables AI models to analyze uploaded images.
- **[PDF input](https://github.com/iwamot/collmbo/wiki/PDF-input)** – Enables AI models to analyze uploaded PDFs.

## Configuration

Collmbo runs with default settings, but you can customize its behavior by [setting optional environment variables](https://github.com/iwamot/collmbo/wiki/Optional-Settings).

## Contributing

Questions and suggestions welcome! Feel free to open an issue.

## Related Projects

- [seratch/ChatGPT-in-Slack](https://github.com/seratch/ChatGPT-in-Slack) – The original project by @seratch.

## License

**The code** in this repository is licensed under the **MIT License**.

**The Collmbo icon** (`assets/icon.png`) is licensed under **[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)**. For example, you may use it as a Slack profile icon.
