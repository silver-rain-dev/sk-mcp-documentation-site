# SK MCP Documentation

Documentation site for MCP (Model Context Protocol) servers built by [skylarchen.dev](https://skylarchen.dev/).

Built with [Hugo](https://gohugo.io/) and the [Hextra](https://imfing.github.io/hextra/) theme.

## Documented MCPs

- **SK Wwise MCP** — AI-powered Wwise authoring through 95 tools across 12 servers

## Local Development

```bash
# Install Hugo (extended edition required)
# https://gohugo.io/installation/

# Clone with submodules
git clone --recurse-submodules https://github.com/silver-rain-dev/sk-mcp-documentation-site.git
cd sk-mcp-documentation-site

# Start dev server
hugo server --buildDrafts
```

Site runs at `http://localhost:1313`.

## Project Structure

```
content/          # Markdown pages
assets/           # Images processed by Hugo (cards, etc.)
static/           # Static assets served as-is (logo, etc.)
themes/hextra/    # Hextra theme (git submodule)
hugo.toml         # Site configuration
```
