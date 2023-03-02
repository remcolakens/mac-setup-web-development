# Mac Setup for Web Development [2024]

In this article I want to share with you my macOS setup for web development.

- [Mac Setup for Web Development \[2024\]](#mac-setup-for-web-development-2024)
- [MacBook Pro Specifications](#macbook-pro-specifications)
- [System Settings](#system-settings)
- [System Settings (Terminal)](#system-settings-terminal)
- [Homebrew](#homebrew)
  - [GUI Applications](#gui-applications)
  - [Terminal Applications](#terminal-applications)
  - [Optional Applications](#optional-applications)
- [iTerm2](#iterm2)
  - [iTerm2 Colors + Font](#iterm2-colors--font)
- [Shell configuration](#shell-configuration)
  - [Zsh](#zsh)
  - [Starship Theme](#starship-theme)
    - [Config starship theme](#config-starship-theme)
  - [Oh My Zsh Plugins](#oh-my-zsh-plugins)
  - [Zsh Configuration File (_.zshrc_):](#zsh-configuration-file-zshrc)
  - [Fish](#fish)
  - [Starship Theme](#starship-theme-1)
    - [Config starship theme](#config-starship-theme-1)
  - [Fish Variables](#fish-variables)
  - [Fish Configuration File (_.config.fish_):](#fish-configuration-file-configfish)
  - [Fnm](#fnm)
  - [Gnupg as SSH agent (optional)](#gnupg-as-ssh-agent-optional)
  - [Functions](#functions)
    - [unset](#unset)
    - [envsource](#envsource)
    - [gpg-decrypt](#gpg-decrypt)
    - [gpg-encrypt](#gpg-encrypt)
  - [Reset shell](#reset-shell)
- [VS Code](#vs-code)
  - [Extensions](#extensions)
  - [JSON Settings](#json-settings)
- [Sublime](#sublime)
  - [General](#general)
  - [Extensions](#extensions-1)
  - [JSON Settings](#json-settings-1)
- [Git](#git)
- [SSH](#ssh)
- [OpenPGP](#openpgp)
  - [SSH with OpenPGP](#ssh-with-openpgp)
  - [More information about OpenPGP](#more-information-about-openpgp)
  - [Troubleshooting](#troubleshooting)
- [Fast Node Manager (fnm) for Node.js](#fast-node-manager-fnm-for-nodejs)
  - [Configuration](#configuration)
- [Git project folder](#git-project-folder)

# MacBook Pro Specifications

- 16-inch
- Apple MacBook Pro, M2 Pro 12‑Core CPU, 19‑Core GPU and 16‑Core Neural Engine
- 32 GB RAM
- 512 GB SSD
- QWERTY = English (USA)
- macOS Sonoma (14.2.1)

# System Settings

- Profile
  - Set avatar
  - iCloud
    - Disable
- Network
  - Firewall
    - On
    - Options: Enable stealth mode
- Notifications
  - Off
- General
  - Software Update: Update All
  - AirDrop: No One
  - Sharing
    - Make sure everything is off
    - Change computer name (local hostname)
  - Time Machine: Configure when required
- Appearance
  - Auto
- Accessibility
  - Display
    - Shake mouse pointer to locate: Off
- Control Centre
  - Battery: Show Percentage
- Siri & Spotlight
  - Disable
- Privacy & Security
  - Analytics & Improvements: Off
  - Apple advertising: Off
  - Screen recording: Firefox
  - FileVault: On
- Desktop & Dock
  - Remove most applications from Dock
  - Smaller Dock
  - Minimise windows using: Scale Effect
  - Magnification: Off
  - Automatic Hide
  - Show recent applications in Dock: Off
  - Show indicators for open applications: On
  - Click wallpaper to reveal desktop: Only in stage manager
  - Stage manager: Off
  - Hot Corners: Disable all
- Display
  - True Tone: On
- Wallpaper
  - Dynamic
- Lock Screen
  - Start Screen Saver when inactive: Never
  - Turn display off (battery): 5 minutes
  - Turn display off (power): 10 minutes
  - Require password: Immediately
- Touch ID & Password
  - Enable RH-finger
  - Enable LH-finger
- Game Center
  - Disable
- Keyboard
  - Key repeat rate: 10/10
  - Delay until repeat: 10/10
  - Keyboard Shortcuts
    - Disable Launchpad & Dock
    - Disable Mission control
    - Disable Spotlight
    - Disable Accessibility
  - Text Input
    - Edit
      - Disable Correct spelling automatically
      - Disable Capitalise word automatically
      - Disable Add full stop with double-space
      - Disable Use smart quotes and dashes
      - Use `"` for double quotes
      - Use `'` for single quotes
- Trackpad
  - Point & Click
    - Tap to Click
    - Look up & data detectors: Off
    - Speed: 4/10
  - Scroll & Zoom
    - Natural scrolling: Off
  - More Gestures
    - Notification centre: Off
    - Mission Control: Off
    - Launchpad: Off
    - Show desktop: Off
- Printers & Scanners
  - Add printer/scanner when required
- Finder
  - General
    - New Finder: Desktop
  - Hide all Tags
  - Sidebar
    - Enable
      - AirDrop
      - Applications
      - Desktop
      - Documents
      - Downloads
      - Pictures
      - _(Your account name)_
    - Disable
      - iCloud folders
      - Tags
  - Advanced
    - Show all filename extensions
    - Remove Items from Bin after 30 Days
- Widget
  - Remove widgets
- Storage
  - Remove Garage Band & Sound Library
  - Remove iMovie
- Desktop
  - Right click > Sort By > Snap to Grid

# System Settings (Terminal)

Override more system settings from the terminal...

```
# change computer name
sudo scutil --set ComputerName "newname"
sudo scutil --set LocalHostName "newname"
sudo scutil --set HostName "newname"

# take screenshots as jpg (usually smaller size) and not png
defaults write com.apple.screencapture type jpg

# do not open previous previewed files (e.g. PDFs) when opening a new one
defaults write com.apple.Preview ApplePersistenceIgnoreState YES

# show Library folder
chflags nohidden ~/Library

# show hidden files
defaults write com.apple.finder AppleShowAllFiles YES

# show path bar
defaults write com.apple.finder ShowPathbar -bool true

# show status bar
defaults write com.apple.finder ShowStatusBar -bool true

# set dock animation speed to 600ms
defaults write com.apple.dock autohide-time-modifier -float 0.6;

# restart dock
killall Dock;

# restart finder
killall Finder;
```

# Homebrew

Install [Homebrew](https://brew.sh) as package manager for macOS:

```
# paste in terminal and follow the instructions
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Update everything in Homebrew to recent version:

```
brew update
```

Install GUI applications (read more about these in GUI Applications):

```
brew install --cask \
  bitwarden \
  alfred \
  google-chrome  \
  firefox \
  iterm2 \
  visual-studio-code \
  bruno \
  github \
  https://raw.githubusercontent.com/Homebrew/homebrew-cask/9c7cef6f712515f8b87983685f0e82047362e08c/Casks/sublime-text.rb \
  spotify \
  rectangle \
  appcleaner \
  slack \
  discord \
  vlc \
  figma \
  keyboardcleantool \
  betterdisplay \
  imageoptim \
  handbrake \
  the-unarchiver \
  tunnelblick
```

Install terminal applications (read more about these in Terminal Applications):

```
brew install \
  wget \
  svgo \
  git \
  openssl \
  commitizen
```

Optional: These are applications I like to use in my specific setup

```
brew install --cask \
  yubico-authenticator \
  logitech-options
```

## GUI Applications

- [Bitwarden](https://bitwarden.com/) (password manager)
  - Preferences
    - Vault timeout: 5 minutes
    - Clear clipboard: 30s
    - Enable Touch ID
    - Start automatically on login
    - Theme: Dark
- [Alfred](https://www.alfredapp.com/) (spotlight alternative)
  - Use license
  - Set shortcut to: option + space
  - Launch Alfred at login
  - Appearance
    - Alfred macOS Dark
    - Hide hat on Alfred window
- [Google Chrome](https://www.google.com/chrome/) (web development)
  - Never save passwords
  - Chrome Extensions
    - [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
- [Firefox](https://www.google.com/chrome/) (web development, web browsing)
  - Sync up with Mozilla account or manually import bookmarks
  - Set default browser
  - Never save passwords
  - Firefox Extensions
    - [Bitwarden](https://addons.mozilla.org/en-US/firefox/addon/bitwarden-password-manager/)
    - [Daily.dev](https://addons.mozilla.org/en-US/firefox/addon/daily/)
    - [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/)
    - [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
    - [React Developer Tools](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)
- [iTerm2](https://iterm2.com/) (terminal)
- [Visual Studio Code](https://code.visualstudio.com/) (web development IDE)
- [Bruno](https://www.usebruno.com/) (api development platform)
  - Preferences
    - Font
      - Code Editor Font: Hack Nerd Font Mono
    - Theme
      - Dark
- [GitHub Desktop](https://desktop.github.com/) (GUI for Git)
  - Preferences
    - Intergrations
      - External editor: Visual Studio Code
      - Shell: iTerm2
    - Appearance
      - Enable dark mode
    - Advanced
      - Disable: Usage (Help GitHub Desktop improve by submitting)
- [Sublime Text](https://www.sublimetext.com/) (lightweight editor)
  - Optional: Disable updates (my license is not valid for newer versions)
- [Rectangle](https://rectangleapp.com//) (window manager)
  - Use Rectangle settings, not Spectacle
  - Enable "Launch at Login"
- [Appcleaner](https://freemacsoft.net/appcleaner/) (app uninstaller)
- [Slack](https://slack.com/) (team messenger)
- [Discord](https://discord.com/) (community messenger)
- [VLC](https://www.videolan.org/vlc/) (video player)
  - Use as default for video files
- [Figma](https://www.figma.com/) (design)
- [KeyboardCleanTool](https://folivora.ai/keyboardcleantool) (blocks keyboard for cleaning)
- [BetterDisplay](https://github.com/waydabber/BetterDisplay) (display tool)
- [ImageOptim](https://imageoptim.com/mac) (performance)
- [Handbrake](https://handbrake.fr/) (performance)
- [The Unarchiver](https://theunarchiver.com/) (unarchiver)
- [Tunnelblick](https://www.tunnelblick.net/) (vpn)

## Terminal Applications

- [wget](https://www.gnu.org/software/wget/) (curl replacement)
- [git](https://git-scm.com/) (version control)
- [openssl](https://www.openssh.com/) (OpenSSH)
- [pnpm](https://pnpm.io/) (node package manager)
- [commitzen](https://commitizen-tools.github.io/commitizen/) (committing rules for projects)

## Optional Applications

- [Yubico Authenticator](https://www.yubico.com/products/yubico-authenticator/) (TOTP manager)
- [Logi Options](https://www.logitech.com/en-us/software/options.html) (drivers and settings for Logitech products)

# iTerm2

The look and feel we want to achieve from our terminal:

![terminal](https://i.postimg.cc/tgL2XrYL/iterm.png "terminal")

- Make iTerm2 Default Term
- Preferences ->
  - General -> Window
    - Unselect "Native full screen windows"
  - Appearance ->
    - Tabs
      - Unselect "Show tab bar in fullscreen"
    - Dimming
      - Unselect all dimming and
      - Set dimming amount: 1
    - General
      - Theme: minimal
  - Profiles -> Window
    - Transparency: 0
    - Style: Normal
    - Screen: Main Screen
    - Columns: 120
    - Rows: 30
  - Profiles -> Advanced
    - Semantic History -> Open with editor ... -> VS Code
  - Advanced
    - Tabs: in minimal tab outline 0.1

## iTerm2 Colors + Font

Download the snazzy theme

```
bash (curl -Ls https://raw.githubusercontent.com/sindresorhus/iterm2-snazzy/main/Snazzy.itermcolors > /tmp/Snazzy.itermcolors && open /tmp/Snazzy.itermcolors)
```

Now you have to manually configure the iTerm2 color theme:

```
iTerm2 Preferences: Profiles > Colors > Color Presets: Snazzy
```

As font we will be using Hack Nerd Font in iTerm2, VS Code, and Sublime Text. Install it via:

```
brew tap homebrew/cask-fonts
brew install --cask font-hack-nerd-font
```

Use the new font in

```
iTerm2: Preferences -> Profile -> Text -> Font: font-hack-nerd-font.
```

# Shell configuration

By default macOS ships with Zsh, in my opinion it's still missing some important features and for that reason I like to extend it with some plugins and custom settings.

My personal favorite is the relatively new Fish shell, it's blazing fast and very easy to use. I will also provide you with instructions on how to get started with this shell.

## Zsh

<details>

<summary>
Configure with Zsh
</summary>
<br/>

Install [Oh My Zsh](https://ohmyz.sh/) for an improved terminal experience:

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Update everything (e.g. plugins) in Oh My Zsh to recent version:

```
omz update
```

Important: If you change something in your Zsh configuration (_.zshrc_), force a reload:

```
source ~/.zshrc
```

## Starship Theme

Install [Starship](https://starship.rs/) as your new terminal theme:

```
brew install starship
```

Make it the default theme for Zsh by using the following command:

```
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

If the theme and font changes do not apply, reload your zsh configuration or close/open iTerm2.

### Config starship theme

To get started configuring starship, create the following file: `~/.config/starship.toml`.

```
mkdir -p ~/.config && touch ~/.config/starship.toml
```

All configuration for starship is done in this TOML file:

```
# Get editor completions based on the config schema
"$schema" = 'https://starship.rs/config-schema.json'

# Add longer timeout for fnm to install node
command_timeout = 9000
```

These are my settings but feel free to [add your own](https://starship.rs/config/)

## Oh My Zsh Plugins

Please follow the instructions and install these plugins by using Oh My Zsh:

- [zsh-completions](https://github.com/zsh-users/zsh-completions)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [fast-syntax-highlighting](https://github.com/zdharma/fast-syntax-highlighting)

## Zsh Configuration File (_.zshrc_):

Open vim to view the current configuration

```
vim ~/.zshrc
```

Copy and paste the new configuration but don't forget to replace the placeholders.

```
# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# enable when using Yubikey, otherwise you can remove these lines
# export GPG_TTY=$(tty)
# export KEYID="<your gpg key>"

# enable when using GPG for SSL, otherwise you can remove these lines
# export SSH_AUTH_SOCK=$(gpgconf --list-dirs agent-ssh-socket)
# gpgconf --launch gpg-agent

# Git variables
export GH_TOKEN="<your token>"
export GIT_AUTHOR_NAME="<your name>"
export GIT_AUTHOR_EMAIL="<your email>"
export GIT_COMMITTER_NAME="<your name>"
export GIT_COMMITTER_EMAIL="<your email>"

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(
  git
  zsh-completions
  zsh-autosuggestions
  zsh-syntax-highlighting
  F-Sy-H
)

# get machine's ip address
alias ip="ipconfig getifaddr en0"

# get global ip address
alias pubip="curl ifconfig.me"

# edit global zsh configuration
alias zshconfig="vim ~/.zshrc"

# reload zsh configuration
alias zshsource="source ~/.zshrc"

# update brew and cleanup
alias brewup="brew update; brew upgrade; brew cleanup; brew doctor"

# open file or folder in Sublime Text
alias sublime='open -a "Sublime Text"'

# open file or folder in VSCode
alias code='open -a "Visual Studio Code"'

# load zsh-completions
autoload -U compinit && compinit

# use oh my zsh
source $ZSH/oh-my-zsh.sh

# use fnm
eval "$(fnm env --use-on-cd)"

# use starship theme (needs to be at the end)
eval "$(starship init zsh)"
```

</details>

## Fish

<details>

<summary>
Configure with Fish
</summary>
<br/>

To get started download the shell by using Homebrew:

```
brew install fish
```

Now we will configure it to be our default shell:

```
# Add the shell to /etc/shells with
echo /opt/homebrew/bin/fish | sudo tee -a /etc/shells

# changing the default shell to fish
chsh -s /opt/homebrew/bin/fish
```

Congratulations, you've now successfully installed the Fish shell on your local machine let's dive into the configurations.

## Starship Theme

Install [Starship](https://starship.rs/) as your new terminal theme:

```
brew install starship
```

Make it the default theme for Fish by using the following command:

```
echo 'starship init fish | source' >> ~/.config/fish/config.fish
```

If the theme and font changes do not apply, reload your fish configuration or close/open iTerm2.

### Config starship theme

To get started configuring starship, create the following file: `~/.config/starship.toml`.

```
mkdir -p ~/.config && touch ~/.config/starship.toml
```

All configuration for starship is done in this TOML file:

```
# Get editor completions based on the config schema
"$schema" = 'https://starship.rs/config-schema.json'

# Add longer timeout for fnm to install node
command_timeout = 9000
```

These are my settings but feel free to [add your own](https://starship.rs/config/)

## Fish Variables

To add and preserve variables in the fish shell its very easy to do.
Let's add some variables that I use frequently, please remember to change the placeholders

```
# enable when using Yubikey
# set -Ux KEYID "<your gpg key>"

# Git variables
set -Ux GH_TOKEN <your token>
set -Ux GIT_AUTHOR_NAME <your name>
set -Ux GIT_AUTHOR_EMAIL <your email>
set -Ux GIT_COMMITTER_NAME <your name>
set -Ux GIT_COMMITTER_EMAIL <your email>
```

Universal variables will be stored in the file `~/.config/fish/fish_variables`.

To remove a variable you can use: `set --erase myvar` or a function `unset` that we will add later.

## Fish Configuration File (_.config.fish_):

Open vim to view the current configuration

```
vim ~/.config/fish/config.fish
```

Copy and paste the new configuration

```
if status is-interactive
    # Commands to run in interactive sessions can go here
end

# get machine's ip address
alias ip="ipconfig getifaddr en0"

# get global ip address
alias pubip="curl ifconfig.me"

# edit global fish configuration
alias fconfig="vim ~/.config/fish/config.fish"

# reload zsh configuration
alias fsource="source ~/.config/fish/config.fish"

# update brew and cleanup
alias brewup="brew update; brew upgrade; brew cleanup; brew doctor"

# open file or folder in Sublime Text
alias sublime='open -a "Sublime Text"'

# open file or folder in VSCode
alias code='open -a "Visual Studio Code"'

# add fish path for homebrew
fish_add_path /opt/homebrew/bin

# use starship theme (needs to be at the end)
starship init fish | source
```

## Fnm

Install the package with homebrew:

```
brew install fnm
```

Create `~/.config/fish/conf.d/fnm.fish` add this line to it:

```
fnm env --use-on-cd | source
```

## Gnupg as SSH agent (optional)

Create `~/.config/fish/conf.d/gnupg.fish` add these lines to it:

```
# Ensure that GPG Agent is used as the SSH agent
set -e SSH_AUTH_SOCK
set -U -x SSH_AUTH_SOCK (gpgconf --list-dirs agent-ssh-socket)

set -x GPG_TTY (tty)

gpgconf --launch gpg-agent
```

## Functions

Just like with Zsh, you can use functions to extend the basic terminal commands.

Here are some of my favorite functions that I use daily, you can copy and paste them into your Fish shell to add them.

### unset

_alias for 'set --erease myvar'_

```
function unset
  set --erase $argv
end

funcsave unset
```

### envsource

_loads .env files into your terminal_

```
function envsource
  for line in (cat $argv | grep -v '^#' | grep -v '^\s*$')
    set item (string split -m 1 '=' $line)
    set -gx $item[1] $item[2]
    echo "Exported key $item[1]"
  end
end

funcsave envsource
```

### gpg-decrypt

_decrypt a gpg file with my private key_

```
function gpg-decrypt
    set -l output $argv[1]
    gpg --decrypt --armor $output
end

funcsave gpg-decrypt
```

### gpg-encrypt

_encrypt a gpg file with my public key_

```
function gpg-encrypt
    set -l keyid $argv[1]
    set -l output $argv[2]
    gpg --encrypt --armor --recipient $keyid -o $output -
end

funcsave gpg-encrypt
```

</details>

## Reset shell

If you ever want to reset your shell to the default settings, you can do so by running the following command:

```
chsh -s /bin/zsh
```

If you need to determine the path to your shell, you can use the following command:

```
which zsh fish
```

# VS Code

The look and feel we want to achieve from our IDE:

![ide](https://i.postimg.cc/qMzhLpmx/vscode.png "ide")

## Extensions

- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
- [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)
- [Convert px to rem](https://marketplace.visualstudio.com/items?itemName=gwanduke.convert-px-to-rem)
- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Git Blame](https://marketplace.visualstudio.com/items?itemName=waderyan.gitblame)
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
- [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
- [GraphQL](https://marketplace.visualstudio.com/items?itemName=mquandalle.graphql)
- [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
- [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
- [HTMLHint](https://marketplace.visualstudio.com/items?itemName=HTMLHint.vscode-htmlhint)
- [Import Cost](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
- [MDX](https://marketplace.visualstudio.com/items?itemName=unifiedjs.vscode-mdx)
- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)
- [Paste JSON as Code](https://marketplace.visualstudio.com/items?itemName=quicktype.quicktype)
- [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
- [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [VSCode React Refactor](https://marketplace.visualstudio.com/items?itemName=planbcoding.vscode-react-refactor)

## JSON Settings

```
{
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "workbench.sideBar.location": "left",
  "workbench.startupEditor": "none",
  "workbench.statusBar.visible": true,
  "workbench.editor.enablePreview": true,
  "workbench.activityBar.visible": true,
  "workbench.editor.restoreViewState": true,

  "editor.fontFamily": "Hack Nerd Font Mono",
  "editor.lineHeight": 1.6,
  "editor.tabSize": 2,
  "editor.insertSpaces": false,
  "editor.detectIndentation": false,
  "editor.renderWhitespace": "none",
  "editor.scrollBeyondLastLine": true,
  "editor.minimap.enabled": false,
  "editor.lineNumbers": "on",
  "editor.find.seedSearchStringFromSelection": "never",
  "editor.renderLineHighlight": "all",
  "editor.inlineSuggest.enabled": true,
  "editor.quickSuggestions": {
    "strings": true
  },

  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.formatOnType": false,
  "editor.formatOnPaste": false,

  "editor.codeActionsOnSave": {
    "source.fixAll": true,
    "source.sortImports": true
  },

  "workbench.colorCustomizations": {
    "editor.lineHighlightBackground": "#223851"
  },

  "files.trimFinalNewlines": true,
  "files.trimTrailingWhitespace": true,
  "files.associations": {
    ".env*": "makefile"
  },

  "tailwindCSS.experimental.classRegex": [
    ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"]
  ],

  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ],
  "javascript.validate.enable": false,
  "javascript.updateImportsOnFileMove.enabled": "never",
  "typescript.updateImportsOnFileMove.enabled": "never",

  "explorer.confirmDelete": false,
  "explorer.compactFolders": false,
  "explorer.confirmDragAndDrop": false,
  "js/ts.implicitProjectConfig.checkJs": true,

  "extensions.ignoreRecommendations": true,
  "security.workspace.trust.untrustedFiles": "open",
  "git.openRepositoryInParentFolders": "never",

  "typescript.preferences.quoteStyle": "double",
  "javascript.preferences.quoteStyle": "double",

  "github.copilot.enable": {
    "*": true,
    "plaintext": true,
    "markdown": true,
    "scminput": false
  }
}
```

# Sublime

Not used for web development anymore. Primarily used for quick edits

![sublime](https://i.postimg.cc/q7FT4b8K/Screenshot-2023-03-02-at-19-22-06.png"sublime")

## General

- Use license

## Extensions

- [Agila Theme](https://packagecontrol.io/packages/Agila%20Theme) (Theme)
- [Predawn](https://packagecontrol.io/packages/Predawn) (Theme)
- [SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements) (Folder/File Features)
- [TrailingSpaces](https://packagecontrol.io/packages/TrailingSpaces) (Deletes Trailing Spaces)

## JSON Settings

```
{
  "caret_style": "solid",
  "folder_exclude_patterns":
  [
    ".git",
    "node_modules"
  ],
  "font_size": 13,
  "font_face": "Hack Nerd Font",
  "gutter": true,
  "highlight_line": true,
  "highlight_modified_tabs": true,
  "ignored_packages":
  [
    "TypeScript",
    "Vintage"
  ],
  "line_padding_bottom": 1,
  "line_padding_top": 1,
  "predawn_findreplace_small": true,
  "predawn_sidebar_arrows": true,
  "predawn_sidebar_narrow": true,
  "predawn_sidebar_xsmall": true,
  "predawn_tabs_small": true,
  "rulers":
  [
    120
  ],
  "scroll_past_end": true,
  "show_line_numbers": true,
  "spell_check": false,
  "tab_size": 2,
  "theme": "Agila Origin.sublime-theme",
  "theme_agila_compact_sidebar": true,
  "theme_agila_compact_tab": true,
  "theme_agila_horizontal_scrollbar_thinnest": true,
  "theme_agila_sidebar_font_xsmall": true,
  "theme_agila_sidebar_mini": true,
  "theme_agila_vertical_scrollbar_thinnest": true,
  "translate_tabs_to_spaces": false,
  "trim_trailing_white_space_on_save": true,
  "color_scheme": "Packages/Agila Theme/Agila Origin Oceanic Next.tmTheme",
  "update_check": false,
}
```

# Git

From terminal, set global name and email:

```
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global core.ignorecase false
```

Improved git log

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

Set the default branch to main instead of master

```
git config --global init.defaultBranch main
```

Print global git configuration:

```
git config --list
```

# SSH

There are several strategies for SSH keys: one SSH key to rule them all or one SSH key per service. I use the latter one and will here run you through it by connecting [to GitHub via SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

First, create a new SSH key in the _~/.ssh_ folder:

```
# in case the folder is not there yet
mkdir ~/.ssh

cd ~/.ssh

ssh-keygen -t ed25519 -C "github"
# follow instructions
# use file name: github
# use passphrase and store it somewhere secure
```

Confirm whether passphrase was used properly by accessing private key:

```
ssh-keygen -y -f github
# confirm with passphrase
```

Create the SSH configuration file if it doesn't exist yet:

```
touch ~/.ssh/config
# in case the file is not there yet
```

In your _~/.ssh/config_ file, add the new SSH key, so that it can get picked up for every terminal session automatically:

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github
```

Add SSH key to MacOS' keychain:

```
ssh-add --apple-use-keychain ~/.ssh/github
```

Add the public key manually to your GitHub settings via the website:

```
cat ~/.ssh/github.pub | pbcopy
# copy public key to clipboard and add it manually to https://github.com/settings/keys
```

That's it. You have created an SSH key locally, secured it via a passphrase, made it automatically available for every terminal session, and applied it to GitHub. In the case of GitHub, you are now able to interact with GitHub via SSH.

# OpenPGP

With OpenPGP, you can sign your commits on GitHub. This is of course not mandatory but a good practice especially when you are using multiple computers.
There are multiple ways to setup OpenPGP on your computer, my recommendation is to use a Yubikey and follow [this guide](https://github.com/drduh/YubiKey-Guide) to add your keys.

Let's start by installing all of the dependencies:

```
brew install \
  ykman \
  gnupg \
  pinentry-mac
```

Now assuming you already have the keys set up, you can import the (public) key(s) like this:

```
# import OpenPGP key
gpg --import ./public.asc
```

Now check if you have imported all of your keys by using:

```
# View imported keys on your machine
gpg -k
```

Copy your `public key ID` to the clipboard, we will need this later to configure Git.
Let's first add the pin-prompts to your terminal + macOS

```
# add pin-prompt to cli you might want to add this to your shell configuration
export GPG_TTY=$(tty)

# add pinnetry-mac to your gpg config
echo "pinentry-program /opt/homebrew/bin/pinentry-mac" > ~/.gnupg/gpg-agent.conf

# restart the agent
killall gpg-agent
```

Almost done, now we just have to configure Git by letting it automatically sign the commits and tags and use our `public key ID`.

```
# tell git config to sign all commits and tags by default (alternative is -s flag)
git config --global commit.gpgsign true
git config --global tag.gpgsign true

# configure the signature key
git config --global user.signingkey <PUBLIC KEY ID>
```

## SSH with OpenPGP

A very cool feature of OpenPGP is that you use it for SSH authentication. In combination with a YubiKey, you will always carry a physical key that allows you to access your Git repositories. Here are two methods of enabling SSH authentication:

- [SSH with FIDO2](https://gist.github.com/Kranzes/be4fffba5da3799ee93134dc68a4c67b)
- [Enable SSH authentication with gpg-agent](https://github.com/drduh/YubiKey-Guide#ssh)

## More information about OpenPGP

That's it OpenPGP is now configured on your machine, if you like to learn more about how to create these OpenPGP keys I can recommend reading one of these guides:

- [About commit signature verification with Github](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- [Yubikey guide (OpenPGP)](https://github.com/drduh/YubiKey-Guide)
- [Yubikey guide alternative (OpenPGP)](https://whynothugo.nl/journal/2022/07/11/using-a-yubikey-for-gpg/)

## Troubleshooting

One final note, if you're using a Yubikey for signing commits on your brand new machine you will need to run this command to reset the default key location:

```
gpg-connect-agent "scd serialno" "learn --force" /bye
```

# Fast Node Manager (fnm) for Node.js

The [Fast Node Manager (fnm)](https://github.com/Schniz/fnm) is used to install and manage multiple Node versions. The idea and CLI is identical to `nvm` it's just faster basically.

Let's start by installing fnm on your local machine:

```
brew install fnm
```

Now configure your terminal to use fnm by following [these instructions](https://github.com/Schniz/fnm#shell-setup)

## Configuration

Now let's install the lts version of Node.js on the machine

```
fnm install --lts
```

Afterward, check whether the installation was successful and whether the [node package manager (npm)](https://www.npmjs.com/) got installed along the way:

```
node -v && npm -v
```

And set [defaults for npm](https://docs.npmjs.com/creating-a-package-json-file#setting-config-options-for-the-init-command):

```
npm set init-author-email "example-user@example.com"
npm set init-author-name "example_user"
npm set init-license "MIT"

npm config set save-exact true
```

That's it. If you want to list all your Node.js installations, type the following:

```
fnm list
```

If you want to install a newer Node.js version, then type:

```
fnm install <version> && fnm use <version>
```

Optionally install [pnpm](https://pnpm.io/) if you use it as alternative to npm:

```
corepack enable pnpm
```

Configure pnpm with some recommended settings:

```
pnpm config set save-prefix ""
```

If you want to list all globally installed packages, run this command:

```
npm list -g --depth=0
```

That's it. You have a running version of Node.js and its package manager.

# Git project folder

To keep your mac clean, I suggest adding a new (root) folder for all of your git projects

```
mkdir ~/Git
```

Drag this folder to your favorites in the Finder and configure your terminal to open this location by default

---

I hope my setup helps other developers to get their Mac up and running. If you have any additional ideas or want to share your setup, let me know!

This article is inspired by [Robin Wieruch](https://www.robinwieruch.de/mac-setup-web-development/).
