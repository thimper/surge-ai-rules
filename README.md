# Surge AI 规则订阅

集中维护 AI 服务的域名分流规则，供 macOS 和 iOS Surge 共用。更新此仓库一次，各设备会自动下载同一份规则，无需分别修改本地名单。

## 订阅地址

https://raw.githubusercontent.com/thimper/surge-ai-rules/main/rules/ai.list

在 Surge 配置的 `[Rule]` 中添加以下一行，并放在国内直连规则和其他通用规则之前：

```ini
RULE-SET,https://raw.githubusercontent.com/thimper/surge-ai-rules/main/rules/ai.list,🤖 AI专属,update-interval=86400
```

`🤖 AI专属` 是各设备本地的策略组名。节点、密钥、默认节点选择均保留在设备本地；本仓库只维护公开域名匹配规则，不存放完整配置或访问凭据。

## 覆盖范围

Anthropic / Claude、OpenAI / ChatGPT、Google AI、xAI / Grok，以及 Perplexity、Poe、Hugging Face、Cursor、Copilot、Midjourney、Runway、ElevenLabs、Mistral、Groq、Together、Replicate、Muse 等。

Muse 使用 `DOMAIN-SUFFIX,muse.ai`，包含其认证等子域名。Google AI 只列相关子域名，普通 Google 搜索继续使用原有分流。

## 如何维护

修改 `rules/ai.list` 并提交到 `main`：

- `DOMAIN-SUFFIX,example.ai`：匹配域名及其所有子域名。
- `DOMAIN,ai.example.com`：只匹配指定主机名。
- 文件中的规则不填写策略组名，也不加入 FINAL 规则。

各设备配置为每 24 小时检查更新。需要立即生效时，可在 Surge 的外部资源中更新此规则集。
