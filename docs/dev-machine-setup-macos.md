# Development Machine Setup for MacOS

### Install iTerm2

iTerm2 is a replacement for the MacOS Terminal application and comes with an
impressive set of features. Download and install iTerm2 from
[here](https://iterm2.com/).

### Install Homebrew & Required Packages

See latest install docs [here](https://brew.sh/).

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install git wget
brew install tree # optional package for directory listing
```

### Install Z Shell

Starting MacOS 10.15 (Catalina), the default shell is zsh. If your default shell
is not zsh, I highly recommend changing it to zsh.

Execute the following command in your terminal window to find out your default
shell:

```bash
echo $SHELL
```

If you see something other than `/bin/zsh`, then zsh is not your default shell.
Change it using the following command:

```bash
chsh -s /bin/zsh
```

Now close the terminal and reopen it. Type `echo $SHELL` to make sure that zsh
is the default.

### Install Oh My Zsh

[Oh My Zsh](https://ohmyz.sh/) is a delightful framework for managing your Zsh
configuration. It comes bundled with thousands of helpful functions, helpers,
plugins and themes. Enter the following command in your shell to install Oh My
Zsh:

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

The installation script creates a backup of your .zshrc file, and then replaces
it with its own version. If you had any important configuration in your original
.zshrc, copy it over to your new .zshrc.

### Install Node Version Manager & Node

[Node Version Manager](https://github.com/nvm-sh/nvm) (nvm) is a bash script to
manage multiple node.js versions. It is better than using the Node.js installer
or Homebrew (see
[this article](https://pawelgrzybek.com/install-nodejs-installer-vs-homebrew-vs-nvm/)).

> Note: Go to the NVM site for the latest version of the install command.

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Now install the latest LTS version of Node.js

```bash
nvm install --lts
source "$HOME/.zshrc"
node -v    # prints v16.17.1 as of this writing
```

If you get the error `nvm: command not found`, then follow the instructions
under
[Troubleshooting on macOS](https://github.com/nvm-sh/nvm#troubleshooting-on-macos).

Now install [Yarn](https://classic.yarnpkg.com/en/).

```bash
npm install --global yarn
yarn -v    # should print a version number like v1.22.19
```

### Verify ~/.zshrc

At this point, the end of your .zshrc file should look something like this. Make
sure that each section is in the correct order.

```bash
# Node Version Manager (NVM)
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# Yarn
export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```

#### Optional

Add the following command shortcuts at the end of .zshrc

```bash
# ----- Command Shortcuts -----
# preferred 'ls' implementation
alias ll='ls -FGlAhp'

# recursive directory listing
alias lr='ls -R | grep ":$" | sed -e '\''s/:$//'\'' -e '\''s/[^-][^\/]*\//--/g'\'' -e '\''s/^/   /'\'' -e '\''s/-/|/'\'' | less'

# better directory listing
alias ltree='tree --dirsfirst -F -a'

# preferred 'ps' implementation
alias pc='ps -e -o user,pid,comm'
```

### Try building a React app

Clone the
[Accelerated News](https://github.com/PublicisSapient/accelerated-news) repo
wherever you keep projects and verify that you can build and run the app. I
recommend keeping all your projects under ~/projects.

```bash
cd ~/projects
git clone https://github.com/PublicisSapient/accelerated-news.git
cd accelerated-news
yarn
yarn start
```

Congratulations! Your machine is now certified to build React apps!

## Install an IDE

You may now install an IDE like
[Visual Studio Code](https://code.visualstudio.com/) (free) or
[WebStorm](https://www.jetbrains.com/webstorm/) (paid).

Here are some useful, Visual Studio Code extensions:

- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
- [Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Rewrap](https://marketplace.visualstudio.com/items?itemName=stkb.rewrap)
- [Version Lens](https://marketplace.visualstudio.com/items?itemName=pflannery.vscode-versionlens)
