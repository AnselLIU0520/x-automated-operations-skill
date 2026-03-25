# X Automated Operations Skill 2.0

<div align="center">

![X API](https://img.shields.io/badge/X%20API-v2-blue)
![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

**Automated X/Twitter Operations for AI & Tech Domain - Search, Engage, Create, Report**

</div>

## 🎯 What This Skill Does

Tired of manually tracking AI developments on X? This skill automates your daily X operations, specifically designed for the AI/ML, tech investment, and startup ecosystem.

### Real-World Scenarios

#### 🏢 **For AI Startup Founders**
*"I need to stay on top of what Sam Altman, Andrej Karpathy, and other AI leaders are talking about, but I don't have time to scroll through X all day."*

**→ This skill automatically:**
- Searches for the latest tweets from AI leaders you care about
- Engages with relevant content (likes, retweets)
- Posts thoughtful commentary based on trending topics
- Sends you a digest on Feishu so you're always informed

#### 📈 **For Tech Investors**
*"I need to monitor AI investment trends and identify emerging opportunities without manual tracking."*

**→ This skill automatically:**
- Tracks tweets from top VCs (a16z, Sequoia, Y Combinator)
- Analyzes sentiment around AI funding announcements  
- Identifies trending technologies and startups
- Provides daily intelligence reports

#### 🎓 **For AI Researchers & Engineers**
*"I want to participate in technical discussions but struggle to find the right conversations."*

**→ This skill automatically:**
- Finds technical discussions about LLMs, transformers, new architectures
- Engages with peer researchers
- Shares your insights at optimal times
- Builds your professional presence

## ✨ Core Features

### 🔍 **Intelligent Discovery**
- **Targeted Search**: Focuses on three key account types:
  - **AI Companies**: OpenAI, Anthropic, Google AI, Microsoft
  - **Tech Influencers**: Sam Altman, Andrej Karpathy, Yann LeCun, Andrew Ng
  - **Investors & Leaders**: Garry Tan, Paul Graham, Naval Ravikant
- **Smart Filtering**: Excludes spam, retweets, and irrelevant content
- **Trend Analysis**: Identifies emerging topics from search results

### 🤝 **Strategic Engagement**
- **Likes**: 5 high-quality tweets daily
- **Retweets**: 5 valuable insights to share  
- **Comments**: Intelligent responses (with graceful degradation)
- **Original Content**: 1 thoughtful tweet ending with a question

### 📊 **Automated Reporting**
- **Feishu Integration**: Structured daily reports
- **Performance Metrics**: Success rates, engagement stats
- **Trend Insights**: What's hot in AI today
- **Actionable Intelligence**: Not just data, but insights

### 🔒 **Enterprise-Grade Reliability**
- **Error Handling**: Automatic retries and fallbacks
- **Rate Limit Management**: Intelligent pacing to avoid blocks
- **Security First**: No hardcoded credentials, environment variables only
- **Permission Diagnostics**: Tools to fix common API permission issues

## 🚀 Quick Start

### Prerequisites
- Node.js 16+ 
- OpenClaw environment
- X Developer Account with API access
- (Optional) Feishu account for daily reports

### Installation

```bash
# Clone the repository
git clone https://github.com/AnselLIU0520/x-automated-operations-skill
cd x-automated-operations-skill

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
```

### Configuration

Edit `.env` file with your credentials:

```env
# X API Credentials (get from https://developer.twitter.com)
X_BEARER_TOKEN=your_bearer_token_here
X_CONSUMER_KEY=your_consumer_key_here
X_CONSUMER_SECRET=your_consumer_secret_here
X_ACCESS_TOKEN=your_access_token_here
X_ACCESS_TOKEN_SECRET=your_access_token_secret_here
X_USER_ID=your_user_id_here

# Optional: Proxy settings (if needed)
# HTTPS_PROXY=http://127.0.0.1:17890

# Optional: Feishu Webhook for daily reports
# FEISHU_WEBHOOK=https://www.feishu.cn/flow/api/trigger-webhook/your_id_here
```

### Getting X API Permissions (Critical!)

90% of issues come from incorrect permissions. Follow these steps:

1. **Apply for X Developer Account** at https://developer.twitter.com
2. **Create a new Application**
3. **Set App Permissions to "Read and Write"** (not "Read only")
4. **Generate API Keys and Tokens**
5. **Use our OAuth tools if needed**:
   ```bash
   # Generate authorization URL
   node scripts/generate_oauth_url.js
   
   # Authorize, get PIN, then:
   node scripts/get_new_token.js <PIN_CODE>
   ```

### Testing Your Setup

```bash
# Test permissions and connectivity
node scripts/test_permissions.js

# Dry run (preview without posting)
node scripts/daily_operations.js --dry-run

# View what will happen:
# - Which tweets will be engaged with
# - What original content will be posted
# - What Feishu report will look like
```

### Daily Execution

```bash
# Run the full daily operations
node scripts/daily_operations.js

# Or schedule it (Linux/macOS crontab)
0 9,17 * * * cd /path/to/skill && node scripts/daily_operations.js >> logs/cron.log 2>&1
```

## 💬 Natural Language Commands for OpenClaw

Once installed, you can use these natural language commands:

### Daily Operations
- **"Run my daily X operations"**
- **"Check what's trending in AI today"**
- **"Engage with AI leaders on X"**
- **"Post my daily AI insights"**
- **"Send me the X intelligence report"**

### Testing & Diagnostics
- **"Test my X API permissions"**
- **"Check if my X credentials work"**
- **"Diagnose why comments aren't working"**
- **"Test the Feishu integration"**

### Configuration & Setup
- **"Help me set up X API permissions"**
- **"Generate OAuth authorization URL"**
- **"Update my X access token"**
- **"Configure my target accounts"**

### Content & Strategy
- **"What topics are trending in AI?"**
- **"Who should I follow in AI/ML?"**
- **"Suggest some engagement strategies"**
- **"Review my daily operation results"**

## 🏗️ Project Structure

```
x-automated-operations-skill/
├── README.md                 # This document
├── README_CN.md             # Chinese documentation
├── SKILL.md                 # OpenClaw skill definition
├── package.json             # Dependencies
├── .env.example             # Environment template
├── .gitignore              # Git ignore rules
├── lib/
│   └── client.js           # Enhanced X API client
├── config/
│   ├── targets.js          # Target account configuration
│   ├── keywords.js         # Search keywords
│   └── templates.js        # Content templates
├── scripts/
│   ├── daily_operations.js # Main operations script
│   ├── test_permissions.js # Permission diagnostics
│   ├── generate_oauth_url.js # OAuth authorization
│   ├── get_new_token.js    # Access token exchange
│   └── quick_security_check.js # Security audit
├── references/             # Guides and documentation
└── logs/                   # Execution logs (auto-generated)
```

## ⚙️ Customization

### Target Accounts
Edit `config/targets.js` to customize who you track:

```javascript
module.exports = {
  // AI Company Official Accounts
  official: ['OpenAI', 'AnthropicAI', 'GoogleAI', 'Microsoft'],
  
  // Tech Influencers & Researchers
  kols: ['sama', 'karpathy', 'ylecun', 'AndrewYNg'],
  
  // Investors & Industry Leaders
  leaders: ['gdb', 'paulg', 'naval', 'cdixon']
};
```

### Search Keywords
Edit `config/keywords.js` to customize search terms:

```javascript
module.exports = [
  // English Keywords
  'AI', 'artificial intelligence', 'machine learning',
  'large language model', 'LLM', 'GPT', 'AGI',
  
  // Chinese Keywords (for bilingual tracking)
  'AI大模型', '人工智能', '机器学习',
  '大语言模型', 'AGI', 'AIGC'
];
```

### Content Templates
Edit `config/templates.js` to customize your voice:

```javascript
module.exports = {
  // Original tweet templates (always end with a question)
  originalTweets: [
    "Noticing {trend} across multiple sources today. What's the most underrated implication for {sector}?",
    "{insight} suggests we're at an inflection point. How should {audience} prepare for what's next?"
  ],
  
  // Comment templates (engaging, not spammy)
  commentTemplates: [
    "Interesting perspective. How do you see this impacting adoption timelines?",
    "This aligns with what we're seeing. The key question is scalability."
  ]
};
```

## 🛠️ Troubleshooting

### Common Issues & Solutions

#### ❌ "All write operations return 401 error"
**Problem**: Access token doesn't have write permissions.

**Solution**:
```bash
# 1. Run diagnostics
node scripts/test_permissions.js

# 2. Check X Developer Portal
#    - Go to https://developer.twitter.com
#    - Find your app
#    - Ensure "App permissions" is "Read and Write"

# 3. If still "Read only", change to "Read and Write"
# 4. Regenerate access tokens
# 5. Update .env file
```

#### ❌ "Comments fail but likes/retweets work"
**Problem**: X has additional restrictions on comments.

**Solution**:
- The skill automatically degrades (failed comments become likes+retweets)
- Ensure you're only engaging with accounts that allow replies
- Avoid commenting on protected accounts
- Keep comments short and meaningful

#### ❌ "Rate limit exceeded (429 error)"
**Problem**: Too many API calls too quickly.

**Solution**:
- Increase `OPERATION_DELAY` in `.env` file
- Reduce number of daily interactions
- The skill already includes intelligent pacing

#### ❌ "Network/proxy connection issues"
**Problem**: Can't connect to X API.

**Solution**:
```env
# In .env file, configure proxy if needed:
HTTPS_PROXY=http://127.0.0.1:17890
```

## 📈 Best Practices

### Engagement Strategy
1. **Quality Over Quantity**: Better to engage meaningfully with 5 tweets than superficially with 50
2. **Consistency**: Daily engagement builds presence better than sporadic bursts
3. **Value Add**: Comments should provide insight, not just "nice post"
4. **Original Content**: Share unique perspectives, not just retweets

### Technical Recommendations
1. **Environment Variables**: Never commit `.env` to version control
2. **Regular Updates**: Check for X API changes quarterly
3. **Monitoring**: Review logs weekly to catch issues early
4. **Backup Configuration**: Keep backups of your custom configs

### Compliance & Ethics
1. **Follow X Rules**: Respect rate limits and terms of service
2. **Authentic Engagement**: Don't spam or use deceptive practices
3. **Transparency**: Be clear about automated engagement if asked
4. **Value Focus**: Aim to contribute to conversations, not just extract value

## 🔄 Version History

### v2.0 (2026-03-25) - Major Rewrite
- **Modular Architecture**: Separated lib/, config/, scripts/, references/
- **Enhanced Error Handling**: Retry logic, graceful degradation
- **Permission Diagnostics**: Complete toolset for API permission issues
- **OAuth 1.0a Tools**: generate_oauth_url.js and get_new_token.js
- **Comprehensive Documentation**: English and Chinese README
- **Security First**: No hardcoded credentials, security audit tools

### v1.x (Previous Version)
- Basic search and engagement functionality
- Simple error handling
- Limited documentation

## 🤝 Contributing

Found a bug? Have a feature request?

1. **Check Existing Issues** on GitHub
2. **Create New Issue** with detailed description
3. **Include Logs**: Run with `--debug` flag and include output
4. **Be Specific**: What happened vs what you expected

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built for the OpenClaw ecosystem
- Designed specifically for AI/tech domain operators
- Tested with real-world X API constraints
- Inspired by the need for better intelligence tools in fast-moving industries

---

**Ready to automate your X intelligence?** Start with `node scripts/test_permissions.js` to ensure everything's working, then schedule your first daily run!

**Questions?** Check the [Chinese documentation](README_CN.md) or create an issue on GitHub.