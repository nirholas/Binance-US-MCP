# Binance-US-MCP examples

MCP server for Binance.US exchange - spot trading, wallet management, and US-specific features

## Example 1

```bash
# Clone the repository
git clone https://github.com/nirholas/Binance-US-MCP.git
cd Binance-US-MCP

# Install dependencies
npm install

# Build the project
npm run build
```

## Example 2

```bash
BINANCE_US_API_KEY=your_api_key_here
BINANCE_US_API_SECRET=your_api_secret_here
```

## Example 3

```bash
# Run in development mode with hot reload
npm run dev

# Test with MCP Inspector
npm test
```

## Example 4

```bash
# Build the project
npm run build

# Start the server
npm start
```

## Example 5

```text
https://modelcontextprotocol.name/mcp/binance-us-mcp
```

## Example 6

```bash
curl -X POST https://modelcontextprotocol.name/mcp/binance-us-mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_ticker_price","arguments":{"symbol":"BTCUSD"}}}'
```

## Example 7

```bash
curl -X POST https://modelcontextprotocol.name/mcp/binance-us-mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_24h_stats","arguments":{"symbol":"ETHUSD"}}}'
```

## Example 8

```bash
curl -X POST https://modelcontextprotocol.name/mcp/binance-us-mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_order_book","arguments":{"symbol":"BTCUSD","limit":5}}}'
```


Every snippet above is taken from the [repository documentation](https://github.com/nirholas/Binance-US-MCP#readme).
