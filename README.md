# agent-tools

Agent tooling packages - pi extensions, MCP servers, and more.

## Packages

| Package                                         | Description                           | npm                           |
| ----------------------------------------------- | ------------------------------------- | ----------------------------- |
| [@walterra/pi-charts](./packages/pi-charts)     | Vega-Lite chart extension for pi      | `npm i @walterra/pi-charts`   |
| [@walterra/pi-graphviz](./packages/pi-graphviz) | Graphviz DOT diagram extension for pi | `npm i @walterra/pi-graphviz` |

## Package Naming Convention

| Package              | Target          | Description                |
| -------------------- | --------------- | -------------------------- |
| `@walterra/pi-*`     | pi-coding-agent | Extensions, skills, themes |
| `@walterra/mcp-*`    | Any MCP client  | MCP servers (future)       |
| `@walterra/cursor-*` | Cursor          | Rules, configs (future)    |

## Development

```bash
# Install dependencies
pnpm install

# Build all packages
pnpm build
```

## License

MIT
