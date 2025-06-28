# Airbnb MCP Server

MCP Server for searching Airbnb and get listing details. Uses streamable HTTP transport for communication.

## Tools

1. `airbnb_search`
   - Search for Airbnb listings
   - Required Input: `location` (string)
   - Optional Inputs:
     - `placeId` (string)
     - `checkin` (string, YYYY-MM-DD)
     - `checkout` (string, YYYY-MM-DD)
     - `adults` (number)
     - `children` (number)
     - `infants` (number)
     - `pets` (number)
     - `minPrice` (number)
     - `maxPrice` (number)
     - `cursor` (string)
     - `ignoreRobotsText` (boolean)
   - Returns: Array of listings with details like name, price, location, etc.

2. `airbnb_listing_details`
   - Get detailed information about a specific Airbnb listing
   - Required Input: `id` (string)
   - Optional Inputs:
     - `checkin` (string, YYYY-MM-DD)
     - `checkout` (string, YYYY-MM-DD)
     - `adults` (number)
     - `children` (number)
     - `infants` (number)
     - `pets` (number)
     - `ignoreRobotsText` (boolean)
   - Returns: Detailed listing information including description, host details, amenities, pricing, etc.

## Features

- Respects Airbnb's robots.txt rules
- Uses cheerio for HTML parsing
- No API key required
- Returns structured JSON data
- Reduces context load by flattening and picking data

## Setup

### Installing on Claude Desktop

This server uses streamable HTTP transport and runs as an Express server on port 3000.

Before starting make sure [Node.js](https://nodejs.org/) and [pnpm](https://pnpm.io/) are installed on your desktop.

1. Start the server:

```bash
pnpx -y gartmeier/mcp-server-airbnb
```

To ignore robots.txt for all requests, use the `--ignore-robots-txt` flag:

```bash
pnpx -y gartmeier/mcp-server-airbnb --ignore-robots-txt
```

2. Go to: Settings > Developer > Edit Config

3. Add the following to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "airbnb": {
      "transport": {
        "type": "http", 
        "url": "http://localhost:3000/mcp"
      }
    }
  }
}
```

4. Restart Claude Desktop and plan your next trip that include Airbnbs!

## Build (for devs)

```bash
pnpm install
pnpm run build
```

## License

This MCP server is licensed under the MIT License.

## Disclaimer

Airbnb is a trademark of Airbnb, Inc.
OpenBnB is not related to Airbnb, Inc. or its subsidiaries
