---
name: tavily
description: 使用 Tavily API 进行网络搜索。适用于：(1) 用户需要 AI 优化的搜索结果，(2) 研究类查询需要结构化输出，(3) 当 Brave Search 不可用时作为替代方案。
metadata:
  {
    "openclaw":
      {
        "primaryEnv": "TAVILY_API_KEY",
        "requires": { "bins": ["curl"], "env": ["TAVILY_API_KEY"] },
      },
  }
---

# Tavily 搜索

使用 Tavily API 进行网络搜索。Tavily 专为 AI/Agent 设计，提供结构化输出和研究类搜索。

**重要：`TAVILY_API_KEY` 已由 OpenClaw 自动注入到 shell 环境变量中。直接在命令中使用 `$TAVILY_API_KEY`，无需检查或手动设置。**

## 使用方式

```bash
curl -s -X POST "https://api.tavily.com/search" \
  -H "Content-Type: application/json" \
  -d "{\"query\":\"你的查询\",\"api_key\":\"$TAVILY_API_KEY\",\"max_results\":5}"
```

## 参数说明

- `query`: 搜索关键词
- `api_key`: 使用 `$TAVILY_API_KEY`（已自动注入）
- `max_results`: 返回结果数量（默认 5）
- `search_depth`: `"basic"` 或 `"advanced"`（深度搜索）

## 示例

```bash
curl -s -X POST "https://api.tavily.com/search" \
  -H "Content-Type: application/json" \
  -d "{\"query\":\"OpenAI latest news\",\"api_key\":\"$TAVILY_API_KEY\",\"max_results\":3}"
```

## 注意事项

- 免费版每月 1000 credits
- 响应速度快（约 2 秒）
- 返回结构化 JSON，包含 `title`、`url`、`content`、`score`
