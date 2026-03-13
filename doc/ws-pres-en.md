---
marp: true
theme: default
paginate: true
backgroundColor: #1e1e1e
color: #ffffff
header: 'AI Agent Workshop - Model Context Protocol'
footer: 'Leif Terje Fonnes & Lars Søraas | March 2026'
style: |
  section {
    font-size: 24px;
    line-height: 1.3;
    padding: 40px;
  }
  h1 {
    font-size: 42px;
    margin-bottom: 0.4em;
    margin-top: 0.2em;
  }
  h2 {
    font-size: 32px;
    margin-bottom: 0.3em;
    margin-top: 0.2em;
  }
  h3 {
    font-size: 28px;
    margin-bottom: 0.2em;
    margin-top: 0.2em;
  }
  li {
    margin-bottom: 0.2em;
  }
  code {
    font-size: 18px;
  }
  pre {
    font-size: 16px;
    line-height: 1.2;
    margin: 0.5em 0;
  }
  ul, ol {
    margin: 0.5em 0;
  }
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem; /* Adds space between columns */
  }
---

<!--
_class: lead
_color: black _color: black
-->

# AI Agent Workshop
## AI Agents with Model Context Protocol (MCP)

**Leif Terje Fonnes and Lars Søraas**
*13 March - Booster 2026*

![bg](https://www.publicdomainpictures.net/pictures/180000/velka/paper-and-a-pencil-14671851619PA.jpg)

---

# 🎯 Learning Objectives

- **Understand** MCP architecture and concepts
- **Build** your own AI agent with tools
- **Extend** the system with new capabilities
- **Deploy** using Docker containers
- **Learn** best practices for production

![bg ](https://images.unsplash.com/photo-1589395937658-0557e7d89fad?fm=jpg&q=60&w=3000&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

---
<!--
_color: black _color: black
-->

# Agenda

1. **Introduction to MCP and AI Agents**
2. **Architecture Overview**
3. **Setting Up the Development Environment**
4. **MCP Architecture Recap**
5. **Hands-on**
8. **Advanced Features**
9. **Improvements**
10. **Summary & Resources**


![bg](https://www.publicdomainpictures.net/pictures/180000/velka/paper-and-a-pencil-14671851619PA.jpg)

---

<!-- _class: lead -->
# What is Model Context Protocol (MCP)?

![bg right](https://plus.unsplash.com/premium_photo-1678216285973-466494c8c707?fm=jpg&q=60&w=3000&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

---
# But first some context - what actually is an AI agent?

<div class="columns">
<div>

## An agent is "_something_" that can:
- Understand user requests
- Provide contextual responses
- Learn and adapt over time
- Perform actions via tools
- Fetch real-time data and resources
</div>
<div>

## To achieve this it needs
- Reasoning
  - Plan, make decisions
- Memory
  - Remember, have knowledge
- Access to the real world
  - Sense, feel, act
</div>
</div>

## MCP provides access to tools and data in a standardized way!

---

# MCP

###  **Protocol** for sending messages between AI and tools
- **Transport**: Which channels are used (HTTP, stdio, WebSocket)

- **Tool Definition**: How tools are described and discovered
- **Resources**: Access to data and documents
- **Prompts**: Reusable prompt templates

#### https://modelcontextprotocol.io/specification/2025-11-25 + https://modelcontextprotocol.io/docs/getting-started/intro

![bg right](https://images.unsplash.com/photo-1764185800646-f75f7e16e465?q=80&w=870)

---

<!-- _class: lead -->
# Architecture

## How does it all fit together?
### Workshop

![bg right](https://images.unsplash.com/photo-1554793000-245d3a3c2a51?fm=jpg&q=60&w=3000&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

---
# System Architecture


## 🌐 **Web Interface**
- Simple HTML frontend for testing
- Real-time interaction with agent


## 🤖 **AI Agent**
- Processes user requests with OpenAI
- Calls MCP tools when needed
- Handles "conversation memory"

## 🖥️ **MCP Server**
- Hosts tools for the agent
- Exposes tools via MCP standard
- Handles external API and resource integration

![w:500 bg right](https://res.cloudinary.com/duiwgrncm/image/upload/v1769337120/overordnet_1_xxnp4q.png)

---
# Deployment

- Each component runs in its own Docker container
- Host exposes 8080 (Web) and 8001 (Agent API), and 8000 (MCP Server API)
- Logs and data are shared via volumes

![w:500 bg right](https://res.cloudinary.com/duiwgrncm/image/upload/v1769296308/docker-ws_hsahin.png)

---
# Data Flow

## Startup

![h:16cm bg](https://res.cloudinary.com/duiwgrncm/image/upload/v1769353979/oppstart_1_dqqr1a.png)

---
# Data Flow

## Request

![h:16cm bg](https://res.cloudinary.com/duiwgrncm/image/upload/v1769337313/dataflyt_1_p11d46.png)

---

<!-- _class: lead -->
# Setting Up the Development Environment for the Workshop

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# Development Environment for the Workshop

## 1. Log in to your GitHub account
## 2. Create a *fork* of https://github.com/zral/mcp-lab03
## 3. Check **Copy the main branch only**
## 4. Select **Code / Codespaces / Create Codespace on...**
## 5. Copy **env.example** to **.env** in Codespace
## You now have a ready-to-go development environment!

---

# API Key for OpenAI GPT-4.1-mini
## You need this to access an LLM (weather data uses yr.no - no key required)
<p></p>

## 1. Go to https://github.com/marketplace/models
## 2. Select **OpenAI GPT-4o-mini / Use this model / Create Personal Access Token**
## 3. Copy the token - remember - you _cannot_ view it again
## 4. Open the **.env** file in Codespaces and paste the token into the placeholder for ```OPENAI_API_KEY```
## 5. Weather data is fetched from yr.no (api.met.no) - no API key required
---

<!-- _class: lead -->
# Before we get started - recap and clarifications

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# MCP Architecture

## Dynamic Tools Discovery
- **Agent fetches tools automatically** from MCP server at startup
- **No hardcoding** of tool definitions in agent code
- **MCP standard** for tools exchange

## Easier Development
- **Only modify MCP server** to add new tools
- **Agent restarts automatically** with new tools
- **Loose coupling** between components

## Scalability
- **Multiple MCP servers** can expose different tools
- **Plugin architecture** for new functionality

https://modelcontextprotocol.io/specification/2025-11-25/server/tools

---

# MCP Standard 2025-11-25
## The workshop follows the standard but with some simplifications for learning

<div class="columns" >
<div>

### 1. ✅ **JSON-RPC 2.0 Protocol**
- ✅ Implemented `tools/list` and `tools/call`
- ✅ Uses standardized JSON-RPC messages
- ⚠️ Can be extended with notifications and cancellation

### 2. **Multiple Transport Protocols**
- ✅ **HTTP**: Already supported
- 📝 **stdio**: For CLI integration
- 📝 **HTTP SSE**: For streaming
- 📝 **WebSocket**: For real-time communication
</div>
<div>

### 3. **Simplify - Use MCP SDK**
- Python: `mcp` package from modelcontextprotocol
- TypeScript: `@modelcontextprotocol/sdk`
- Simplifies transport and protocol handling
- NOTE: Our JSON-RPC implementation follows the standard and is compatible!

### 4. **Extend with More MCP Capabilities**
- **Resources**: Access to data and documents
- **Prompts**: Reusable prompt templates
- **Sampling**: LLM sampling requests
</div>

---

<!-- _class: lead -->
# Hands-on: Exploring the Code

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---


# Project Structure

```
./
├── docker-compose.yml        # 🐳 Container orchestration (use: docker compose)
├── .env.example              # 🔐 Environment variables (copy to .env)
└── services/
    ├── mcp-server/          # 🔧 MCP Server
    │   ├── app.py           # ⭐ JSON-RPC 2.0 endpoint
    │   ├── Dockerfile       # 🐳 Container image
    │   └── requirements.txt
    ├── agent/               # 🤖 AI Agent
    │   ├── app.py           # ⭐ OpenAI & MCP Server integration
    │   ├── conversation_memory.py       # 🧠 Conversation memory
    │   ├── Dockerfile
    │   └── requirements.txt
    ├── web/                  # 🌐 Frontend
    │   ├── app.py            # ⭐ Simple web server
    │   ├── Dockerfile
    │   └── templates/
    ├── mcp-sdk-client/       # ✅ Compliance test
    │   ├── test_mcp_sdk.py
    │   ├── Dockerfile
    │   └── requirements.txt
    └── shared/               # 📦 Shared resources
```

---

# Agent - Fetching Tools from MCP Server

```python
# services/agent/app.py

# Tools are fetched dynamically from MCP server at startup via JSON-RPC
async def load_tools_from_mcp_server(self):
    """Fetch available tools from MCP server via JSON-RPC."""
    jsonrpc_request = {
        "jsonrpc": "2.0",
        "id": 1,
        "method": "tools/list"
    }
    response = await self.http_client.post(
        f"{self.mcp_server_url}/message",
        json=jsonrpc_request
    )
    jsonrpc_response = response.json()
    mcp_tools = jsonrpc_response["result"]

    # Convert from MCP format to OpenAI function calling format
    for tool in mcp_tools.get("tools", []):
        openai_tool = {
            "type": "function",
            "function": {
                "name": tool["name"],
                "description": tool["description"],
                "parameters": tool["inputSchema"]
            }
        }
        self.tools.append(openai_tool)
```

---
# MCP Server - Tools Manifest

```json
{
  "tools": [
    {
      "name": "get_weather_forecast",
      "title": "Weather Forecast Provider",
      "description": "Fetch weather forecast for a destination...",
      "inputSchema": {
        "$schema": "https://json-schema.org/draft/2020-12/schema",
        "type": "object",
        "properties": {
          "location": {
            "type": "string",
            "description": "Name of city or location"
          }
        },
        "required": ["location"],
        "additionalProperties": false
      },
      "outputSchema": {
        "$schema": "https://json-schema.org/draft/2020-12/schema",
        "type": "object",
        "properties": {
          "location": { "type": "object" },
          "current": { "type": "object" },
          "forecast": { "type": "array" }
        }
      }
    }
  ]
}
```

---

# 🔄 JSON-RPC 2.0 Protocol

### MCP Message Handler - JSON-RPC
```python
# MCP Server: JSON-RPC message handler
@app.post("/message")
async def handle_jsonrpc(request: JSONRPCRequest):
    if request.method == "tools/list":
        return JSONRPCResponse(id=request.id, result={"tools": [...]})
    elif request.method == "tools/call":
        tool_name = request.params["name"]
        arguments = request.params["arguments"]
        result = await handle_tools_call(tool_name, arguments)
        return JSONRPCResponse(id=request.id, result=result)
```

### Agent Calls via JSON-RPC
```python
# Agent: Call tools/call via JSON-RPC
jsonrpc_request = {
    "jsonrpc": "2.0",
    "id": 2,                # Unique ID per call
    "method": "tools/call",
    "params": {
        "name": "get_weather_forecast",
        "arguments": {"location": "Oslo"}
    }
}
response = await http_client.post("/message", json=jsonrpc_request)
result = response.json()["result"]
```

---

# Flow - Tool Calls

```python
# When OpenAI wants to use a tool
if response_message.tool_calls:
    for tool_call in response_message.tool_calls:
        tool_name = tool_call.function.name
        tool_args = json.loads(tool_call.function.arguments)

        # Call MCP server
        tool_result = await self.call_mcp_tool(tool_name, tool_args)

        # Add result to the conversation
        messages.append({
            "role": "tool",
            "tool_call_id": tool_call.id,
            "content": json.dumps(tool_result)
        })
```

---

<!-- _class: lead -->
# Hands-on: Building Tools

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# Lab Exercise 1: Explore Existing Tools

## Let's examine the weather tool and the new MCP architecture

```bash
# Start the system
docker compose up -d

# Test tools/list - see available tools (JSON-RPC)
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 1, "method": "tools/list"}' | python3 -m json.tool

# Test tools/call - call weather tool directly (JSON-RPC)
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 2,
    "method": "tools/call",
    "params": {
      "name": "get_weather_forecast",
      "arguments": {"location": "Oslo"}
    }
  }'

# Test via agent (agent uses JSON-RPC internally)
curl -X POST "http://localhost:8001/query" \
  -H "Content-Type: application/json" \
  -d '{"query": "What is the weather in Bergen?"}'
```

---

# Lab Exercise 2: Add a New Tool - Random Fact

### Step 1: Add fact endpoint to MCP Server

<div style="font-size: small;">

```python
# In services/mcp-server/app.py

async def get_random_fact(category: str = "general") -> Dict[str, Any]:
    """Get a random interesting fact."""
    try:
        facts = {
            "general": ["Honeybees produce food eaten by humans.",
                       "Bananas are berries, but strawberries are not."],
            "space": ["A day on Venus is longer than its year.",
                     "Saturn would float in water."]
        }

        import random
        fact = random.choice(facts.get(category, facts["general"]))

        result = {
            "category": category,
            "fact": fact,
            "timestamp": datetime.now().isoformat()
        }

        return result

    except Exception as e:
        logger.error(f"Fact retrieval error: {e}")
        return {"error": f"Could not retrieve fact: {str(e)}"}
```
</div>

---

# Lab Exercise 2: Update Tools Manifest

### Step 2: Add to the tools list (JSON-RPC compliant)

<div style="font-size: small;">

```python
# In services/mcp-server/app.py, update handle_tools_list():

async def handle_tools_list() -> Dict[str, Any]:
    tools = [
        {
            "name": "get_weather_forecast",
            "title": "Weather Forecast Provider",
            "description": "Fetch weather forecast for a destination",
            "inputSchema": { /* ... */ }
        },
        {
            "name": "get_random_fact",
            "title": "Random Fact Provider",
            "description": "Get a random interesting fact",
            "inputSchema": {
                "$schema": "https://json-schema.org/draft/2020-12/schema",
                "type": "object",
                "properties": {
                    "category": {
                        "type": "string",
                        "description": "Fact category (general, space)",
                        "enum": ["general", "space"]
                    }
                },
                "required": ["category"],
                "additionalProperties": False
            }
        }
    ]
    return {"tools": tools}
```

</div>

---
# Lab Exercise 2: Handle Tool Calls

### Step 3: Add routing in handle_tools_call()

```python
# In handle_tools_call(), add:

elif tool_name == "get_random_fact":
    category = arguments.get("category", "general")

    result = await get_random_fact(category)

    if "error" in result:
        return {
            "content": [{"type": "text", "text": json.dumps(result, ensure_ascii=False)}],
            "isError": True
        }

    return {
        "content": [{"type": "text", "text": json.dumps(result, ensure_ascii=False, indent=2)}],
        "structuredContent": result,
        "isError": False
    }
```
---

# Lab Exercise 2: Test the New Tool

### Step 4: JSON-RPC Compliance Testing

```bash
# Rebuild (agent fetches tools at startup)
docker compose build mcp-server travel-agent
docker compose up -d

# Test tools/list with JSON-RPC
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 1, "method": "tools/list"}' | python3 -m json.tool

# Test tools/call to fetch a fact (space category)
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 2,
    "method": "tools/call",
    "params": {
      "name": "get_random_fact",
      "arguments": {"category": "space"}
    }
  }' | python3 -m json.tool

# Test the new tool via agent
curl -X POST "http://localhost:8001/query" \
  -H "Content-Type: application/json" \
  -d '{"query": "Tell me an interesting fact about space"}'
```

---

# Expected Result

**When you run these commands you should see:**
- ✅ `tools/list` returns both `get_weather_forecast` and `get_random_fact`
- ✅ `tools/call` for `get_random_fact` returns a JSON response
- ✅ Agent can use both weather tool and fact tool in the same conversation

---

# Lab Exercise 2.5: Validation - Multiple Tools Together

**Test that the agent can use both tools in the same query:**

```bash
curl -X POST "http://localhost:8001/query" \
  -H "Content-Type: application/json" \
  -d '{"query": "What is the weather in Oslo and tell me a fact about space"}'
```

The agent should now automatically:
1. Fetch weather data for Oslo
2. Fetch a fact about space
3. Combine the answers into one response

---

# Lab Exercise 3: API Integration - https://newsapi.org


<div class="columns">
<div>

### Now you'll use **everything** you've learned so far to add a real News API

The code you can use is shown on the right side.

- In addition, you need to create a manifest and routing for the tool.
- The API key must be added to the .env file as NEWS_API_KEY.
- Finally, test with JSON-RPC or Curl and via the agent.

</div>
<div>

```python
# In services/mcp-server/app.py - Add to handle_tools_call()

async def get_news(topic: str, language: str = "no") -> Dict[str, Any]:
    """Get recent news about a topic via NewsAPI."""
    api_key = os.getenv("NEWS_API_KEY")
    if not api_key:
        return {
            "isError": True,
            "content": [{"type": "text", "text": "NEWS_API_KEY not configured"}]
        }

    try:
        async with httpx.AsyncClient() as client:
            response = await client.get(
                "https://newsapi.org/v2/everything",
                params={
                    "q": topic,
                    "language": language,
                    "apiKey": api_key
                },
                timeout=10.0
            )

        news_data = response.json()
        articles = [
            {"title": article["title"], "url": article["url"]}
            for article in news_data.get("articles", [])[:3]
        ]

        return {
            "isError": False,
            "content": [{
                "type": "text",
                "text": f"Latest news about '{topic}':\n\n" +
                        "\n".join([f"- {a['title']}\n  {a['url']}" for a in articles])
            }]
        }
    except Exception as e:
        return {
            "isError": True,
            "content": [{"type": "text", "text": f"Error fetching news: {str(e)}"}]
        }
```

## Add to handle_tools_list()
```python
{
    "name": "get_news",
    "description": "Fetch latest news about a topic",
    "inputSchema": {
        "type": "object",
        "properties": {
            "topic": {"type": "string", "description": "Topic to search for"},
            "language": {"type": "string", "description": "Language code (e.g. 'no', 'en')"}
        },
        "required": ["topic"]
    }
}
```

</div>
</div>
---

<!-- _class: lead -->
# 🐳 Deployment & Test

---

# Docker Compose Commands

## Development Workflow

```bash
# Start from scratch
docker compose up --build

# Stop everything
docker compose down

# Rebuild a specific service
docker compose build mcp-server

# View logs
docker compose logs -f travel-agent

# Check health
curl http://localhost:8000/health
```

---

# Environment Setup

## 1. Copy environment file
```bash
cp .env.example .env
```

## 2. Add API keys
```bash
# .env
OPENAI_API_KEY=your-openai-api-key-here
# Weather data uses yr.no (api.met.no) - no API key required
NEWS_API_KEY=your-news-api-key-here  # If you use the news tool
```

## 3. Build and start
```bash
docker compose up --build
```

---

# Testing Strategy

## 1. Unit Testing (Individual Tools)
```bash
# Test MCP server tools/call directly via JSON-RPC
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "tools/call",
    "params": {
      "name": "get_weather_forecast",
      "arguments": {"location": "Oslo"}
    }
  }'

# Test Lab Exercise 3: get_news tool
curl -X POST "http://localhost:8000/message" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "id": 2,
    "method": "tools/call",
    "params": {
      "name": "get_news",
      "arguments": {"topic": "Python", "language": "en"}
    }
  }'
```

## 2. Integration Testing (Full Flow)
```bash
# Test through agent
curl -X POST "http://localhost:8001/query" \
  -H "Content-Type: application/json" \
  -d '{"query": "What are the latest news about AI?"}'
```

## 3. Web Testing
Open http://localhost:8080 in your browser

---

# Tips - Debugging

## Common Problems & Solutions

### 🔴 **Container won't start**
```bash
docker compose logs service-name
```

### 🔴 **API calls failing**
```bash
docker compose exec travel-agent env | grep API
```

### 🔴 **Tool not recognized**
```bash
curl http://localhost:8001/health
```

---

<!-- _class: lead -->
# Advanced Features

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# Advanced MCP Tool Concepts

<div class="columns">
<div>

### 1. **Stateful Tools**
- **User preferences**: Remember temperature unit, language, location
- **Conversation history**: View previous questions and answers
- **Session management**: Authentication, authorization
- **Example**: Weather tool remembers that user uses Celsius

### 2. **Asynchronous Operations** (Async/Polling)
- **Long-running tasks**: API calls that take a long time
- **Background processing**: Data fetching or computation
- **Polling/Callbacks**: Check job status
- **Example**: Order report → receive status ID → poll for result
</div>
<div>

## 3. **Multi-step Workflows** (Orchestration)
- **Tool chaining**: Tool A provides output to Tool B
- **Conditional logic**: "If weather forecast is bad, check alternatives"
- **Error handling**: Retry on timeout, fallback alternatives
- **Example**: Get weather → find attractions → book activity
</div>
</div>

---

# Security Considerations

## Input Validation
```python
from pydantic import BaseModel, validator

class SecureRequest(BaseModel):
    location: str

    @validator('location')
    def validate_location(cls, v):
        if len(v) > 100:
            raise ValueError('Location too long')
        # Add more validation...
        return v
```

## API Key Management
```python
import os

def get_api_key(service: str) -> str:
    key = os.getenv(f"{service.upper()}_API_KEY")
    if not key:
        raise ValueError(f"Missing {service} API key")
    return key
```

---

# Deployment - Production

## Scalability
- **Load balancing** with multiple agent instances
- **Database clustering** for conversation memory
- **Caching** for frequently used tool results

## Monitoring
- **Health checks** and uptime monitoring
- **Log aggregation** (ELK stack)
- **Metrics collection** (Prometheus/Grafana)
- **Error tracking** (Sentry)

## Security
- **API rate limiting**
- **Input sanitization**
- **HTTPS termination**
- **Secrets management**

---

# Extending the Architecture

## Adding New Features

### 🧠 **Memory**
- Vector databases for semantic search
- Knowledge graphs for relationships
- Long-term learning and adaptation

### 🔗 **Integration**
- Webhook endpoints for real-time updates
- Message queues for asynchronous processing
- Event-driven architecture

### 🌐 **Multi-Modal Support**
- Image analysis tools
- Audio processing
- Video interpretation

---

<!-- _class: lead -->
# Further Work

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# Exercise 1: Weather Improvement
**Difficulty: Beginner**

Improve the weather tool to include:
- UV index information
- Air quality data
- Sunrise/sunset times

**Tip:** yr.no (api.met.no) provides all this data in the response - without an API key!

---

# Exercise 2: Calculator Tool
**Difficulty: Beginner**

Create a calculator tool that can:
- Perform basic mathematical operations
- Handle complex expressions
- Show step-by-step solutions

```python
# Tool idea
@app.post("/tools/calculate")
async def calculate(request: CalculationRequest):
    # Your implementation here
    pass
```

---

# Exercise 3: Memory-Enabled Chat
**Difficulty: Intermediate**

Extend the agent to remember:
- User preferences (favorite cities, units)
- Previous conversations
- Personalized recommendations

**Files to modify:**
- `conversation_memory.py`
- Agent conversation logic

---

# Exercise 4: Orchestration - Workflows
**Difficulty: Advanced**

Create a travel planning workflow:
1. Get weather for destination
2. Find nearby attractions
3. Check calendar availability
4. Send email summary

**Requires:** Multiple API integrations + workflow logic

---

<!-- _class: lead -->
# Summary

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)

---

# What You Have Learned

<div class="columns" >
<div>

## 🧠 **Concepts**
- Model Context Protocol fundamentals
- JSON-RPC 2.0 protocol for tool communication
- Dynamic tool discovery and loading
- AI agent architecture patterns
- Tool-based AI system design

## 🚀 **Best Practices**
- Structured error handling and error responses
- Security considerations (input validation, API keys)
- Project structure and code organization
- Debugging and logging
</div>
<div>

## 🛠️ **Practical Skills**
- Building MCP-compatible tools
- Integrating external APIs securely
- Docker containerization and docker compose orchestration
- Testing strategies
- Conversation memory and stateful agents

</div>
</div>

---

# Next Steps

## 📚 **Keep Learning**
- Explore the MCP specification in depth
- Study advanced AI agent patterns
- Learn about vector databases and RAG and integrate with MCP

## 🔧 **Build More**
- Create industry-specific tools
- Implement production monitoring
- Scale to multi-tenant architecture

## 🌐 **Community**
- Join the MCP developer community
- Contribute to open source tools
- Share implementations

---

# Resources

## 📖 **Documentation**
- [Model Context Protocol Docs](https://modelcontextprotocol.io/)
- [OpenAI API Reference](https://platform.openai.com/docs/)
- [Docker Compose Guide](https://docs.docker.com/compose/)

## 🛠️ **Tools & Libraries**
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Pydantic for Data Validation](https://pydantic-docs.helpmanual.io/)
- [HTTPX for Async HTTP](https://www.python-httpx.org/)

---

<!-- _class: lead -->
# Questions & Discussion

## Thank you!

**Leif Terje Fonnes**
leffen@gmail.com
github.com/leffen

**Lars Søraas**
lsoraas@gmail.com
github.com/zral

![bg opacity:.3](https://res.cloudinary.com/duiwgrncm/image/upload/v1769355942/walkator-klMii3cR9iI-unsplash_xxqclo.jpg)
