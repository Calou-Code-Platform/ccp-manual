# Calou Code Platform Manual
> This manual just applicable `calou-code-platform:remosh` docker images.<br>
> if you want try this manual on another platform at your own peril.

## Prepare Tools
| Platform | Tool Name |
|---|---|
| Windows / Linux / MacOS | [Visual Studio Code](https://code.visualstudio.com/) |
| Windows | CMD / PowerShell |
| MacOS / Linux | Terminal |
| Android | [termux](https://termux.dev/en/) |
| iOS / iPadOS | [Termius](https://apps.apple.com/tw/app/termius-modern-ssh-client/id549039908) |

## Connection
### Visual Studio Code:
1. Click the left-down corner pc icon button.
2. Select "Install Remote-SSH".
3. Select "Connect to Host...".
4. Select "Add New SSH Host..."
5. Enter `ssh <yourname>@ssh.calou.cc -p <port>`.
6. Select "Connect to Host..." Again.
7. Select Your server.
8. Yes.
9. Enter your password.

### CMD / Powershell / Terminal / termux
1. Enter `ssh <yourname>@ssh.calou.cc -p <port>`.
2. Enter "Yes".
3. Enter your password.

### Termius
1. Just create a SSH connection.

## Initailization
1. On your terminal, enter this command `~/get-builder.sh`.
2. Next use this command `./builder.sh`.
3. After install you want package, and run this command `source ~/.bashrc`

## About tmux
`SSH` not `code-server`, so we need this extension make application can running on background.

| directions | commands |
|---|---|
| Create a new session, name is `window1` | `tmux new -t window1` |
| Enter session, name is `window1` | `tmux a -t window1` |
| Kill a session, name is `window1` | `tmux kill-session -t window1` |
| Show all session | `tmux ls` |
| Left current session | [Ctrl + B] > [D] |

## Code-Server
1. When you initailzation, you need install `code-server`
2. Open new tmux session.
3. Run `code-server` command on your tmux session.
4. Use `dev-<yourname>.calou.cc` to connection the web page.

## nvm
About [nvm](https://github.com/nvm-sh/nvm)
```shell
nvm install 25
nvm use 25
```

## pyenv
About [pyenv](https://github.com/pyenv/pyenv)
```shell
pyenv install 3.10
pyenv global 3.10
```

## Port
| Your container port | Website url |
|---|---|
| 3000 | `web-<yourname>.calou.cc` |
| 3100 | `dev-<yourname>.calou.cc` |

## Restart your contai
```shell
sudo kill 1
```
