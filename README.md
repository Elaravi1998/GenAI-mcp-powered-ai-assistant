# 🤖 MCP-Powered AI Assistant

An AI assistant built with **Python, Model Context Protocol (MCP), and optional LLM integration**. This project demonstrates how an AI application can dynamically discover external tools, execute structured tool calls, and use an LLM to select tools based on natural-language requests.

## 🚀 Features

- 🔌 MCP server and client integration
- 🛠️ Dynamic tool discovery
- 🧮 Arithmetic tool for calculations
- 🔎 Knowledge-base search tool
- 💻 System-status tool
- 🧠 Optional LLM-assisted tool selection
- 🔄 Deterministic fallback without an API key
- 🔐 Environment-variable configuration for API credentials
- 📓 Python Jupyter Notebook walkthrough

## 🏗️ Architecture

```text
                User Request
                     |
                     v
             AI Assistant
                     |
                     v
           Optional LLM Planner
                     |
                     v
                MCP Client
                     |
              Tool Discovery
              and Execution
                     |
                     v
                 MCP Server
                     |
        +------------+------------+
        |            |            |
        v            v            v
   Add Numbers   Knowledge     System
                  Search       Status
```

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Model Context Protocol (MCP) | Standardized communication between AI applications and tools |
| FastMCP | Creating the MCP server |
| MCP Python SDK | Connecting to and invoking MCP tools |
| OpenAI-compatible API | Optional LLM-based tool selection |
| python-dotenv | Loading environment configuration |
| Jupyter Notebook | Interactive development and demonstration |

## 📁 Project Structure

```text
mcp-powered-ai-assistant/
│
├── mcp_powered_ai_assistant.ipynb
├── mcp_server.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

**Note:** The notebook generates `mcp_server.py` when you run the server-code cell.

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/mcp-powered-ai-assistant.git
cd mcp-powered-ai-assistant
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Create a virtual environment

**Windows PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS/Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook mcp_powered_ai_assistant.ipynb
```

Run the notebook cells from top to bottom.

## 🔌 MCP Tools

The example MCP server provides three tools.

### 1. Add Numbers

Adds two numbers and returns the result.

Example arguments:

```json
{
  "a": 17,
  "b": 25
}
```

Expected sum: `42`

### 2. Search Knowledge Base

Searches a small sample knowledge base using keyword matching.

Example arguments:

```json
{
  "query": "MCP security",
  "limit": 3
}
```

### 3. Get System Status

Returns a simple status response for the local demonstration server.

Example output:

```json
{
  "status": "ok",
  "service": "portfolio-assistant",
  "environment": "local-demo"
}
```

## 🧠 Optional LLM Integration

The notebook can optionally use an OpenAI-compatible API to choose an MCP tool based on a user's request.

Create a `.env` file using `.env.example` as a template.

Example configuration:

```dotenv
OPENAI_API_KEY=your_api_key_here
OPENAI_BASE_URL=https://api.openai.com/v1
OPENAI_MODEL=gpt-4.1-mini
```

Use the API endpoint and model name supported by your provider.

**Important:** Never commit your `.env` file or expose API keys in source code.

Without an API key, the notebook uses a deterministic fallback for supported example requests.

## 💬 Example Requests

Try these requests in the notebook:

```text
Add 17 and 25
```

```text
Search the knowledge base for MCP security
```

```text
Get system status
```

The assistant routes supported requests to the relevant tool.

## 🔐 Security Considerations

This is an educational starter project, not a production-hardened AI agent.

Before using it in production:

- Validate tool arguments against their schemas.
- Enforce authorization independently of the LLM.
- Expose only the tools required for the task.
- Treat user prompts and tool outputs as untrusted input.
- Use timeouts, rate limits, and appropriate error handling.
- Keep API keys in environment variables or a secrets manager.
- Require user confirmation before consequential or externally visible actions.
- Add audit logs and automated tests.
- Avoid exposing unrestricted shell access, private files, or unrestricted database access to an AI model.

The sample knowledge-base search uses keyword matching; it is not a production-grade semantic search or RAG implementation.

## 🛣️ Future Enhancements

- [ ] Add an MCP web-search integration.
- [ ] Add a read-only SQL database tool.
- [ ] Replace the simple planner with native LLM tool calling.
- [ ] Add schema-based argument validation and permission checks.
- [ ] Build a Streamlit or React chat interface.
- [ ] Add conversation memory.
- [ ] Implement automated tests and robust error handling.
- [ ] Add tracing, latency metrics, and token-cost tracking.
- [ ] Add authentication and deployment configuration.

## 🎯 Learning Outcomes

By completing this project, you will learn how to:

- Understand the MCP client-server architecture.
- Create an MCP server with custom tools.
- Discover tools dynamically.
- Invoke tools with structured arguments.
- Connect LLM-based reasoning with external tool execution.
- Implement basic fallback behavior.
- Identify security requirements for agentic AI applications.

## 📜 License

Choose a license before publishing, such as the MIT License, and include the corresponding `LICENSE` file.

---

**Built with Python, MCP, and Generative AI.**
