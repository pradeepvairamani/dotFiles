# dotFiles

Personal macOS configuration synced via git.

## Structure

```
├── iterm2/          # iTerm2 preferences
│   └── com.googlecode.iterm2.plist
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

### Commit and push
```bash
cd ~/.dotfiles
git add -A
git commit -m "Update settings"
git push
```
