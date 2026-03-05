---
name: tavily-search
description: |
  Tavily 搜索工具：使用 Tavily API 进行网络搜索

  当需要搜索最新信息、新闻、网页内容时使用此技能。
  支持中英文搜索，可指定搜索结果数量和语言地区。
---

# Tavily 搜索技能

## 重要：正确的 API 调用方式

**Tavily API 必须使用 POST 方法 + JSON body 格式！**

### ❌ 错误方式（返回401）

```bash
curl "https://api.tavily.com/search?q=xxx&api_key=xxx"
```

### ✅ 正确方式

```bash
curl -s "https://api.tavily.com/search" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "搜索关键词",
    "api_key": "你的API Key",
    "max_results": 5
  }'
```

## 配置

API Key 已配置在 `~/.openclaw/openclaw.json` 中：

```json
{
  "web": {
    "tavily_api_key": "tvly-dev-xxxx"
  }
}
```

## 使用示例

### 搜索中文内容

```json
{
  "query": "中国股市 中东局势",
  "api_key": "tvly-dev-xxxx",
  "max_results": 5
}
```

### 搜索英文内容

```json
{
  "query": "China stock market Middle East impact",
  "api_key": "tvly-dev-xxxx",
  "max_results": 5
}
```

## 响应字段

| 字段              | 说明       |
| ----------------- | ---------- |
| results[].title   | 结果标题   |
| results[].url     | 结果链接   |
| results[].content | 内容摘要   |
| results[].score   | 相关度分数 |

## 常见问题

**Q: 返回 401 Unauthorized**
A: 检查是否用了 GET 方法，必须用 POST + JSON body

**Q: API Key 无效**
A: 登录 tavily.com 确认 Key 状态，可能是新申请的需要等待几分钟生效
