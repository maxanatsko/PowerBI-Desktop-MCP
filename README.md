# Power BI Desktop MCP Server

**Version 1.3.0** - Model Context Protocol Server for Power BI Desktop

> **Developed by Maxim Anatsko** | [maxanatsko.com](https://maxanatsko.com)
>
> **Note**: This is an independent, community-developed tool and is not affiliated with, endorsed by, or connected to Microsoft Corporation in any way.

## What is this?

The Power BI Desktop MCP Server is a tool that lets AI assistants like Claude interact with your Power BI models programmatically. It enables Claude to read your model structure, run DAX queries, create and modify measures, manage relationships, and perform advanced analytics - all through natural conversation.

Think of it as giving Claude "eyes and hands" to work with your Power BI models, allowing you to automate tasks, analyze data, and build solutions using AI assistance.

## Key Features

### 🎯 25 Powerful Tools for Power BI Model Operations

**Model Management**
- Auto-discover and connect to running Power BI Desktop instances
- List available models and select which one to work with
- Get current connection status

**Data Exploration**
- List and describe tables, columns, and measures
- Preview table data
- Export complete model schema
- Execute DAX queries
- Get column statistics and distinct values

**Measure Management**
- Create new DAX measures with formatting and organization
- Update existing measures
- Delete measures
- Create dedicated measures tables

**Relationship Operations**
- List all relationships with properties
- Create new relationships with full control over cardinality and cross-filter direction
- Update relationship properties
- Delete relationships

**Search & Discovery**
- Search for objects by name pattern (tables, columns, measures)
- Full-text search across DAX and M expressions
- Find calculated columns

**Advanced Analytics**
- Query performance analysis with execution metrics
- VertiPaq statistics for storage optimization
- Column cardinality and compression information

**Data Source Management**
- List data sources
- View partition information
- Analyze M partition expressions

## Prerequisites

Before installing, make sure you have:

1. **Windows 10/11** (Windows-only application)
2. **Power BI Desktop** installed ([Download MSI](https://www.microsoft.com/en-us/download/details.aspx?id=58494) or from Microsoft Store)
3. **Claude Desktop** or **Claude Code** application installed

Note: The `.exe` and `.mcpb` packages are self-contained and include all necessary runtime components. You do not need to install .NET separately.

## Installation

You can install the Power BI MCP Server in three ways:

### Option 1: Claude Desktop with .mcpb Package (Recommended)

The `.mcpb` package is the easiest way to install - it's a self-contained extension specifically for Claude Desktop.

1. **Download the package**: Get `powerbi-desktop-mcp-1.3.0.mcpb` from the releases

2. **Install the extension**:
   - **Simple method**: Double-click the `.mcpb` file. Claude Desktop will open and show the installation dialog.
   - **Alternative method**:
     - Open Claude Desktop
     - Go to Settings (gear icon) → Extensions
     - Click "Advanced settings" → "Extension Developer" section
     - Click "Install Extension..."
     - Select the downloaded `powerbi-desktop-mcp-1.3.0.mcpb` file
     - Click "Install" in the dialog

3. **Restart Claude Desktop**: Completely quit and restart the application (not just close the window)

The server will be automatically configured and ready to use. You'll see an MCP indicator in the bottom-right corner of the conversation input box when the server is active.

### Option 2: Claude Desktop with .exe (Manual Configuration)

If you prefer manual configuration or need more control:

1. **Download the executable**: Get `PbiMcp.exe` from the releases

2. **Place in a permanent location**: For example, `C:\Program Files\PowerBI-MCP\PbiMcp.exe`

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
      "command": "C:\\Program Files\\PowerBI-MCP\\PbiMcp.exe",
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

1. **Download the executable**: Get `PbiMcp.exe` from the releases

2. **Place in a permanent location**: For example, `C:\Program Files\PowerBI-MCP\PbiMcp.exe`

3. **Add the MCP server using the command line**:

   Open Claude Code and use the built-in terminal or command palette:

```bash
claude mcp add --transport stdio powerbi-desktop -- "C:\Program Files\PowerBI-MCP\PbiMcp.exe"
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

## Getting Started

### 1. Start Power BI Desktop

Open Power BI Desktop and load a `.pbix` file that you want to work with. The MCP server will auto-discover running Power BI instances.

### 2. Start Your AI Assistant

Launch Claude Desktop or Claude Code. The Power BI MCP Server will start automatically in the background.

### 3. List Available Models

If you have multiple Power BI files open, ask Claude:

```
"List my available Power BI models"
```

Claude will use the `list_available_models` tool to show you all running instances.

### 4. Select a Model

Tell Claude which model to connect to:

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

## Available Tools (v1.3.0)

### Model Management (3 tools)
- `list_available_models` - Discover all running Power BI instances
- `select_model` - Connect to a specific model by ID or index
- `get_current_model` - Get info about currently connected model

### Table Operations (6 tools)
- `list_tables` - List all tables
- `describe_table` - Get detailed table structure
- `preview_table_data` - Preview rows from a table
- `list_measures` - List all measures (with optional table filter)
- `export_model_schema` - Export complete schema as JSON
- `run_dax` - Execute DAX queries

### Column Operations (4 tools)
- `list_columns` - List columns with types and formats
- `get_column_values` - Sample distinct values from a column
- `get_column_summary` - Get statistics (min, max, null count)
- `list_calculated_columns` - List calculated columns with expressions

### Measure Management (4 tools)
- `create_measure` - Create new DAX measures
- `update_measure` - Modify existing measures
- `delete_measure` - Remove measures
- `create_measures_table` - Create dedicated measures table

### Relationship Operations (4 tools)
- `list_relationships` - List all relationships with properties
- `create_relationship` - Create new relationships
- `update_relationship` - Modify relationship properties
- `delete_relationship` - Remove relationships

### Search (2 tools)
- `search_objects` - Find objects by name pattern
- `search_string` - Full-text search in names and expressions

### Advanced Analysis (2 tools)
- `analyze_dax_query` - Query performance analysis
- `get_vertipaq_stats` - VertiPaq storage statistics

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

### "Tools not showing up in Claude"

**Solution:**
1. Restart Claude Desktop or Claude Code completely (not just close the window)
2. Check the MCP server is running (look for PbiMcp.exe in Task Manager)
3. Review the Claude logs for error messages
4. Verify the configuration file syntax is correct (no missing commas or brackets)

## Security & Privacy

- **Local-only**: The MCP server runs entirely on your local machine. No data is sent to external servers.
- **Read & Write Access**: The server can both read from and write to your Power BI models. Be cautious when Claude suggests changes.
- **Connection Security**: Uses local Analysis Services connections (same as Power BI Desktop itself)
- **No Credentials**: No passwords or connection strings are exposed to Claude

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
**Copyright**: © Maxim Anatsko, WarpBI

**Disclaimer**: This software is an independent, community-developed tool and is not affiliated with, endorsed by, or connected to Microsoft Corporation. Power BI and Analysis Services are trademarks of Microsoft Corporation.

## Acknowledgments

Built with:
- Model Context Protocol (MCP) by Anthropic
- Microsoft Analysis Services Tabular API
- .NET 8.0

---

**Version**: 1.3.0
**MCP Protocol**: 2025-06-18
**Release Date**: October 2024
**Platform**: Windows 10/11
