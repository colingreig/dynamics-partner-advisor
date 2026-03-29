# Dynamics Partner Advisor - MCP Server

![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-green)
![Status](https://img.shields.io/badge/Status-Live-blue)

The **Dynamics Partner Advisor** MCP Server connects your AI agents (Claude Desktop, Cursor, Windsurf, etc.) to the most comprehensive database of Microsoft Dynamics 365 implementation partners.

**🔗 Official Website:** [https://topdynamicspartners.com/resources/mcp-server](https://topdynamicspartners.com/resources/mcp-server)
*

## 🚀 Features

Equip your AI assistant with the ability to:
* **🔎 Search Partners:** Find partners by product (Business Central, Finance, Sales), industry, and region.
* **📊 Get Deep Insights:** Retrieve detailed partner profiles, including verified reviews and specific functional strengths.
* **💡 Generate Shortlists:** Get AI-driven recommendations for the best partners based on project complexity and company size.

## 🔌 Quick Start: Claude Desktop

To add this server to Claude Desktop, edit your configuration file:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

Add the following entry to the `mcpServers` object:

```json
"dynamics-partners": {
  "command": "npx",
  "args": [
    "-y",
    "@modelcontextprotocol/server-sse",
    "--url",
    "[https://topdynamicspartners.com/api/mcp/sse](https://topdynamicspartners.com/api/mcp/sse)"
  ]
}
