# cursor_customizations

Documented Cursor/VS Code customizations and agent rules.

## Non-default settings

### User-level settings (`/home/randy/.vscode/settings.json`)

- `ansible.python.interpreterPath`: `/home/randy/ansible-env/bin/python`

### Workspace-level settings (`/home/randy/repos/.vscode/settings.json`)

- `ansible.python.interpreterPath`: `/bin/python3`

### Project-level settings (`/home/randy/repos/ansible/.vscode/settings.json`)

- `ansible.python.interpreterPath`: `/usr/bin/python3`
- `yaml.schemas`: maps the Ansible lint schema URL to `file:///home/randy/repos/ansible/.ansible-lint`

## Rules

### Custom authoring rule (Markdown)

- In Markdown tables, visually align all `|` delimiters by column in monospace view.
- Ensure each table cell has at least one space after opening `|` and before closing `|`.
- Make separator-row dash counts match content column widths exactly.
- For multi-byte Unicode in table cells (for example em dash, ellipsis), count by display width.
- After editing any Markdown file, verify all tables in that file, not just edited ones.

### Custom coding rule (Ansible)

- Always use FQCN notation in playbooks, including updating existing code to FQCN where appropriate.
- Always trim any unneeded whitespace that will cause linting errors.
- Assume playbooks run from Ansible Automation Platform; variables not created in the playbook should come from surveys or `ansible.builtin.set_stats`.

### Custom safety rule (file changes)

- Do not delete source files; move them to a `.trash` folder within the project instead.

## Repo rule files

- No `.cursor/rules` files are currently present in this repository.

## Apply on a new machine

1. Clone this repository:
   - `git clone <your-repo-url> ~/repos/cursor_customizations`
2. Create target config folders:
   - `mkdir -p ~/.vscode`
   - `mkdir -p ~/repos/.vscode`
   - `mkdir -p ~/repos/ansible/.vscode`
3. Copy or merge settings (recommended: review before overwrite):
   - User settings: copy keys into `~/.vscode/settings.json`
   - Workspace settings: copy keys into `~/repos/.vscode/settings.json`
   - Ansible project settings: copy keys into `~/repos/ansible/.vscode/settings.json`
4. Optional symlink approach (if you want this repo as the single source of truth):
   - `ln -s ~/repos/cursor_customizations/settings/user.settings.json ~/.vscode/settings.json`
   - `ln -s ~/repos/cursor_customizations/settings/repos.settings.json ~/repos/.vscode/settings.json`
   - `ln -s ~/repos/cursor_customizations/settings/ansible.settings.json ~/repos/ansible/.vscode/settings.json`
5. Add rules if/when you create them:
   - Put repo rules in `~/repos/cursor_customizations/.cursor/rules/`
   - Keep this README updated when rules are added or changed.
