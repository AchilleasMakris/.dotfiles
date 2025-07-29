# My Hyprland Dotfiles

Personal Hyprland configuration files managed with GNU Stow.

## What's Included

- **hypr**: Hyprland window manager configuration
- **waybar**: Status bar for Wayland
- **kitty**: Terminal emulator configuration
- **rofi**: Application launcher

## Prerequisites

Install required packages on Arch Linux:

```bash
sudo pacman -S hyprland waybar kitty rofi stow
```

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/AchilleasMakris/.dotfiles.git ~/dotfiles
   cd ~/dotfiles
   ```

2. Use stow to create symlinks:
   ```bash
   # Install all configs
   stow */
   
   # Or install individual configs
   stow hypr
   stow waybar
   stow kitty
   stow rofi
   ```

3. Restart Hyprland or reload configs

## Usage

### Managing Configs

- **Add new config**: Create directory structure and use `stow <package>`
- **Remove config**: Use `stow -D <package>`
- **Restow config**: Use `stow -R <package>`

### Making Changes

1. Edit files in the dotfiles directory
2. Changes are automatically reflected (symlinked)
3. Commit and push changes:
   ```bash
   git add .
   git commit -m "Update configuration"
   git push
   ```

## Directory Structure

```
dotfiles/
├── hypr/
│   └── .config/
│       └── hypr/
│           ├── hyprland.conf
│           ├── hypridle.conf
│           └── ...
├── waybar/
│   └── .config/
│       └── waybar/
│           ├── config
│           └── style.css
└── ...
```

Each directory represents a "stow package" that can be independently managed.
