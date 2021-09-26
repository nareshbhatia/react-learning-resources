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

Tip: Always run Chocolatey from PowerShell running as an administrator.

### Install 7-Zip

[7-Zip](https://www.7-zip.org/) is a good open source file archiver.

```bash
choco install 7zip -y
```

### Install Cmder

[Cmder](https://cmder.net/) is a great console emulator for Windows. We will use
the git-for-windows version which includes all Unix commands ready in PATH so
that you can use commands like `git`, `cat` and `ls` instantly on your machine.

```bash
choco install cmdr -y
```

Cmder is installed under C:\tools\cmder. Open this folder in File Explorer. You
will find the Cmder executable here called Cmder.exe. Pin this executable to the
taskbar for ease. Now start Cmder from the taskbar.

By default, Cmder starts at C:\tools\cmder. I prefer having it start at my home
directory (e.g. D:\users\<username>). Follow the steps below to do this.

- Click on the hamburger menu (bottom right) and select Settings.
- In the navigation bar, select Startup > Tasks.
- Under Predefined Tasks, click on {cmd::Cmder}.
- Click the button that says "Startup dir..."
- Select your home directory.
- Click on "Save Settings".

### Install Node

```bash
choco install nodejs-lts -y
```

Open Cmder and verify that node is installed correctly:

```bash
node -v    # prints v14.17.6 as of this writing
```

### Install Yarn

```bash
choco install yarn -y
```

Open Cmder and verify that yarn is installed correctly:

```bash
yarn -v    # prints v1.22.5 as of this writing
```

### Try building a React app

Clone the
[Accelerated News](https://github.com/PublicisSapient/accelerated-news) repo
wherever you keep projects and verify that you can build and run the app. I
recommend keeping all your projects under your home directory, e.g.
`D:\user\<username>\projects`.

Open Cmder and execute the following commands:

```bash
cd projects
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
