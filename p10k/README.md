# Powerlevel10k Setup

Personal zsh + Oh My Zsh + Powerlevel10k config.

## Prerequisites

```bash
sudo apt install zsh git
chsh -s $(which zsh)
```

## 1. Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 2. Install Powerlevel10k

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## 3. Install MesloLGS NF fonts

The four `.ttf` files under `fonts/` are required for p10k icons to render correctly.

### Windows (host)

Right-click each `.ttf` in `fonts/` → **Install for all users**.

### macOS

```bash
cp fonts/*.ttf ~/Library/Fonts/
```

### Linux

```bash
mkdir -p ~/.local/share/fonts
cp fonts/*.ttf ~/.local/share/fonts/
fc-cache -f -v
```

## 4. Configure terminal font

Set the terminal font to **MesloLGS NF**.

| Terminal | Path |
|----------|------|
| Windows Terminal | Settings → Profile → Appearance → Font face |
| VS Code | `terminal.integrated.fontFamily`: `"MesloLGS NF"` |
| iTerm2 | Preferences → Profiles → Text → Font |
| GNOME Terminal | Preferences → Profile → Custom font |

## 5. Deploy config files

```bash
cp .zshrc ~/.zshrc
cp .p10k.zsh ~/.p10k.zsh
exec zsh
```

> **Note:** Copy the files directly. Do not paste contents into the terminal to avoid bracketed paste issues (`[200~`).

---

## Reconfigure prompt

```bash
p10k configure
```

This rewrites `~/.p10k.zsh` interactively.

---

## Troubleshooting

**Icons show as `?` or boxes**
Font is not applied. Verify the terminal font is set to `MesloLGS NF` and restart the terminal.

**`[oh-my-zsh] theme 'powerlevel10k/powerlevel10k' not found`**
Step 2 was skipped or cloned to the wrong location. Re-run the clone command.

**CRLF line endings (`^M`)**
```bash
sed -i 's/\r//' ~/.zshrc ~/.p10k.zsh
```

**Instant prompt warnings**
Move any code that prints output or reads input above the instant-prompt block in `~/.zshrc`, or run `p10k configure` and choose to silence the warning.
