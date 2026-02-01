# dotFiles

Personal macOS configuration synced via git.

## Structure

```
├── iterm2/          # iTerm2 preferences
│   └── com.googlecode.iterm2.plist
├── obsidian/        # Obsidian vault settings
│   ├── *.json       # Core config files
│   ├── plugins/     # Community plugins
│   ├── snippets/    # CSS snippets
│   └── themes/      # Installed themes
├── vscode/          # VS Code settings
│   ├── settings.json
│   ├── keybindings.json
│   ├── snippets/
│   └── extensions.txt
└── zsh/             # Zsh configuration
    ├── .zshrc
    └── .zshrc.local.template
```

## Setup on a New Mac

### Clone the repo

```bash
git clone https://github.com/pradeepvairamani/dotFiles.git ~/.dotfiles
```

### iTerm2

1. Open iTerm2 → **Preferences** → **General** → **Preferences**
2. Check **"Load preferences from a custom folder or URL"**
3. Set path to: `~/.dotfiles/iterm2`
4. Check **"Save changes to folder when iTerm2 quits"**
5. Restart iTerm2

### VS Code

```bash
# Copy settings
cp ~/.dotfiles/vscode/settings.json ~/Library/Application\ Support/Code/User/
cp ~/.dotfiles/vscode/keybindings.json ~/Library/Application\ Support/Code/User/
cp -r ~/.dotfiles/vscode/snippets ~/Library/Application\ Support/Code/User/

# Install extensions
cat ~/.dotfiles/vscode/extensions.txt | xargs -L 1 code --install-extension
```

### Zsh

```bash
# Backup existing .zshrc if needed
cp ~/.zshrc ~/.zshrc.backup

# Copy zshrc
cp ~/.dotfiles/zsh/.zshrc ~/.zshrc

# Create local secrets file from template
cp ~/.dotfiles/zsh/.zshrc.local.template ~/.zshrc.local
# Edit ~/.zshrc.local and add your secrets
```

### Obsidian

```bash
# Copy settings to your vault (replace YOUR_VAULT with your vault path)
VAULT=~/Library/Mobile\ Documents/iCloud~md~obsidian/Documents/YOUR_VAULT

cp ~/.dotfiles/obsidian/*.json "$VAULT/.obsidian/"
cp -r ~/.dotfiles/obsidian/plugins "$VAULT/.obsidian/"
cp -r ~/.dotfiles/obsidian/snippets "$VAULT/.obsidian/"
cp -r ~/.dotfiles/obsidian/themes "$VAULT/.obsidian/"

# If using Todoist plugin, copy your token
cp ~/.dotfiles/obsidian/todoist-token.template "$VAULT/.obsidian/todoist-token"
# Edit the file and add your API token
```

## Updating Settings

### iTerm2
Changes save automatically if "Save changes to folder when iTerm2 quits" is enabled.

### VS Code
```bash
cp ~/Library/Application\ Support/Code/User/settings.json ~/.dotfiles/vscode/
cp ~/Library/Application\ Support/Code/User/keybindings.json ~/.dotfiles/vscode/
code --list-extensions > ~/.dotfiles/vscode/extensions.txt
```

### Zsh
```bash
cp ~/.zshrc ~/.dotfiles/zsh/.zshrc
# Make sure to remove any secrets before committing!
```

### Obsidian
```bash
VAULT=~/Library/Mobile\ Documents/iCloud~md~obsidian/Documents/YOUR_VAULT
cp "$VAULT/.obsidian/"*.json ~/.dotfiles/obsidian/
cp -r "$VAULT/.obsidian/plugins" ~/.dotfiles/obsidian/
cp -r "$VAULT/.obsidian/snippets" ~/.dotfiles/obsidian/
cp -r "$VAULT/.obsidian/themes" ~/.dotfiles/obsidian/
# Remove todoist-token and workspace files before committing!
rm -f ~/.dotfiles/obsidian/todoist-token ~/.dotfiles/obsidian/workspace*.json
```

### Commit and push
```bash
cd ~/.dotfiles
git add -A
git commit -m "Update settings"
git push
```
