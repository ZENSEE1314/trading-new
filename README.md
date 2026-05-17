# AI Trader

Railway-ready AI crypto trading app with:

- Express dashboard and API server
- Always-on trading bot launched from `entry.js`
- Agent coordinator, strategy lab, optimizer, Kronos/swarm signals, and trail watchdog
- PostgreSQL-backed user, trade, log, strategy, and wallet data
- Static dashboard assets in `public/`

## Start

```bash
npm install
npm start
```

`npm start` runs `node entry.js`, which binds `/health` immediately for Railway, loads the full server, then starts the trading bot.

## Railway

Railway uses `railway.toml`:

```toml
[deploy]
startCommand = "npm start"
healthcheckPath = "/health"
```

Set required secrets in Railway variables, using `.env.example` as the template. Never enable withdrawal permissions on exchange API keys.

## Important Files

- `entry.js` - Railway entrypoint and healthcheck bootstrap
- `server.js` - Express app, routes, static dashboard, API surface
- `bot.js` - trading bot lifecycle, Telegram commands, watchdog startup
- `cycle.js` - core trading cycle
- `agents/` - AI agent framework
- `routes/` - authenticated and admin API routes
- `public/` - dashboard, chart, copy-trade UI, and assets

## Risk

This app can place real trades. Test with small size, keep API keys restricted to trading/read access, and understand that crypto futures can lose money quickly.
