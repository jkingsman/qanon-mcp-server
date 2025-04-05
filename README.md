## QAnon is a dangerous cult. This archive is for research purposes only, and I do _not_ endorse any material in this repo.

# Q-Anon Posts/Drops MCP Server

![](https://badge.mcpx.dev?type=server 'qanon-mcp')
[![smithery badge](https://smithery.ai/badge/@jkingsman/qanon-mcp-server)](https://smithery.ai/server/@jkingsman/qanon-mcp-server)

An MCP (Model Context Protocol) server that provides access to a dataset of Q-Anon posts for anthropological/sociological research. This server allows AI assistants like Claude to search, filter, and analyze the Q-Anon drops.

Posts are drawn from https://github.com/jkingsman/JSON-QAnon. You can learn more about how the source data was composed there, as well as find alternate formats, schemas, etc.

### Warning: This tool was entirely vibe coded. Use at your own risk.

## Prerequisites

- Python 3.10 or higher
- `uv` package manager
- Claude Desktop (for Claude integration)

## Installation

This tool is compatible with `uvx` and doesn't need to be cloned/installed.

### Installing via Smithery

To install qanon-mcp-server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@jkingsman/qanon-mcp-server):

```bash
npx -y @smithery/cli install @jkingsman/qanon-mcp-server --client claude
```

### Manual

1. Clone or download this repository to your local machine
2. Install the required packages using `uv`:

```bash
uv pip install -e .
```

## Usage

You can run the server directly with `uvx`:

```bash
uvx qanon_mcp
```

## Claude Desktop Integration

To use this MCP server with Claude Desktop:

1. Make sure you have [Claude Desktop](https://claude.ai/download) installed
2. Open the Claude menu and select "Settings..."
3. Click on "Developer" in the left-hand bar and then "Edit Config"
4. Add the following configuration to the `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "qanon_mcp": {
      "command": "uvx",
      "args": [
        "qanon_mcp"
      ]
    }
  }
}
```

or, if you don't have `uvx` installed:

```json
{
  "mcpServers": {
    "qanon_mcp": {
      "command": "uv",
      "args": [
        "tool",
        "run",
        "qanon_mcp"
      ]
    }
  }
}
```


5. Save the file and restart Claude Desktop
6. Start a new conversation in Claude Desktop
7. You should see a hammer icon in the input box, indicating that tools are available

## Features

### Resources

- `qanon://posts/count` - Get the total number of posts
- `qanon://posts/{post_id}` - Access a specific post by ID
- `qanon://posts/raw/{post_id}` - Get the raw JSON data for a specific post
- `qanon://authors` - List all unique authors
- `qanon://stats` - Get dataset statistics

### Tools

- **get_post_by_id_tool** - Retrieve a specific post by its ID
- **search_posts** - Find posts containing specific keywords or phrases
- **get_posts_by_date** - Retrieve posts from a specific date range
- **get_posts_by_author_id** - Find posts by a specific author ID
- **analyze_post** - Get detailed analysis of a specific post including references and context
- **get_timeline_summary** - Generate a chronological timeline, optionally within a date range
- **word_cloud_by_post_ids** - Generate a word frequency analysis for posts within a specified ID range
- **word_cloud_by_date_range** - Generate a word frequency analysis for posts within a specified date range

## Example Queries for Claude

Once the MCP server is connected to Claude Desktop, you can ask questions like:

- "How many Q-Anon posts are in the dataset?"
- "Search for posts that mention 'storm'"
- "Show me posts from October 2020"
- "Analyze post #3725"
- "Create a timeline of Q-Anon posts from 2018"
- "Generate a word cloud for Q-Anon posts between January and March 2019"
- "Get the raw data for post #4500"
- "What are the most common words used in posts #1000-2000?"

## Troubleshooting

- If Claude Desktop doesn't show the hammer icon, check your configuration and restart Claude Desktop
- Ensure the `posts.json` file is in the same directory as the script
- Check the output in the terminal for any error messages
- Make sure you're using the absolute path to the script in your Claude Desktop configuration
