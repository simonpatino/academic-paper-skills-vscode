# Contributing

Thank you for your interest in contributing to academic-paper-skills-vscode!

## Ways to Contribute

- **New platform support**: Add writing standards for new academic platforms (SSRN, bioRxiv, etc.)
- **Script improvements**: Enhance the Python validation scripts
- **Bug fixes**: Fix issues with skill invocation or path resolution
- **Examples**: Add example papers and outlines
- **Documentation**: Improve installation or usage docs

## Guidelines

1. Keep all skill paths absolute (`~/.claude/skills/...`) — relative paths break in VS Code
2. Use `web_fetch` or `bash curl` for web search — not MCP-specific tools
3. Test your changes in both Copilot CLI terminal and VS Code Agent window
4. Follow the existing SKILL.md YAML frontmatter format:
   ```yaml
   ---
   name: skill-name
   description: ...
   trigger: /slash-command
   ---
   ```

## Submitting a PR

1. Fork the repository
2. Create a branch: `git checkout -b feature/my-improvement`
3. Make your changes
4. Open a pull request with a clear description
