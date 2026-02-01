# dotFiles

Personal macOS configuration synced via git.

## Structure

```
├── iterm2/          # iTerm2 preferences
│   └── com.googlecode.iterm2.plist
└── vscode/          # VS Code settings
    ├── settings.json
    ├── keybindings.json
    ├── snippets/
    └── extensions.txt
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

## Updating Settings

### iTerm2
Changes save automatically if "Save changes to folder when iTerm2 quits" is enabled.

### VS Code
```bash
# Export current settings
cp ~/Library/Application\ Support/Code/User/settings.json ~/.dotfiles/vscode/
cp ~/Library/Application\ Support/Code/User/keybindings.json ~/.dotfiles/vscode/
code --list-extensions > ~/.dotfiles/vscode/extensions.txt
```

### Commit and push
```bash
cd ~/.dotfiles
git add -A
git commit -m "Update settings"
git push
```
