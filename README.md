# agents-lib

Personal Cursor global agents for syncing between machines.

Agents live in this repo as `.md` files. On each machine, `~/.cursor/agents/<name>.md` should be a symlink into this folder.

## Add a new agent

1. Create the agent under this repo (or copy it in from elsewhere):

```bash
# add <name>.md, then:
cd ~/Documents/agents-lib && git add <name>.md && git commit -m "Add <name> agent"
```

2. Symlink it into Cursor’s global agents dir:

```bash
ln -s ~/Documents/agents-lib/<name>.md ~/.cursor/agents/<name>.md
```

If the agent already exists only under `~/.cursor/agents/<name>.md`:

```bash
mv ~/.cursor/agents/<name>.md ~/Documents/agents-lib/<name>.md
ln -s ~/Documents/agents-lib/<name>.md ~/.cursor/agents/<name>.md
cd ~/Documents/agents-lib && git add <name>.md && git commit -m "Add <name> agent"
```

## Install on an empty machine

```bash
git clone <this-repo-url> ~/Documents/agents-lib
mkdir -p ~/.cursor/agents
cd ~/Documents/agents-lib
for f in *.md; do
  [ "$f" = "README.md" ] && continue
  ln -s "$(pwd)/$f" ~/.cursor/agents/$f
done
```
