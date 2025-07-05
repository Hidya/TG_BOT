# 🎨 Telegram AI Image Generator Bot

A powerful Telegram bot that generates stunning images using A4F.co's FLUX.1-dev model. Built with Python and designed for easy deployment on Back4app.

## ✨ Features

- 🎯 Generate high-quality images from text descriptions
- 🚀 Powered by FLUX.1-dev model via A4F.co API
- 💬 User-friendly Telegram interface
- 🔄 Webhook support for production deployment
- 🛡️ Environment variable configuration for security
- 📱 Responsive design with HTML formatting

## 🚀 Quick Start

### 1. Get API Keys

**Telegram Bot:**
1. Message [@BotFather](https://t.me/BotFather)
2. Create new bot: `/newbot`
3. Save your bot token

**A4F.co API:**
1. Visit [A4F.co](https://www.a4f.co/)
2. Create account and get API key
3. Ensure access to `provider-3/FLUX.1-dev` model

### 2. Environment Setup

Create `.env` file:
```env
BOT_TOKEN=your_telegram_bot_token_here
A4F_API_KEY=your_a4f_api_key_here
WEBHOOK_URL=https://your-app-name.back4app.io
ENVIRONMENT=production
PORT=5000
```

### 3. Local Testing

```bash
# Install dependencies
pip install -r requirements.txt

# Set environment for local testing
export ENVIRONMENT=local

# Run bot
python main.py
```

## 🌐 Back4app Deployment

### Step 1: Back4app Setup
1. Create account on [Back4app](https://www.back4app.com/)
2. Create new app
3. Connect your GitHub repository

### Step 2: Environment Variables
In Back4app dashboard, set these variables:
- `BOT_TOKEN`: Your Telegram bot token
- `A4F_API_KEY`: Your A4F.co API key
- `WEBHOOK_URL`: Your Back4app app URL
- `ENVIRONMENT`: `production`
- `PORT`: `5000`

### Step 3: Deploy
1. Push code to GitHub
2. Back4app will auto-deploy
3. Set webhook: `POST /set_webhook`

## 📁 Project Structure

```
telegram-image-bot/
├── main.py              # Main bot application
├── requirements.txt     # Python dependencies
├── runtime.txt         # Python version
├── Procfile            # Back4app process configuration
├── .env.example        # Environment variables template
├── README.md           # This file
└── .gitignore         # Git ignore file
```

## 🤖 Bot Commands

- `/start` - Welcome message and introduction
- `/help` - Usage instructions and tips
- Send any text - Generate image from description

## 🔧 API Integration

### A4F.co Configuration
- **Model**: `provider-3/FLUX.1-dev`
- **Output Format**: PNG
- **Aspect Ratio**: 1:1 (square)
- **Quality**: 80%

### Example API Request
```json
{
  "model": "provider-3/FLUX.1-dev",
  "prompt": "A beautiful sunset over mountains",
  "num_outputs": 1,
  "aspect_ratio": "1:1",
  "output_format": "png",
  "output_quality": 80
}
```

## 📊 Usage Examples

**Simple prompts:**
- "A cute cat"
- "Beautiful landscape"
- "Modern city at night"

**Detailed prompts:**
- "A futuristic cyberpunk city with neon lights reflecting on wet streets"
- "A serene Japanese garden with cherry blossoms and a traditional bridge"
- "A photorealistic portrait of a person wearing vintage clothing"

## 🛠️ Development

### Local Development
```bash
# Clone repository
git clone https://github.com/yourusername/telegram-image-bot.git
cd telegram-image-bot

# Install dependencies
pip install -r requirements.txt

# Copy environment template
cp .env.example .env

# Edit .env with your keys
nano .env

# Run in local mode
export ENVIRONMENT=local
python main.py
```

### Testing Webhook
```bash
# Test webhook endpoint
curl -X POST https://your-app-name.back4app.io/set_webhook

# Health check
curl https://your-app-name.back4app.io/health
```

## 🔐 Security

- Never commit API keys to repository
- Use environment variables for sensitive data
- Keep bot token secure
- Monitor API usage and costs

## 📈 Monitoring

### Health Check
- Endpoint: `GET /health`
- Returns bot status

### Logs
- Check Back4app logs for errors
- Monitor API rate limits
- Track user usage

## 💰 Cost Considerations

- **Back4app**: Free tier available
- **A4F.co**: Pay per image generation
- **Telegram**: Free

## 🚨 Troubleshooting

### Common Issues

**Bot not responding:**
- Check BOT_TOKEN is correct
- Verify webhook is set properly
- Check Back4app logs

**Image generation fails:**
- Verify A4F_API_KEY is valid
- Check API quota/credits
- Monitor API response codes

**Webhook errors:**
- Ensure WEBHOOK_URL is correct
- Check SSL certificate
- Verify POST /set_webhook was called

### Debug Commands
```bash
# Check webhook status
curl https://api.telegram.org/bot<BOT_TOKEN>/getWebhookInfo

# Test API directly
curl -X POST https://api.a4f.co/v1/images/generations \
  -H "Authorization: Bearer <A4F_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{"model": "provider-3/FLUX.1-dev", "prompt": "test"}'
```

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [A4F.co](https://www.a4f.co/) for FLUX.1-dev model API
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot) library
- [Back4app](https://www.back4app.com/) for hosting platform