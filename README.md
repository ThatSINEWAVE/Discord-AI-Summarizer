<div align="center">
 
# Discord AI Summarizer Bot

This Discord bot analyzes and summarizes conversations in a specified channel using AI, powered by OpenAI's GPT-3.5 model.

</div>

## Features

- **Summarization:** Automatically generates a summary of messages in a Discord channel.
- **Permission Control:** Only users with a specified role can invoke the summarization command.
- **Embeds:** Sends the summary as an embed message, including details like the number of messages analyzed and the time range.
- **Customizable AI Model:** By default, the bot uses `gpt-3.5-turbo`, but you can switch to `gpt-4` for a more in-depth analysis (at a higher API cost).

<div align="center">

## ☕ [Support my work on Ko-Fi](https://ko-fi.com/thatsinewave)

</div>

## Installation

To run the bot locally or on a server, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/discord-ai-summarizer.git
   cd discord-ai-summarizer
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Configure environment variables:

   Create a `.env` file in the root directory and add the following variables:

   ```dotenv
   REQUIRED_ROLE_ID=your_role_id_here
   OPENAI_API_KEY=your_openai_api_key_here
   DISCORD_TOKEN=your_discord_bot_token_here
   ```

4. Run the bot:

   ```bash
   python main.py
   ```

<div align="center">

## [Join my discord server](https://thatsinewave.github.io/Discord-Redirect/)

</div>

## Usage

Once the bot is running and added to your Discord server, users with the specified role can use the `/summarize` command in any channel to generate a summary.

### Command Usage

- `/summarize <channel_mention> <message_count>`: Summarizes the last `message_count` messages in the specified `channel_mention`.

### Example

To summarize the last 50 messages in a channel:

```
/summarize #general 50
```

## Customizing the AI Model

By default, the bot uses `gpt-3.5-turbo`, which is optimized for speed and cost efficiency. However, for a more detailed and nuanced analysis, you can change the model to `gpt-4` in `main.py`:

```python
response = bot.openai_client.chat.completions.create(
    model="gpt-4",  # Change "gpt-3.5-turbo" to "gpt-4" for better accuracy
    messages=[
        {
            "role": "system",
            "content": "You are a professional conversation analyst. Create a detailed summary of this Discord conversation.",
        },
        {
            "role": "user",
            "content": f"Analyze this conversation and provide a comprehensive summary:\n\n{conversation}",
        },
    ],
    temperature=0.5,
    max_tokens=2000,
)
```

### ⚠️ Note:
- **GPT-4 provides better, more context-aware summaries**, but **it costs more per API request**.
- Consider using GPT-3.5 for general use and switching to GPT-4 only when necessary.

## Contributing

If you'd like to contribute to this project, please fork the repository and create a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
