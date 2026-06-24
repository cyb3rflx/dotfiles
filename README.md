# dotfiles

My personal dotfiles, managed with a small Bash setup script. It backs up any
existing configuration, installs [Starship](https://starship.rs), and symlinks
the tracked files into place.

## What's included

| File                     | Purpose                          |
| ------------------------ | -------------------------------- |
| `.bashrc`                | Bash shell configuration         |
| `.config/starship.toml`  | Starship prompt configuration    |

## Requirements

- Bash
- `curl` (used to install Starship)
- A GNU userland (`cp --parents` is GNU-specific)

## Usage

```bash
git clone https://github.com/cyb3rflx/dotfiles.git
cd dotfiles
./setup
```

The script is safe to run more than once.

## What the script does

1. **Backup** — Each tracked file that already exists in `$HOME` (and isn't
   already a symlink) is copied to `backup/` before anything is changed.
   A manifest at `backup/backup_files.txt` records what has been saved, so a
   re-run only backs up files that aren't backed up yet, an interrupted run
   safely resumes instead of skipping or overwriting.
2. **Install Starship** — Fetches and runs the official install script.
3. **Symlink** — Links each tracked file from the repo into `$HOME`, creating
   parent directories (e.g. `~/.config`) as needed.


> **Note:** The `backup/` directory holds copies of your real config files and
> is excluded via `.gitignore`. Keep it that way so backups never get pushed.

## Disclaimer

These dotfiles are provided "as is", without warranty of any kind. The setup
script modifies files in your home directory, use it at your own risk and
review it before running. I take no responsibility for any data loss or damage
that may result from its use.
