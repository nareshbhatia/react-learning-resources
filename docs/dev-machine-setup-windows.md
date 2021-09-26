# Development Machine Setup for Windows

### Install Chocolatey

[Chocolatey](https://chocolatey.org/) is a universal package manager and
installer for Windows software. We will use it to install the tools and
utilities we need for developing React applications.

Follow the steps listed below to install Chocolatey (these are based on the
[installation procedure](https://chocolatey.org/install) described on the
Chocolatey site):

- Open PowerShell as an administrator (Click **Start**, type **PowerShell**,
  right-click **Windows PowerShell**, and then click **Run as administrator**.)

- Ensure that the execution policy is not restricted. Run `Get-ExecutionPolicy`.
  If it returns `Restricted`, then run the following command:

```bash
Set-ExecutionPolicy Bypass -Scope Process
```

- Now run the following command. (Get this command from
  [Chocolatey’s official installation page](https://chocolatey.org/install#individual)
  in case there are any changes.)

```bash
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

- Wait for a few seconds for the command to complete.

- Shut down and restart PowerShell as an administrator for the installation to
  take effect.

- Type `choco -?` to make sure Chocolatey runs.

- See [Getting Started](https://docs.chocolatey.org/en-us/getting-started) for
  usage instructions and
  [Commands](https://docs.chocolatey.org/en-us/choco/commands/) for a listing of
  CLI commands.

### Install 7-Zip

[7-Zip](https://www.7-zip.org/) is a good open source file archiver.

```bash
choco install 7zip -y
```

### Install Cmder

[Cmder](https://cmder.net/) is a great console emulator for Windows. We will use
the git-for-windows version which includes all Unix commands ready in PATH so
that you can use commands like `git`, `cat` and `ls` instantly on your machine.

### Install Node

### Install Yarn

### Try building a React app

Clone the following repo wherever you keep projects and verify that you can
build and run a React app. I recommend keeping all your projects under your home
directory at `\user\<username>\projects`. (%HOMEDRIVE% %HOMEPATH%)

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
