a---
name: dynamics-partner-advisor
description: >
  Search, compare, and shortlist Microsoft Dynamics 365 implementation partners by product, industry, and region.
    Use when someone asks about finding a Dynamics partner, comparing ERP/CRM consultants, selecting a Business Central
      or Finance & Operations implementer, or needs help choosing a Microsoft partner for an ERP or CRM project.
        Connects to the live Top Dynamics Partners database via MCP (Model Context Protocol).
        license: MIT
        compatibility: >
          Requires MCP client support (Claude Desktop, Claude Code, Cursor, Windsurf, Cline, or any MCP-compatible agent).
            No local dependencies — connects to a hosted SSE endpoint.
            metadata:
              author: Ignite Marketing
                version: 1.0.0
                  tags: microsoft-dynamics, erp, crm, business-central, partner-selection, mcp
                    website: https://topdynamicspartners.com
                      repository: https://github.com/ignitemarketing/dynamics-partner-advisor
                      ---

                      # Dynamics Partner Advisor

                      Connect your AI agent to the most comprehensive database of Microsoft Dynamics 365 implementation partners. Search by product, filter by industry and region, and get AI-scored shortlists — all through the Model Context Protocol.

                      ## When to Use This Skill

                      Use this skill when the user:

                      - Asks about finding or comparing Microsoft Dynamics 365 partners
                      - Needs help selecting a Business Central, Finance & Operations, Sales, or Customer Service implementer
                      - Wants to evaluate ERP or CRM consultants in a specific country or region
                      - Asks for partner recommendations based on their company size, industry, or project type
                      - Mentions "Dynamics partner", "ERP partner", "Business Central consultant", or similar queries

                      ## Setup

                      Add the Dynamics Partner Advisor MCP server to your agent configuration.

                      ### Claude Desktop

                      Add to your `claude_desktop_config.json`:

                      ```json
                      {
                        "mcpServers": {
                            "dynamics-partners": {
                                  "command": "npx",
                                        "args": [
                                                "-y",
                                                        "@modelcontextprotocol/server-sse",
                                                                "--url",
                                                                        "https://topdynamicspartners.com/api/mcp/sse"
                                                                              ]
                                                                                  }
                                                                                    }
                                                                                    }
                                                                                    ```

                                                                                    ### Claude Code

                                                                                    ```bash
                                                                                    claude mcp add dynamics-partners -- npx -y @modelcontextprotocol/server-sse --url https://topdynamicspartners.com/api/mcp/sse
                                                                                    ```

                                                                                    ### Cursor / Windsurf / Other MCP Clients

                                                                                    Use the SSE transport endpoint:

                                                                                    ```
                                                                                    https://topdynamicspartners.com/api/mcp/sse
                                                                                    ```

                                                                                    ## Available Tools

                                                                                    ### 1. `search_partners`

                                                                                    Search for partners by product, country, and optional filters.

                                                                                    **Parameters:**

                                                                                    | Parameter | Required | Description |
                                                                                    |-----------|----------|-------------|
                                                                                    | `product` | Yes | Dynamics product (e.g., "Business Central", "Finance", "Sales", "Customer Service") |
                                                                                    | `country` | Yes | Country name or ISO code (e.g., "US", "United States", "CA", "United Kingdom") |
                                                                                    | `cityOrRegion` | No | City or state/province to narrow results |
                                                                                    | `industry` | No | Industry filter (e.g., "Manufacturing", "Distribution", "Retail", "Healthcare") |
                                                                                    | `min_review_score` | No | Minimum review rating (1-5) |

                                                                                    **Example prompt:** "Find Business Central partners in the United States that specialize in manufacturing"

                                                                                    **Returns:** Up to 3 partners (free tier) with name, location, products supported, industries, review score, and a link to their full profile on topdynamicspartners.com.

                                                                                    ### 2. `get_partner_details` *(authenticated)*

                                                                                    Get the full profile for a specific partner including services, strengths, ideal customer profile, and sample use cases.

                                                                                    **Parameters:**

                                                                                    | Parameter | Required | Description |
                                                                                    |-----------|----------|-------------|
                                                                                    | `slug` | Yes | Partner slug or name (e.g., "contoso-consulting") |

                                                                                    **Returns:** Complete partner profile with products, industries, services, regions served, Microsoft designations, years in business, review data, strengths, ideal customer profile, and sample use cases.

                                                                                    ### 3. `recommend_shortlist` *(authenticated)*

                                                                                    Get an AI-scored shortlist of partners tailored to a specific project.

                                                                                    **Parameters:**

                                                                                    | Parameter | Required | Description |
                                                                                    |-----------|----------|-------------|
                                                                                    | `primary_product` | Yes | Main Dynamics product needed |
                                                                                    | `industry` | Yes | Your industry |
                                                                                    | `region` | Yes | Geographic region (e.g., "North America", "US", "UK") |
                                                                                    | `company_size` | Yes | "small", "mid", or "enterprise" |
                                                                                    | `project_type` | Yes | "new", "upgrade", "rescue", or "extension" |
                                                                                    | `complexity_level` | Yes | "simple", "moderate", or "complex" |
                                                                                    | `budget` | No | Budget range for context |

                                                                                    **Example prompt:** "Recommend Dynamics 365 Business Central partners for a mid-market manufacturing company in North America doing a new implementation with moderate complexity"

                                                                                    **Returns:** Up to 5 ranked recommendations with fit reasoning and risk notes for each partner.

                                                                                    ## Access Tiers

                                                                                    | Feature | Free | Authenticated |
                                                                                    |---------|------|---------------|
                                                                                    | `search_partners` | 3 results, core fields | 25 results, full details |
                                                                                    | `get_partner_details` | — | Full profile |
                                                                                    | `recommend_shortlist` | — | Up to 5 recommendations |
                                                                                    | Rate limit | 30 req/min, 250/day | 60 req/min, 100K/day |

                                                                                    Request an API key at [topdynamicspartners.com/resources/mcp-server](https://topdynamicspartners.com/resources/mcp-server) for authenticated access.

                                                                                    ## Data Source

                                                                                    Partner data comes from [Top Dynamics Partners](https://topdynamicspartners.com), the independent directory of Microsoft Dynamics 365 implementation partners. The database includes verified partner profiles, client reviews, product certifications, industry specializations, and service offerings across 30+ countries.

                                                                                    ## Links

                                                                                    - **Website:** [topdynamicspartners.com](https://topdynamicspartners.com)
                                                                                    - **MCP Server Docs:** [topdynamicspartners.com/resources/mcp-server](https://topdynamicspartners.com/resources/mcp-server)
                                                                                    - **GitHub:** [github.com/ignitemarketing/dynamics-partner-advisor](https://github.com/ignitemarketing/dynamics-partner-advisor)
                                                                                    - **MCP Manifest:** [topdynamicspartners.com/.well-known/mcp.json](https://topdynamicspartners.com/.well-known/mcp.json)
