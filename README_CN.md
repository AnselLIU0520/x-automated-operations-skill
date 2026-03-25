# X自动化运营技能 2.0

<div align="center">

![X API](https://img.shields.io/badge/X%20API-v2-blue)
![OpenClaw 技能](https://img.shields.io/badge/OpenClaw-技能-green)
![许可证](https://img.shields.io/badge/许可证-MIT-yellow)

**AI大模型领域自动化运营工具 - 每日自动执行搜索、互动、发布、推送**

</div>

## 🎯 这个技能解决什么问题？

还在手动刷X跟踪AI动态？这个技能帮你自动化每日X运营，专为AI/机器学习、科技投资和创业生态设计。

### 真实使用场景

#### 🏢 **AI创业者/创始人**
*"我需要关注Sam Altman、Andrej Karpathy这些AI领袖在讨论什么，但没时间整天刷X。"*

**→ 这个技能自动帮你：**
- 搜索你关注的AI领袖最新推文
- 与相关内容互动（点赞、转发）
- 基于热点话题发布有见地的评论
- 通过飞书发送每日摘要，让你随时掌握动态

#### 📈 **科技投资者/分析师**
*"我需要监控AI投资趋势，发现新兴机会，但不想手动跟踪。"*

**→ 这个技能自动帮你：**
- 跟踪顶级风投的推文（a16z、红杉、Y Combinator）
- 分析AI融资公告的情绪倾向
- 识别趋势技术和创业公司
- 提供每日情报报告

#### 🎓 **AI研究员/工程师**
*"我想参与技术讨论，但很难找到合适的对话。"*

**→ 这个技能自动帮你：**
- 发现关于LLM、Transformer、新架构的技术讨论
- 与同行研究者互动
- 在最佳时机分享你的见解
- 建立专业形象

## ✨ 核心功能

### 🔍 **智能发现**
- **定向搜索**：聚焦三类关键账号：
  - **AI公司官方**：OpenAI、Anthropic、Google AI、Microsoft
  - **科技影响者**：Sam Altman、Andrej Karpathy、Yann LeCun、吴恩达
  - **投资者与领袖**：Garry Tan、Paul Graham、Naval Ravikant
- **智能过滤**：排除垃圾信息、转推和无关内容
- **趋势分析**：从搜索结果识别新兴话题

### 🤝 **策略性互动**
- **点赞**：每日5条高质量推文
- **转发**：每日5条有价值见解
- **评论**：智能回复（带优雅降级）
- **原创内容**：每日1条以问句结尾的深度推文

### 📊 **自动化报告**
- **飞书集成**：结构化日报推送
- **性能指标**：成功率、互动统计
- **趋势洞察**：今日AI热点
- **可操作情报**：不只是数据，更是洞察

### 🔒 **企业级可靠性**
- **错误处理**：自动重试和降级策略
- **频率控制**：智能节奏避免封禁
- **安全第一**：无硬编码凭证，全用环境变量
- **权限诊断**：修复常见API权限问题的工具

## 🚀 快速开始

### 环境要求
- Node.js 16+
- OpenClaw 环境
- X开发者账号（需要API权限）
- （可选）飞书账号用于日报推送

### 安装

```bash
# 克隆仓库
git clone https://github.com/AnselLIU0520/x-automated-operations-skill
cd x-automated-operations-skill

# 安装依赖
npm install

# 配置环境变量
cp .env.example .env
```

### 配置

编辑`.env`文件填入你的凭证：

```env
# X API 凭证（从 https://developer.twitter.com 获取）
X_BEARER_TOKEN=你的_bearer_token
X_CONSUMER_KEY=你的_consumer_key
X_CONSUMER_SECRET=你的_consumer_secret
X_ACCESS_TOKEN=你的_access_token
X_ACCESS_TOKEN_SECRET=你的_access_token_secret
X_USER_ID=你的_user_id

# 可选：代理设置（如果需要）
# HTTPS_PROXY=http://127.0.0.1:17890

# 可选：飞书Webhook用于日报推送
# FEISHU_WEBHOOK=https://www.feishu.cn/flow/api/trigger-webhook/你的_webhook_id
```

### 获取X API权限（关键！）

90%的问题都来自权限配置错误。按步骤操作：

1. **申请X开发者账号**：访问 https://developer.twitter.com
2. **创建新应用**
3. **设置应用权限为"Read and Write"**（不能是"Read only"）
4. **生成API密钥和令牌**
5. **如果需要，使用我们的OAuth工具**：
   ```bash
   # 生成授权URL
   node scripts/generate_oauth_url.js
   
   # 授权后获取PIN码，然后：
   node scripts/get_new_token.js <PIN码>
   ```

### 测试配置

```bash
# 测试权限和连接
node scripts/test_permissions.js

# 干运行（预览不实际发布）
node scripts/daily_operations.js --dry-run

# 查看将会发生什么：
# - 将与哪些推文互动
# - 将发布什么原创内容
# - 飞书报告将是什么样子
```

### 每日执行

```bash
# 运行完整的日常运营
node scripts/daily_operations.js

# 或定时执行（Linux/macOS crontab）
0 9,17 * * * cd /技能路径 && node scripts/daily_operations.js >> logs/cron.log 2>&1
```

## 💬 OpenClaw自然语言指令

安装后，你可以使用这些自然语言指令：

### 日常运营
- **"运行我的每日X运营"**
- **"查看今天AI领域有什么趋势"**
- **"与AI领袖在X上互动"**
- **"发布我的每日AI见解"**
- **"给我发送X情报报告"**

### 测试与诊断
- **"测试我的X API权限"**
- **"检查我的X凭证是否有效"**
- **"诊断为什么评论功能不工作"**
- **"测试飞书集成"**

### 配置与设置
- **"帮我设置X API权限"**
- **"生成OAuth授权URL"**
- **"更新我的X访问令牌"**
- **"配置我的目标账号"**

### 内容与策略
- **"AI领域什么话题在趋势中？"**
- **"我应该关注哪些AI/ML领域的人？"**
- **"建议一些互动策略"**
- **"查看我的日常运营结果"**

## 🏗️ 项目结构

```
x-automated-operations-skill/
├── README.md                 # 英文文档
├── README_CN.md             # 中文文档（本文档）
├── SKILL.md                 # OpenClaw技能定义
├── package.json             # 依赖配置
├── .env.example             # 环境变量模板
├── .gitignore               # Git忽略配置
├── lib/
│   └── client.js            # 增强版X API客户端
├── config/
│   ├── targets.js           # 目标账号配置
│   ├── keywords.js          # 搜索关键词配置
│   └── templates.js         # 内容模板配置
├── scripts/
│   ├── daily_operations.js  # 主运营脚本
│   ├── test_permissions.js  # 权限诊断工具
│   ├── generate_oauth_url.js # OAuth授权URL生成
│   ├── get_new_token.js     # Access Token获取
│   └── quick_security_check.js # 安全审查工具
├── references/              # 参考文档和指南
└── logs/                    # 执行日志目录（自动生成）
```

## ⚙️ 自定义配置

### 目标账号
编辑`config/targets.js`自定义跟踪对象：

```javascript
module.exports = {
  // AI公司官方账号
  official: ['OpenAI', 'AnthropicAI', 'GoogleAI', 'Microsoft'],
  
  // 科技影响者和研究者
  kols: ['sama', 'karpathy', 'ylecun', 'AndrewYNg'],
  
  // 投资者和行业领袖
  leaders: ['gdb', 'paulg', 'naval', 'cdixon']
};
```

### 搜索关键词
编辑`config/keywords.js`自定义搜索词：

```javascript
module.exports = [
  // 英文关键词
  'AI', 'artificial intelligence', 'machine learning',
  'large language model', 'LLM', 'GPT', 'AGI',
  
  // 中文关键词（双语跟踪）
  'AI大模型', '人工智能', '机器学习',
  '大语言模型', 'AGI', 'AIGC'
];
```

### 内容模板
编辑`config/templates.js`自定义你的声音：

```javascript
module.exports = {
  // 原创推文模板（总是以问句结尾）
  originalTweets: [
    "注意到今天多个来源都在讨论{trend}。这对{sector}最被低估的影响是什么？",
    "{insight}表明我们正处在转折点。{audience}应该如何为下一步做准备？"
  ],
  
  // 评论模板（有参与感，不垃圾）
  commentTemplates: [
    "有趣的观点。你觉得这会如何影响采用时间线？",
    "这与我们观察到的一致。关键问题是可扩展性。"
  ]
};
```

## 🛠️ 故障排除

### 常见问题与解决方案

#### ❌ "所有写入操作都返回401错误"
**问题**：Access Token没有写入权限。

**解决方案**：
```bash
# 1. 运行诊断
node scripts/test_permissions.js

# 2. 检查X开发者后台
#    - 访问 https://developer.twitter.com
#    - 找到你的应用
#    - 确保"应用权限"是"Read and Write"

# 3. 如果还是"Read only"，改为"Read and Write"
# 4. 重新生成Access Token
# 5. 更新.env文件
```

#### ❌ "评论失败但点赞/转发正常"
**问题**：X对评论有额外限制。

**解决方案**：
- 技能自动降级（失败的评论转为点赞+转发）
- 确保只与允许回复的账号互动
- 避免评论受保护的账号
- 保持评论简短有意义

#### ❌ "频率限制超出（429错误）"
**问题**：API调用太频繁。

**解决方案**：
- 在.env文件中增加`OPERATION_DELAY`值
- 减少每日互动数量
- 技能已包含智能节奏控制

#### ❌ "网络/代理连接问题"
**问题**：无法连接X API。

**解决方案**：
```env
# 在.env文件中配置代理（如果需要）：
HTTPS_PROXY=http://127.0.0.1:17890
```

## 📈 最佳实践

### 互动策略
1. **质量优于数量**：有意义地互动5条推文比肤浅地互动50条更好
2. **一致性**：每日互动比偶尔爆发更能建立存在感
3. **价值添加**：评论应提供洞察，不只是"好帖"
4. **原创内容**：分享独特视角，不只是转推

### 技术建议
1. **环境变量**：永远不要将`.env`提交到版本控制
2. **定期更新**：每季度检查X API变化
3. **监控**：每周查看日志及早发现问题
4. **备份配置**：备份你的自定义配置

### 合规与道德
1. **遵守X规则**：尊重频率限制和服务条款
2. **真实互动**：不要垃圾信息或使用欺骗性做法
3. **透明度**：如果被问及，明确说明自动化互动
4. **价值导向**：旨在贡献对话，不只是提取价值

## 🔄 版本历史

### v2.0 (2026-03-25) - 重大重写
- **模块化架构**：分离lib/、config/、scripts/、references/
- **增强错误处理**：重试逻辑、优雅降级
- **权限诊断**：完整的API权限问题工具集
- **OAuth 1.0a工具**：generate_oauth_url.js和get_new_token.js
- **完整文档**：英文和中文README
- **安全第一**：无硬编码凭证，安全审查工具

### v1.x (先前版本)
- 基础搜索和互动功能
- 简单错误处理
- 有限文档

## 🤝 贡献

发现bug？有功能请求？

1. **检查现有问题**在GitHub上
2. **创建新问题**附详细描述
3. **包含日志**：使用`--debug`标志运行并包含输出
4. **具体说明**：发生了什么 vs 你期望什么

## 📄 许可证

MIT许可证 - 详见[LICENSE](LICENSE)文件。

## 🙏 致谢

- 为OpenClaw生态系统构建
- 专为AI/科技领域运营者设计
- 基于真实世界X API限制测试
- 灵感来自快速变化行业中更好的情报工具需求

---

**准备好自动化你的X情报了吗？** 从`node scripts/test_permissions.js`开始确保一切正常，然后安排你的第一次每日运行！

**有问题？** 查看[英文文档](README.md)或在GitHub上创建issue。