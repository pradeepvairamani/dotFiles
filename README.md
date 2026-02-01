# iTerm2 Settings

Personal iTerm2 configuration synced via git.

## Setup on a New Mac

1. Clone this repo:
   ```bash
   git clone <your-repo-url> ~/.iterm2-settings
   ```

2. Open iTerm2 and configure it to use this folder:
   - Go to **Preferences** → **General** → **Preferences**
   - Check **"Load preferences from a custom folder or URL"**
   - Set the path to: `~/.iterm2-settings`
   - Check **"Save changes to folder when iTerm2 quits"**

3. Restart iTerm2 to load the settings.

## Updating Settings

After making changes in iTerm2:

```bash
cd ~/.iterm2-settings
git add -A
git commit -m "Update iTerm2 settings"
git push
```

## Pulling Updates on Another Mac

```bash
cd ~/.iterm2-settings
git pull
```

Then restart iTerm2 to apply changes.
