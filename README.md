# Mac Setup for Web Development [2023]

In this article I want to share with you my macOS setup for web development.

# MacBook Pro Specifications

- 16-inch
- Apple MacBook Pro, M2 Pro 12‑Core CPU, 19‑Core GPU and 16‑Core Neural Engine
- 16 GB RAM
- 512 GB SSD
- QWERTY = English (USA)
- macOS Ventura

# System Settings

- Profile
  - Set avatar
  - iCloud
    - Disable
- Notifications
  - Off
- General
  - Software Update: update all
  - AirDrop: No One
  - Sharing
    - Make sure everything is off
    - Change computer name (local hostname)
  - Time Machine: Configure when required
- Appearance
  - Auto
- Control Centre
  - Battery: "Show Percentage"
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
  - Magnification: Off
  - Automatic Hide
  - Show recent applications in Dock: Off
  - Show indicators for open applications: On
  - Hot Corners: disable all
- Display
  - True Tone: On
- Wallpaper
  - Dynamic
- Lock Screen
  - Start Screen Saver when inactive: Never
  - Turn display off (battery): 5 minutes
  - Turn display off (power): 10 minutes
  - Require password: After 1 minute
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
    - Disable "Correct spelling automatically"
    - Disable "Capitalise word automatically"
    - Disable "Add full stop with double-space"
    - Disable "Use smart quotes and dashes"
    - use `"` for double quotes
    - use `'` for single quotes
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
    - Activate all Favorites
    - Move Library to Favorites
  - Advanced
    - Show all filename extensions
    - Remove Items from Bin after 30 Days
- Widget
  - Remove widgets
- Storage
  - Remove Garage Band & Sound Library
  - Remove iMovie

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

# restart finder
killall Finder;
```

# Alfred

Used as replacement for Apple Spotlight

- Use license
- Set shortcut to: option + space
- Launch Alfred at login
- Appearance
  - Alfred macOS Dark
  - Hide hat on Alfred window

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
  insomnia \
  github \
  https://raw.githubusercontent.com/Homebrew/homebrew-cask/9c7cef6f712515f8b87983685f0e82047362e08c/Casks/sublime-text.rb \
  spotify \
  rectangle \
  maccy \
  slack \
  discord \
  vlc \
  figma \
  imageoptim \
  handbrake \
  the-unarchiver \
  tunnelblick
```

Install terminal applications (read more about these in Terminal Applications):

```
brew install \
  wget \
  exa \
  git \
  nvm \
  pnpm \
  commitizen
```

# GUI Applications

- [Bitwarden](https://bitwarden.com/) (password manager)
  - Preferences
    - Vault timeout: 5 minutes
    - enable Touch ID
    - start automatically on login
    - Theme: Dark
- [Alfred](https://www.alfredapp.com/) (spotlight alternative)
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
- [Insomnia](https://insomnia.rest/) (api development platform)
  - Preferences
    - General
      - Indent with tabs
      - Text editor font: Hack Nerd Font Mono
      - Notifications: do not tell me about premium features
      - Send usage data: off
    - Themes
      - One Dark
- [GitHub Desktop](https://desktop.github.com/) (GUI for Git)
  - Preferences
    - Intergrations
      - External editor: Visual Studio Code
      - Shell: iTerm2
    - Appearance
      - enable dark mode
    - Advanced
      - Disable: Usage (Help GitHub Desktop improve by submitting)
- [Sublime Text](https://www.sublimetext.com/) (lightweight editor)
- [Rectangle](https://rectangleapp.com//) (window manager)
  - use Rectangle settings, not Spectacle
  - enable "Launch at Login"
- [Maccy](https://maccy.app/) (clipboard manager)
  - enable "Launch at Login"
- [Slack](https://slack.com/) (team messenger)
- [Discord](https://discord.com/) (community messenger)
- [VLC](https://www.videolan.org/vlc/) (video player)
  - use as default for video files
- [Figma](https://www.figma.com/) (design)
- [ImageOptim](https://imageoptim.com/mac) (performance)
- [Handbrake](https://handbrake.fr/) (performance)
- [The Unarchiver](https://theunarchiver.com/) (unarchiver)
- [Tunnelblick](https://www.tunnelblick.net/) (vpn)

# Terminal Applications

- [wget](https://www.gnu.org/software/wget/) (curl replacement)
- [exa](https://the.exa.website/install/macos) (ls replacement)
  - `exa`
  - `exa -a` (include hidden files)
  - `exa -l` (include additional information)
- [git](https://git-scm.com/) (version control)
- [nvm](https://github.com/nvm-sh/nvm) (node version manager)
- [pnpm](https://pnpm.io/) (node package manager)
- [commitzen](https://commitizen-tools.github.io/commitizen/) (committing rules for projects)

# iTerm2

The look and feel we want to achieve from our terminal:

![terminal](https://i.postimg.cc/tgL2XrYL/iterm.png 'terminal')

- Make iTerm2 Default Term
- Preferences ->
  - General -> Window
    - unselect "Native full screen windows"
  - Appearance ->
    - Tabs
      - unselect "Show tab bar in fullscreen"
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
  - [Open new split pane with current directory](https://apple.stackexchange.com/a/337386)

# Theme

Install snazzy theme

```
(curl -Ls https://raw.githubusercontent.com/sindresorhus/iterm2-snazzy/main/Snazzy.itermcolors > /tmp/Snazzy.itermcolors && open /tmp/Snazzy.itermcolors)
```

Configure iTerm2 color theme:

```
iTerm2 Preferences: Profiles > Colors > Color Presets: Snazzy
```

# Oh My Zsh

When you open iTerm2, you see that MacOS already comes with zsh as default shell. Install [Oh My Zsh](https://ohmyz.sh/) for an improved (plugins, themes, ...) terminal (here: iTerm2) experience:

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

## Oh My Zsh Theme + Fonts:

Install [Starship](https://starship.rs/) as your new terminal theme. We will use Homebrew, but you can use an alternative from the website too:

```
brew install starship
```

Make it the default theme for Oh My ZSH from the terminal:

```
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
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

If the theme and font changes do not apply, reload your zsh configuration (_.zshrc_) or close/open iTerm2.

## Oh My Zsh Plugins

- [zsh-completions](https://github.com/zsh-users/zsh-completions)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [fast-syntax-highlighting](https://github.com/zdharma/fast-syntax-highlighting)

## ZSH Configuration File (_.zshrc_):

```
# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

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

# reload zsh configuration
alias ohmyzsh="cd ~/.oh-my-zsh"

# git aliases
alias gitc="cz commit"

# open file or folder in Sublime Text
alias sublime='open -a "Sublime Text"'

# open file or folder in VSCode
alias code='open -a "Visual Studio Code"'

# load zsh-completions
autoload -U compinit && compinit

# use oh my zsh
source $ZSH/oh-my-zsh.sh

# use nvm
source /usr/local/opt/nvm/nvm.sh

# use starship theme (needs to be at the end)
eval "$(starship init zsh)"
```

# VS Code

The look and feel we want to achieve from our IDE:

![ide](https://i.postimg.cc/qMzhLpmx/vscode.png 'ide')

## Extensions

- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Color Highlight](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)
- [Color Picker](https://marketplace.visualstudio.com/items?itemName=anseki.vscode-color)
- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Formatting Toggle](https://marketplace.visualstudio.com/items?itemName=tombonnike.vscode-status-bar-format-toggle)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [GraphQL](https://marketplace.visualstudio.com/items?itemName=mquandalle.graphql)
- [Highlight Matching Tag](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
- [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)
- [HTMLHint](https://marketplace.visualstudio.com/items?itemName=HTMLHint.vscode-htmlhint)
- [Import Cost](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)
- [Paste JSON as Code](https://marketplace.visualstudio.com/items?itemName=quicktype.quicktype)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Tabnine](https://marketplace.visualstudio.com/items?itemName=TabNine.tabnine-vscode)
- [VSCode React Refactor](https://marketplace.visualstudio.com/items?itemName=planbcoding.vscode-react-refactor)
- [vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=styled-components.vscode-styled-components)

## JSON Settings

```
{
  "breadcrumbs.enabled": false,
  "files.trimTrailingWhitespace": true,
  "explorer.confirmDelete": false,
  "explorer.compactFolders": false,
  "workbench.colorTheme": "One Dark Pro",
  "workbench.sideBar.location": "left",
  "workbench.startupEditor": "none",
  "workbench.statusBar.visible": true,
  "workbench.editor.enablePreview": true,
  "workbench.activityBar.visible": true,
  "workbench.editor.restoreViewState": true,
  "terminal.integrated.fontFamily": "Hack Nerd Font Mono",
  "editor.fontFamily": "Hack Nerd Font Mono",
  "editor.fontSize": 13,
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
  "workbench.colorCustomizations": {
    "editor.lineHighlightBackground": "#223851",
  },

  "files.associations": {
    ".env*": "makefile"
  },
  "prettier.singleQuote": true,
  "prettier.printWidth": 70,
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.suggest.insertMode": "replace"
  },
  "editor.codeActionsOnSave": {
    "source.fixAll": true,
    "source.sortImports": true
  },
  "eslint.validate": ["javascript", "javascriptreact", "typescript", "typescriptreact"],
  "javascript.validate.enable": false,
  "javascript.updateImportsOnFileMove.enabled": "never",
  "typescript.updateImportsOnFileMove.enabled": "never",
  "explorer.confirmDragAndDrop": false,
  "js/ts.implicitProjectConfig.checkJs": true,
  "editor.formatOnPaste": true,
  "editor.formatOnType": true,
  "extensions.ignoreRecommendations": true,
  "tabnine.experimentalAutoImports": false,
  "security.workspace.trust.untrustedFiles": "open",
  "workbench.iconTheme": "material-icon-theme"
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
}
```

# Git

From terminal, set global name and email:

```
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
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

There are two common strategies for SSH keys: one SSH key to rule them all or one SSH key per service. I use the latter one and will here run yout through it by connecting [to GitHub via SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

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

# NVM for Node.js & NPM

The [Node Version Manager (NVM)](https://github.com/nvm-sh/nvm) is used to install and manage multiple Node versions. Start by installing the latest LTS version on the command line:

```
nvm install --lts
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
```

That's it. If you want to list all your Node.js installations, type the following:

```
nvm list
```

If you want to install a newer Node.js version, then type:

```
nvm install <version> && nvm use <version>
```

Optionally install [yarn](https://yarnpkg.com/) if you use it as alternative to npm:

```
npm install -g yarn
yarn -v
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
