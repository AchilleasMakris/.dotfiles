# My Hyprland Dotfiles

Personal Hyprland configuration files managed with GNU Stow.

## What's Included

### Core Hyprland Ecosystem
- **hypr**: Hyprland window manager configuration
- **hyprlock**: Screen locker for Hyprland 
- **hyprpaper**: Wallpaper daemon for Hyprland
- **waybar**: Status bar for Wayland
- **wofi**: Application launcher for Wayland
- **swaync**: Notification daemon for Wayland

### Terminal & Applications
- **kitty**: Terminal emulator configuration
- **rofi**: Application launcher (X11 fallback)

### Theming & Appearance
- **gtk**: GTK3/GTK4 theme configuration
- **qt-theme**: Qt5/Qt6 theme configuration (qt5ct, qt6ct, Kvantum)
- **wallust**: Dynamic wallpaper-based theming

## Prerequisites

Install required packages on Arch Linux:

```bash
# Core Hyprland ecosystem
sudo pacman -S hyprland hyprlock hyprpaper waybar wofi swaync

# Terminal and applications
sudo pacman -S kitty rofi

# Theming and appearance
sudo pacman -S gtk3 gtk4 qt5ct qt6ct kvantum wallust

# Dotfiles management
sudo pacman -S stow
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
