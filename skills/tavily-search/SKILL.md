---
name: tavily-search
description: |
  Tavily 搜索工具：使用 Tavily API 进行网络搜索

  当需要搜索最新信息、新闻、网页内容时使用此技能。
  支持中英文搜索，可指定搜索结果数量。
---

# Tavily 搜索技能

## 配置

API Key 已配置在 `~/.openclaw/openclaw.json` 中：

```json
{
  "web": {
    "tavily_api_key": "tvly-dev-xxx"
  }
}
```

## 使用方法

### 从配置文件读取 Key 并搜索

```bash
# 自动从配置文件读取 API Key
API_KEY=$(cat ~/.openclaw/openclaw.json | jq -r '.web.tavily_api_key')

curl -s "https://api.tavily.com/search" \
  -H "Content-Type: application/json" \
  -d "{
    \"query\": \"搜索关键词\",
    \"api_key\": \"$API_KEY\",
    \"max_results\": 5
  }"
```

### 响应字段

| 字段              | 说明       |
| ----------------- | ---------- |
| results[].title   | 结果标题   |
| results[].url     | 结果链接   |
| results[].content | 内容摘要   |
| results[].score   | 相关度分数 |

## 重要提示

- **必须使用 POST 方法 + JSON body 格式**
- API Key 从配置文件 `~/.openclaw/openclaw.json` 读取
- 配置文件路径：`web.tavily_api_key`
