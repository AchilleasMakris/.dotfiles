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

### Arch Linux
```bash
# Core Hyprland ecosystem
sudo pacman -S hyprland hyprlock hyprpaper waybar wofi swaync

# Terminal and applications
sudo pacman -S kitty rofi

# Theming and appearance
sudo pacman -S gtk3 gtk4 qt5ct qt6ct kvantum-qt5 wallust

# Dotfiles management
sudo pacman -S stow git
```

### Ubuntu/Debian
```bash
# Update package list
sudo apt update

# Install dependencies
sudo apt install git stow

# Hyprland (requires adding PPA or building from source)
# Follow official Hyprland installation guide for Ubuntu

# Terminal and basic apps
sudo apt install kitty rofi

# GTK theming
sudo apt install gtk-3-examples gtk-4-examples
```

### Fedora
```bash
# Core packages
sudo dnf install hyprland waybar wofi kitty rofi stow git

# Theming packages
sudo dnf install gtk3-devel gtk4-devel qt5ct qt6ct
```

### Other Distributions
- Install `stow` and `git` from your package manager
- Follow the [official Hyprland installation guide](https://hyprland.org/)
- Install the applications listed in "What's Included" section

## Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/AchilleasMakris/.dotfiles.git ~/dotfiles
   cd ~/dotfiles
   ```

2. **Backup existing configurations (recommended):**
   ```bash
   # Backup your current configs if they exist
   mv ~/.config/hypr ~/.config/hypr.backup 2>/dev/null || true
   mv ~/.config/waybar ~/.config/waybar.backup 2>/dev/null || true
   mv ~/.config/kitty ~/.config/kitty.backup 2>/dev/null || true
   # ... backup other configs as needed
   ```

3. **Use stow to create symlinks:**
   ```bash
   # Install all configurations at once
   stow */
   
   # OR install individual packages (recommended for first-time setup)
   stow hypr          # Hyprland window manager
   stow waybar        # Status bar
   stow kitty         # Terminal emulator
   stow wofi          # Application launcher
   stow rofi          # Alternative launcher
   stow gtk           # GTK theming
   stow qt-theme      # Qt theming
   stow hyprlock      # Screen locker
   stow hyprpaper     # Wallpaper daemon
   stow swaync        # Notifications
   stow wallust       # Dynamic theming
   ```

4. **Set environment variables (add to your shell profile):**
   ```bash
   # Add to ~/.bashrc, ~/.zshrc, or ~/.profile
   export QT_QPA_PLATFORMTHEME=qt5ct
   export QT_STYLE_OVERRIDE=kvantum
   ```

5. **Restart or reload:**
   - Log out and back in, or
   - Restart Hyprland: `hyprctl reload`

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

## Troubleshooting

### Common Issues

**Stow conflicts:**
```bash
# If stow complains about conflicts, remove existing files/symlinks first
rm ~/.config/hypr/hyprland.conf  # Remove conflicting file
stow hypr                        # Then restow
```

**Missing packages:**
- Check if all required packages are installed for your distribution
- Some packages might have different names on different distros
- For AUR packages on Arch: `yay -S package-name`

**Theming not working:**
```bash
# Ensure environment variables are set
echo $QT_QPA_PLATFORMTHEME  # Should show qt5ct
echo $QT_STYLE_OVERRIDE     # Should show kvantum

# Restart applications after setting themes
```

**Hyprland not starting:**
- Check Hyprland logs: `journalctl -u hyprland`
- Ensure your GPU drivers are properly installed
- Verify Wayland support

### Updating Configs

```bash
# Pull latest changes
cd ~/dotfiles
git pull

# Restow changed packages
stow -R hypr waybar  # etc.
```

## Customization

### Adding Your Own Configs

1. Create new directory with proper structure:
   ```bash
   mkdir -p mynewapp/.config/mynewapp
   cp ~/.config/mynewapp/* mynewapp/.config/mynewapp/
   ```

2. Stow the new package:
   ```bash
   stow mynewapp
   ```

3. Commit and push:
   ```bash
   git add mynewapp/
   git commit -m "Add mynewapp configuration"
   git push
   ```

### Modifying Existing Configs

Since configurations are symlinked, you can edit them directly:
- Edit files in `~/dotfiles/` directory
- Changes are immediately active
- Commit and push to save changes

## Notes

- These configurations are optimized for **1920x1080** displays
- Some paths might need adjustment for your system
- Wallpapers and themes can be customized in their respective config files
- The setup includes both Wayland (wofi) and X11 (rofi) app launchers for compatibility
