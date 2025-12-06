```
╋┓┏┏┓
┗┗┻┗┫
    ┛
```

A simple deployment helper for apps running under [systemd](https://systemd.io/). It builds timestamped releases, switches them via a symlink for zero(-ish) downtime releases / rollbacks.

# Why?

I wanted to deploy a small service to a VPS, and I don't like using docker for everything. I just wanted to build the service binary on the VPS, and run it reliably. That's why I made this tool.

# Install

```bash
curl -fsSL https://raw.githubusercontent.com/loreanvictor/tug/main/script.sh -o tug
chmod +x tug
sudo mv tug /usr/local/bin/
```

# Usage

Go to your project directory and run:

```bash
tug init
```

You'll be asked for:
- The name of the app,
- The build command to use,
- Path to built binary

> If you have a rust project, the defaults usually work just fine.

These configs will then be stored in `.tug` file in the project directory. The rest of the commands
MUST be run from a directory with a `.tug` file in it.

👉 build a new release:

```bash
tug build
```

👉 deploy the latest built release:

```bash
tug deploy
```

👉 rollback to the previous release:

```bash
tug rollback
```

> Works nicer if you have `fzf` installed:
> ```bash
> sudo apt install fzf
> ```

👉 list all available commands:

```bash
tug help
```

<br/><br/>
