# CopyMe for Claude

The official [CopyMe](https://copyme.cc) plugin for Claude: write, polish and plan talking-video scripts with Claude, saved straight to your CopyMe teleprompter.

The plugin is in [`copyme/`](copyme). It bundles the CopyMe connector (`https://copyme.cc/mcp`), skills for writing, editing and planning scripts, and the commands `/copyme:write`, `/copyme:polish` and `/copyme:plan`. See its [README](copyme/README.md).

## Install

- **Claude (web, desktop, Cowork):** Customize > Plugins > Add > Add marketplace, then enter `ebenezerdon/copyme-claude` and add **CopyMe**. Connect the CopyMe connector from the plugin's Connectors tab.
- **Claude Code:**

  ```
  /plugin marketplace add ebenezerdon/copyme-claude
  /plugin install copyme@copyme
  ```

Setup help: https://copyme.cc/claude · Support: copyme@ebenezerdon.com
