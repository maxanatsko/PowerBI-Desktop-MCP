[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/maxanatsko-powerbi-desktop-mcp-badge.png)](https://mseep.ai/app/maxanatsko-powerbi-desktop-mcp)

# Power BI Desktop MCP Server

**Version 2.0.9** - Model Context Protocol Server for Power BI Desktop

Compatible with: **Claude Desktop** • **Claude Code** • **VS Code (GitHub Copilot)** • Other MCP-compatible AI tools

> **Developed by Maxim Anatsko** | [maxanatsko.com](https://maxanatsko.com)
>
> **Note**: This is an independent, community-developed tool and is not affiliated with, endorsed by, or connected to Microsoft Corporation in any way.

[<img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" width="175" alt="Buy Me a Coffee">](https://buymeacoffee.com/rRVivpcqeW)

## Available Versions

This MCP server comes in two versions:

- **Full Version** (`powerbi-desktop-mcp`) - Complete access with all 26 tools including the ability to create, update, and delete model objects
- **Read-Only Version** (`powerbi-desktop-mcp-readonly`) - Safe exploration with 9 read and analysis tools only. Cannot modify your Power BI models.

Choose the read-only version if you want to explore and analyze your models without any risk of making changes.

## Table of Contents

- [What is this?](#what-is-this)
- [Privacy & Data](#privacy--data)
- [Key Features](#key-features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Option 1: Claude Desktop with .mcpb Package (Recommended)](#option-1-claude-desktop-with-mcpb-package-recommended)
  - [Option 2: Claude Desktop with .exe (Manual Configuration)](#option-2-claude-desktop-with-exe-manual-configuration)
  - [Option 3: Claude Code with .exe](#option-3-claude-code-with-exe)
  - [Option 4: VS Code with Native MCP Support](#option-4-vs-code-with-native-mcp-support)
- [Getting Started](#getting-started)
- [Available Tools](#available-tools)
- [Example Use Cases](#example-use-cases)
- [Troubleshooting](#troubleshooting)
- [Security & Privacy](#security--privacy)
- [Limitations](#limitations)
- [Support](#support)
- [Author & License](#author--license)

## What is this?

The Power BI Desktop MCP Server is a tool that lets AI assistants like Claude, GitHub Copilot, and other MCP-compatible AI tools interact with your Power BI models programmatically. It enables AI to read your model structure, run DAX queries, create and modify measures, manage relationships, and perform advanced analytics - all through natural conversation.

Think of it as giving AI "eyes and hands" to work with your Power BI models, allowing you to automate tasks, analyze data, and build solutions using AI assistance.

## Privacy & Data

### MCP Server: Zero Data Collection

**IMPORTANT: This MCP server does NOT collect, track, or store ANY data.**

The Power BI Desktop MCP Server is a local bridge application that:
- Runs entirely on your machine
- Does NOT send telemetry to any external servers
- Does NOT track analytics or usage data
- Does NOT log your personal information or Power BI model data
- Does NOT upload your data anywhere

**Data Flow:**
The MCP server acts as a simple pass-through between two components on your local machine:
1. **Your Power BI Desktop** → MCP Server (reads model structure, executes queries)
2. **MCP Server** → **Your AI Assistant** (sends responses back)

That's it. Nothing is sent to the MCP server developer or any third-party service.

### AI Assistant Privacy: Not Our Responsibility

**CRITICAL CLARIFICATION:**

This MCP server is a separate piece of software from the AI assistants you use it with (Claude, GitHub Copilot, etc.). **The AI assistants have their own privacy policies and data practices that are completely independent from this MCP server.**

When you use this MCP server with an AI assistant:
- The AI assistant (Claude Desktop, Claude Code, VS Code with GitHub Copilot, etc.) may collect and store conversation data according to their own privacy policies
- Review the privacy policy of your chosen AI assistant:
  - **Claude Desktop/Claude Code**: [Anthropic's Privacy Policy](https://www.anthropic.com/legal/privacy)
  - **VS Code with GitHub Copilot**: [Microsoft/GitHub Privacy Policies](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
- **The MCP server developer is NOT responsible for how AI assistants handle your data**
- Be mindful of what data from your Power BI models you ask the AI to analyze

**Your Responsibility:**
- Understand that AI assistants are third-party services with their own data practices
- Review the privacy policies of the AI assistant you choose to use
- Be careful about what sensitive or confidential data you expose to AI assistants
- The MCP server itself does not retain any data between requests - but your AI assistant might

## Key Features

### 🎯 26 Powerful Tools for Power BI Model Operations

**Model Management**
- Auto-discover and connect to running Power BI Desktop instances
- List available models and select which one to work with
- Get current connection status
- Manage model properties (descriptions, cultures, annotations)

**Data Exploration & Analysis**
- List and describe tables, columns, measures, and hierarchies
- Preview table data with configurable row limits
- Export complete model schema as JSON
- Execute DAX queries with results up to 1000 rows
- Get column statistics (min, max, null count, distinct values)
- Query performance analysis with Storage Engine and Formula Engine metrics

**Table Operations**
- Create new tables with multiple partition types
- Update table properties and structures
- Delete tables from the model
- Mark tables as date tables for time intelligence

**Measure Management**
- Create new DAX measures with dynamic format string expressions
- Update existing measures including name and expression
- Delete measures
- Format strings with static or dynamic expressions
- Display folder organization

**Relationship Operations**
- List all relationships with cardinality and cross-filter direction
- Create new relationships with full control
- Update relationship properties (active status, direction, cardinality)
- Delete relationships

**Partition Management** (Unified for all partition types)
- Create and manage M (Power Query), Query (SQL), Calculated (DAX), and Entity (Dataflow) partitions
- Support for Import, DirectQuery, and Dual storage modes
- Partition refresh at granular level
- View partition expressions and configurations

**Advanced Model Features**
- **User-Defined Functions (UDFs)**: Create, update, delete custom DAX functions with parameters
- **Calculation Groups**: Create calculation groups with dynamic calculation items
- **Hierarchies**: Manage hierarchies with multiple levels and ordering
- **KPIs**: Create Key Performance Indicators with target, status, and trend expressions
- **Roles & Security**: Manage security roles with row-level and object-level security (RLS/OLS)
- **Perspectives**: Create perspectives to filter model objects for different user groups
- **Calendars**: Configure time intelligence calendars with multiple time units

**Multi-Language Support**
- Cultures: Add languages/locales to your model
- Translations: Translate table/column/measure names and descriptions
- Support for 40+ culture codes (en-US, fr-FR, de-DE, es-ES, zh-CN, etc.)

**Data Source Management**
- List data sources and their configuration
- View partition information by type and storage mode
- Analyze M partition expressions
- Get data source details and connections

**Search & Discovery**
- Search for objects by name pattern (tables, columns, measures, calculated columns)
- Full-text search across DAX and M expressions
- Case-sensitive or case-insensitive search modes
- Find calculated columns with expressions

**Storage & Performance Optimization**
- VertiPaq statistics including dictionary size, data size, encoding
- Column cardinality analysis
- Compression ratio evaluation
- Storage mode analysis (Import vs DirectQuery)

**Refresh Operations**
- Refresh individual table partitions
- Refresh entire tables
- Full model refresh
- Metadata refresh for UDFs and calculations

## Prerequisites

Before installing, make sure you have:

1. **Windows 10/11** (Windows-only application)
2. **Power BI Desktop** installed ([Download MSI](https://www.microsoft.com/en-us/download/details.aspx?id=58494) or from Microsoft Store)
3. One of the following AI assistants:
   - **Claude Desktop** (recommended for .mcpb package installation)
   - **Claude Code** (CLI-based coding environment)
   - **VS Code** with GitHub Copilot (requires VS Code 1.102+)

Note: The `.exe` and `.mcpb` packages are self-contained and include all necessary runtime components. You do not need to install .NET separately.

## Installation

You can install the Power BI MCP Server in three ways. Each method works for both the **full version** and the **read-only version** - simply use the corresponding package or executable file for your preferred version.

### Option 1: Claude Desktop with .mcpb Package (Recommended)

The `.mcpb` package is the easiest way to install - it's a self-contained extension specifically for Claude Desktop.

1. **Download the package**:
   - **Full version**: `powerbi-desktop-mcp-2.0.9.mcpb` (all tools including create/update/delete)
   - **Read-only version**: `powerbi-desktop-mcp-readonly-2.0.9.mcpb` (view and analyze only)

2. **Install the extension**:
   - **Simple method**: Double-click the `.mcpb` file. Claude Desktop will open and show the installation dialog.
   - **Alternative method**:
     - Open Claude Desktop
     - Go to Settings (gear icon) → Extensions
     - Click "Advanced settings" → "Extension Developer" section
     - Click "Install Extension..."
     - Select the downloaded `.mcpb` file (full or read-only version)
     - Click "Install" in the dialog

3. **Restart Claude Desktop**: Completely quit and restart the application (not just close the window)

The server will be automatically configured and ready to use. You'll see an MCP indicator in the bottom-right corner of the conversation input box when the server is active.

### Option 2: Claude Desktop with .exe (Manual Configuration)

If you prefer manual configuration or need more control:

1. **Download the executable**:
   - **Full version**: `powerbi-desktop-mcp-2.0.9.exe` (all tools)
   - **Read-only version**: `powerbi-desktop-mcp-readonly-2.0.9.exe` (view and analyze only)

2. **Place in a permanent location**: For example, `C:\Program Files\PowerBI-MCP\powerbi-desktop-mcp-2.0.9.exe` (or the read-only version)

3. **Edit the configuration file**:
   - Open Claude Desktop
   - Click the Settings icon (gear icon in the bottom-left)
   - Navigate to Developer tab
   - Click "Edit Config" button
   - This opens `claude_desktop_config.json` in your default text editor

   **File location**: `%APPDATA%\Claude\claude_desktop_config.json` (Windows)

4. **Add this configuration**:

```json
{
  "mcpServers": {
    "powerbi-desktop": {
      "command": "C:\\Program Files\\PowerBI-MCP\\powerbi-desktop-mcp-2.0.9.exe",
      "args": []
    }
  }
}
```

Note: Use double backslashes (`\\`) in Windows paths. If you already have other MCP servers configured, add the `powerbi-desktop` entry to the existing `mcpServers` object.

5. **Save the file** and **completely quit and restart Claude Desktop**

After restart, you'll see an MCP indicator in the bottom-right corner of the conversation input box showing the server is connected.

### Option 3: Claude Code with .exe

For Claude Code (the coding environment):

1. **Download the executable**:
   - **Full version**: `powerbi-desktop-mcp-2.0.9.exe` (all tools)
   - **Read-only version**: `powerbi-desktop-mcp-readonly-2.0.9.exe` (view and analyze only)

2. **Place in a permanent location**: For example, `C:\Program Files\PowerBI-MCP\powerbi-desktop-mcp-2.0.9.exe` (or the read-only version)

3. **Add the MCP server using the command line**:

   Open Claude Code and use the built-in terminal or command palette:

```bash
# Full version
claude mcp add --transport stdio powerbi-desktop -- "C:\Program Files\PowerBI-MCP\powerbi-desktop-mcp-2.0.9.exe"

# Or read-only version
claude mcp add --transport stdio powerbi-desktop-readonly -- "C:\Program Files\PowerBI-MCP\powerbi-desktop-mcp-readonly-2.0.9.exe"
```

   This command will:
   - Add a new MCP server named "powerbi-desktop"
   - Configure it to use stdio transport (standard input/output)
   - Set the executable path

4. **Choose installation scope** when prompted:
   - **Local**: Private to your current project only
   - **Project**: Shared via `.mcp.json` file (committed to version control)
   - **User**: Available across all your projects (recommended)

5. **Restart Claude Code** or reload the window

The server will be available in all conversations. You can verify it's running by checking for MCP server indicators in the UI.

### Option 4: VS Code with Native MCP Support (Windows)

VS Code has native MCP support starting with version 1.102+. Requires GitHub Copilot.

**Note**: This server only works on Windows as it requires Power BI Desktop.

1. **Download the executable**:
   - **Full version**: `powerbi-desktop-mcp-2.0.9.exe`
   - **Read-only version**: `powerbi-desktop-mcp-readonly-2.0.9.exe`

2. **Place in a permanent location**: Example: `C:\Program Files\PowerBI-MCP\powerbi-desktop-mcp-2.0.9.exe`

3. **Create `.vscode/mcp.json` in your workspace**:

   ```json
   {
     "servers": {
       "powerbi-desktop": {
         "type": "stdio",
         "command": "C:\\Program Files\\PowerBI-MCP\\powerbi-desktop-mcp-2.0.9.exe",
         "args": []
       }
     }
   }
   ```

   **Tip**: Use Command Palette → "MCP: Add Server" → Select "Global" for all workspaces

4. **Restart VS Code**

5. **Enable agent mode**: In Copilot Chat, click the **Tools** button to enable MCP tools

See [VS Code MCP documentation](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) for more details.

## Getting Started

### 1. Start Power BI Desktop

Open Power BI Desktop and load a `.pbix` file that you want to work with. The MCP server will auto-discover running Power BI instances.

### 2. Start Your AI Assistant

Launch your chosen AI assistant:
- **Claude Desktop** or **Claude Code**: The Power BI MCP Server will start automatically in the background
- **VS Code with GitHub Copilot**: Open VS Code with your configured workspace, and the MCP server will be available in Copilot Chat (enable agent mode via the Tools button)

### 3. List Available Models

If you have multiple Power BI files open, ask your AI assistant:

```
"List my available Power BI models"
```

The AI will call `manage_model_connection` with `operation="list"` to show all running instances.

### 4. Select a Model

Tell the AI which model to connect to:

```
"Connect to model 1" or "Connect to [model name]"
```

### 5. Start Working!

Now you can interact with your Power BI model naturally:

**Explore your model:**
```
"Show me all the tables in my model"
"What columns does the Sales table have?"
"What measures are in the Finance table?"
```

**Analyze data:**
```
"Show me a preview of the Customers table"
"What are the distinct values in the Category column?"
"Run this DAX query: EVALUATE TOPN(10, Sales, [SalesAmount], DESC)"
```

**Create measures:**
```
"Create a measure called Total Revenue in the Measures table with this expression: SUM(Sales[Amount])"
"Add a Year-over-Year growth measure with percentage formatting"
```

**Manage relationships:**
```
"List all relationships in my model"
"Create a relationship from Sales[ProductID] to Products[ID]"
"Make the relationship between Sales and Date bidirectional"
```

**Search and discover:**
```
"Find all objects with 'Customer' in the name"
"Search for all measures that use the CALCULATE function"
```

**Performance analysis:**
```
"Show me VertiPaq statistics for the Sales table"
"Which columns have the highest cardinality?"
"Analyze the performance of this DAX query"
```

## Available Tools

### Model Management (1 unified tool)
- `manage_model_connection` - Discover, select, and manage Power BI model connections
  - `operation="list"` - List all running Power BI instances
  - `operation="select"` - Connect to a specific model
  - `operation="get_current"` - Get current connection info

### Model Properties (1 tool)
- `manage_model_properties` - Get and update global model properties, descriptions, cultures, annotations

### Data Exploration (1 unified tool)
- `list_objects` - Consolidated listing with 15 object types (now includes Shared M/Named Expressions)
  - Easily discover tables, measures, columns, relationships, hierarchies, calculation groups, KPIs, cultures, perspectives, partitions, UDFs, roles, calendars, and shared M expressions.

### Core Operations (3 tools)
- `run_dax` - Execute DAX queries (up to 1000 rows)
- `analyze_table` - Describe tables, preview data, get column statistics
- `get_model_info` - Export schema or view data sources

### Search & Discovery (1 unified tool)
- `search_model` — Find things in your model by name or by what their formulas contain.
  - What you can search
    - Names and descriptions: tables, columns, measures, calculated columns, relationships, hierarchies, calculation groups and items, perspectives, cultures
    - DAX expressions: measures, calculated columns, calculation items, KPI status/target/trend, row‑level security filters, calculated tables
    - Power Query (M): table partitions and shared M (named expressions)
  - How it works
    - Name search: find objects by name (supports wildcards `*` and `?`)
    - Text search: find names or descriptions that contain your text
    - DAX search: find DAX that contains your text (e.g., references, functions)
    - M search: find Power Query steps or sources by text
  - Lean defaults (token‑efficient)
    - Default `mode="name"`
    - Default `types=["tables","columns","measures","calculated_columns"]`
    - In name mode, measure and calculated column expressions are omitted by default
    - Results are limited to 50 items per type by default
  - Flags to expand detail
    - `includeExpressions: true` — include full expressions in name mode (token heavy)
    - `previewChars: N` — include `expression_preview` up to N chars instead of full expression
    - `limitPerType: N` — override the per-type cap (default 50)
  - Try asking
    - "Show relationships that involve the Date table"
    - "Which calculation items use SELECTEDVALUE?"
    - "Find KPIs that reference [Sales Amount]"
    - "Search M for Sql.Database connections"
    - "Do we have a perspective for executives?"

### Measure Management (1 unified tool)
- `manage_measure` - Create, update, delete measures with dynamic format strings

### Table Operations (1 unified tool)
- `manage_table` - Create, update, delete tables with partition support
  - Create tables using M (Power Query), SQL, DAX (calculated), or dataflow entities.
  - You can point M partitions at a Shared M (Named Expression) to reuse logic across tables.
  - After creation, the server reports whether it processed the table and surfaces any warnings (e.g., refresh issues) while still returning the new table details.

### Relationship Operations (1 unified tool)
- `manage_relationship` - Create, update, delete relationships with full control

### Partition Management (1 unified tool)
- `manage_partition` - Create, update, delete, refresh all partition types
  - Works with M (Power Query), Query (SQL), Calculated (DAX), and Entity (Dataflow) partitions in Import/DirectQuery/Dual modes.
  - M partitions can use a Shared M (Named Expression) instead of inlining the M text, so you maintain one source of truth.

### Advanced Model Features (9 tools)
- `manage_udf` - User-Defined Functions (create, update, delete with parameters)
- `manage_named_expression` - Create, read, update, and delete Shared M (Named Expressions)
  - Use these to centralize reusable M logic; partitions can reference them by name.
- `manage_calc_group` - Calculation Groups (create calculation items dynamically)
- `manage_hierarchy` - Hierarchies (create, update, delete with level management)
- `manage_kpi` - Key Performance Indicators (target, status, trend expressions)
- `manage_role` - Security Roles (row-level and object-level security)
- `manage_perspective` - Perspectives (filter model objects by user groups)
- `manage_culture` - Cultures (add languages/locales with annotations)
- `manage_translation` - Translations (translate captions and descriptions)

### Storage & Performance (2 tools)
- `get_vertipaq_stats` - VertiPaq statistics (storage, encoding, cardinality)
- `analyze_query_performance` - DAX query performance with detailed metrics

### Refresh Operations (1 tool)
- `refresh` - Refresh at partition, table, or model scope

## Example Use Cases

### 1. Model Documentation

```
"Generate a complete documentation of my Power BI model including all tables,
columns, measures, and relationships. Format it nicely."
```

### 2. Measure Creation Workflow

```
"I need to create a set of time intelligence measures for my Sales table:
- Total Sales
- Sales Last Year
- Sales Year-over-Year Growth %
- Sales Year-to-Date

Create these measures in the Measures table with appropriate formatting."
```

### 3. Relationship Analysis

```
"Analyze all relationships in my model and identify:
1. Inactive relationships
2. Bidirectional relationships
3. Many-to-many relationships
Explain when each might be problematic."
```

### 4. Performance Optimization

```
"Analyze the VertiPaq statistics for all tables and identify:
1. Columns with high cardinality that should be reviewed
2. Tables with poor compression ratios
3. Recommendations for optimization"
```

### 5. DAX Development

```
"I need a measure that calculates the customer retention rate. The measure should:
- Count unique customers in the current period
- Count unique customers who also appeared in the previous period
- Calculate the retention percentage
Create this measure with proper error handling and formatting."
```

### 6. User-Defined Functions

```
"Create a UDF called 'RollingAverage' that takes a measure and period count
and returns a rolling average. Include proper parameter descriptions for IntelliSense."
```

### 7. Multi-Language Model

```
"Add French and German translations to my model. Translate all table names,
measure names, and key descriptions. Use the culture codes fr-FR and de-DE."
```

### 8. Security Implementation

```
"Set up row-level security for our Sales model. Create roles for:
1. SalesManager - can see all regions
2. RegionalRep - can only see their assigned region
3. Finance - read-only access to sensitive columns

Include the appropriate DAX filters."
```

### 9. Time Intelligence Setup

```
"Create a calendar table for 2025 with Year, Quarter, Month hierarchies.
Then create time intelligence measures for:
- YTD Sales
- Prior Year Sales
- Year-over-Year Growth"
```

### 10. Table Management

```
"Create a new calculated table that aggregates sales by customer and month,
then set up a hierarchy with Customer > Month for analysis."
```

### 11. Shared M (Named Expressions) and M Partitions

Ask Claude naturally, no parameters needed:
```
"Create a reusable shared M expression called SimpleData that returns a tiny table with one column 'Col1' and one row 'Val1'. Then create a new table DimSimple that uses this shared expression."
```

What you’ll see:
- The shared expression is created
- A new table is added that reuses it
- A quick status telling you if the table processed, plus any warnings (e.g., refresh issues)

## Troubleshooting

### "No Power BI instances found"

**Solution:**
1. Make sure Power BI Desktop is running
2. Ensure you have a `.pbix` file open (not just Power BI Desktop without a file)
3. Try closing and reopening your PBIX file
4. Check that Power BI Desktop is the MSI or Store version (not a portable version)

### "Failed to connect to model"

**Solution:**
1. Make sure the PBIX file is fully loaded (not showing "Loading..." in Power BI)
2. Try disconnecting and reconnecting in Claude
3. Save and reopen your PBIX file
4. Check Windows Firewall isn't blocking local connections

### "Tool execution timed out"

**Solution:**
1. For large models, some operations may take longer
2. Try simplifying your query or request
3. If running DAX queries, add TOP N to limit results
4. Close other PBIX files to reduce resource usage

### ".mcpb installation fails in Claude Desktop"

**Solution:**
1. Make sure you have the latest version of Claude Desktop
2. Try redownloading the .mcpb file (may have been corrupted)
3. Check you have write permissions to the Claude Desktop extensions folder
4. Try Option 2 (manual .exe configuration) instead

### "Tools not showing up"

**For Claude Desktop/Code:**
1. Restart the application completely (not just close the window)
2. Check the MCP server is running (look for PbiMcp.exe in Task Manager)
3. Review the logs for error messages
4. Verify the configuration file syntax is correct (no missing commas or brackets)

**For VS Code:**
1. Check Output panel (View → Output, select "MCP Servers") for errors
2. Verify the path in `.vscode/mcp.json` uses escaped backslashes (`\\`)
3. Enable agent mode in Copilot Chat (click **Tools** button)
4. Restart VS Code completely

## Security & Privacy

- **Local-only**: The MCP server runs entirely on your local machine. No data is sent to external servers.
- **Read & Write Access**: The server can both read from and write to your Power BI models. Be cautious when the AI suggests changes (consider using the read-only version for exploration).
- **Connection Security**: Uses local Analysis Services connections (same as Power BI Desktop itself)
- **No Credentials**: No passwords or connection strings are exposed to the AI assistant
- **Trust Verification**: Always review server configuration before trusting it in your environment (both Claude and VS Code will prompt for confirmation)

## Limitations

- **Windows Only**: This tool only works on Windows (requires Analysis Services)
- **Power BI Desktop Only**: Does not work with Power BI Service or SQL Server Analysis Services
- **Active File Required**: Power BI Desktop must have a PBIX file open
- **Query Limits**: DAX query results are limited to 1000 rows by default
- **No Direct File Modification**: Changes are made through Analysis Services API, not by editing .pbix files

## Support

For issues, questions, or feature requests:
- Check the troubleshooting section above
- Review the project documentation
- Contact support or check for updates

## Author & License

**Developed by**: Maxim Anatsko
**Website**: [maxanatsko.com](https://maxanatsko.com)
**Copyright**: © 2025 Maxim Anatsko, WarpBI. All rights reserved.

### License Terms

This software is proprietary and confidential. By downloading, installing, or using the Power BI Desktop MCP Server, you agree to the following terms:

**Permitted Use:**
- Personal and commercial use of the software as provided
- Connection to Power BI Desktop for model management and analysis
- Integration with Claude Desktop and Claude Code applications

**Restrictions:**
- You may not modify, reverse engineer, decompile, or disassemble the software
- You may not redistribute, sublicense, rent, lease, or sell the software
- You may not remove or alter any copyright notices or proprietary markings
- Source code is not provided and may not be derived from the binary

**Warranty Disclaimer:**
THIS SOFTWARE IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NON-INFRINGEMENT. THE AUTHOR MAKES NO REPRESENTATIONS OR WARRANTIES ABOUT THE ACCURACY, RELIABILITY, COMPLETENESS, OR TIMELINESS OF THE SOFTWARE OR ITS RESULTS.

**Limitation of Liability:**
IN NO EVENT SHALL MAXIM ANATSKO, WARPBI, OR ANY CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

**Microsoft Disclaimer:**
This software is an independent, community-developed tool and is not affiliated with, endorsed by, or connected to Microsoft Corporation. Power BI, Analysis Services, and other Microsoft product names are trademarks of Microsoft Corporation.

## Acknowledgments

Built with:
- Model Context Protocol (MCP) by Anthropic
- Microsoft Analysis Services Tabular API
- .NET 8.0

Compatible with:
- Claude Desktop and Claude Code (Anthropic)
- VS Code with GitHub Copilot (Microsoft)
- Other MCP-compatible AI assistants

---

**Version**: 2.0.9
**MCP Protocol**: 2025-06-18
**Release Date**: November 2025
**Platform**: Windows 10/11
**Versions**: Full (26 tools) and Read-Only (9 tools - view and analyze only)
**Compatible AI Tools**: Claude Desktop, Claude Code, VS Code (with GitHub Copilot 1.102+), and other MCP-compatible assistants
