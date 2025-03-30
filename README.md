# QAnon is a dangerous cult. This archive is for research purposes only, and I do _not_ endorse any material in this repo.

# Q-Anon Posts/Drops MCP Server

An MCP (Model Context Protocol) server that provides access to a dataset of Q-Anon posts for anthropological/sociological research. This server allows AI assistants like Claude to search, filter, and analyze the Q-Anon drops.

Posts are drawn from https://github.com/jkingsman/JSON-QAnon.

### Warning: This tool was entirely vibe coded. Use at your own risk.

## Prerequisites

- Python 3.10 or higher
- `uv` package manager
- Claude Desktop (for Claude integration)

## Installation

1. Clone or download this repository to your local machine
2. Install the required packages using `uv`:

```bash
uv pip install "mcp[cli]"
```

## Usage

You can run the server directly with `uv`:

```bash
uv run qanon_mcp_server.py
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
    "qanon-explorer": {
      "command": "uv",
      "args": [
        "run",
        "/ABSOLUTE/PATH/TO/qanon_mcp_server.py"
      ]
    }
  }
}
```

Replace `/ABSOLUTE/PATH/TO/qanon_mcp_server.py` with the absolute path to your `qanon_mcp_server.py` file.

For Windows users, the path should use double backslashes:

```json
{
  "mcpServers": {
    "qanon-explorer": {
      "command": "uv",
      "args": [
        "run",
        "C:\\Users\\YourUsername\\Path\\To\\qanon_mcp_server.py"
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
- `qanon://authors` - List all unique authors
- `qanon://stats` - Get dataset statistics

### Tools

- **Search Posts** - Find posts containing specific keywords
- **Get Posts by Date** - Retrieve posts from a date range
- **Get Posts by Author ID** - Find posts by a specific author
- **Analyze Post** - Get detailed analysis of a specific post
- **Get Timeline Summary** - Generate a chronological timeline

## Example Queries for Claude

Once the MCP server is connected to Claude Desktop, you can ask questions like:

- "How many Q-Anon posts are in the dataset?"
- "Search for posts that mention 'storm'"
- "Show me posts from October 2020"
- "Analyze post #3725"
- "Create a timeline of Q-Anon posts from 2018"

## Troubleshooting

- If Claude Desktop doesn't show the hammer icon, check your configuration and restart Claude Desktop
- Ensure the `qposts.json` file is in the same directory as the script
- Check the output in the terminal for any error messages
- Make sure you're using the absolute path to the script in your Claude Desktop configuration
