# Calou Code Platform 教學
> 這個教學僅適用於 `CCP` 服務，若您強行使用在個人的容器上，請帶點腦袋並轉換成自己需要的。<br>
> 若您搞壞了您的容器，於我無關，您責備的我的話，我將會嘲笑您。

## 在這篇教學中你將會知道...
- 怎麼連線我的 CCP 服務。
- `tmux` 究竟是什麼，怎麼用？
- 想使用 iPad 寫程式，怎麼搞？
- 究竟哪些 Port 可以被使用？
- 讓容器重新啟動的辦法。

## 可用工具
- [Visual Studio Code](https://code.visualstudio.com/download)
- [termux](https://f-droid.org/zh_Hant/packages/com.termux/)
- [termius](https://termius.com/)
- Terminal
- CMD
- Powershell

我一率建議 iPhone iPad 使用 termius 連線，因為他是唯一的辦法。<br>
如果你拿的是 Android 則是使用 termux 連線。<br>
電腦的話，就建議 Visual Studio Code 連就好，不要太複雜。

## 如何連線
### Visual Studio Code
1. 打開 Visual Studio Code
2. 最左下角有一個亮色按鈕，按下後選擇帶有 SSH 字眼的選項
3. 等待安裝完後，再點一次左下角亮色按鈕，選擇 `Connect to Host...`
4. 然後先新增一個 SSH (選擇帶有加號的)
5. 輸入 `ssh <name>@ssh.calou.cc -p <port>`
6. 此時選擇你要添加的檔案（隨便你，通常都選第一個）
7. 在左下角連線一次時，會發現多出剛剛新增的設定檔
8. 連線後，依序輸入 `linux` | `yes` | `<password>`
9. 選擇 `/workspace` 作為目標

### Terminal & CMD & Powershell & Termux
1. 開啟 Terminal & CMD & Powershell
2. 輸入 `ssh <name>@ssh.calou.cc -p <port>`
3. 依序輸入 `yes` | `<password>`
4. `cd` 進入 `workspace`

### Termius
1. 創建一個 SSH 即可。
2. 僅會用到 Address Port username password。

## 初始化容器
1. 你進入了容器後，使用 `~/get-builder.sh`
2. 安裝你需要的東西
3. 使用 `source ~/.bashrc` 更新你的指令（不會有任何回應是正常的）

## iPad 寫程式？
請在 [#初始化容器](https://github.com/Calou-Code-Platform/ccp-manual/blob/main/README_zhtw.md#初始化容器) 安裝 visual studio code tunnel 後，在一個新的 tmux 中輸入 `code-tunnel tunnel` ，登入後前往 [vscode.dev](https://vscode.dev) ，選擇連線到通道。

## 關於 nodejs 或者 python
請參閱 [nvm(Node version manager)](https://github.com/nvm-sh/nvm) & [pyenv(Simple Python Version Management)](https://github.com/pyenv/pyenv)

## 關於 tmux
| 說明 | 指令 |
|---|---|
| 創建一個視窗，名稱是 `window1` | `tmux new -t window1` |
| 進入一個視窗，名稱是 `window1` | `tmux a -t window1` |
| 關閉一個視窗，名稱是 `window1` | `tmux kill-session -t window1` |
| 顯示已經開啟的視窗 | `tmux ls` |
| 離開當前的視窗 | [Ctrl + B] > [D] |

如果要讓 tmux 支援滑鼠，請在重新啟動後時輸入 `tmux set -g mouse on`

## 有哪些 Port 可以被使用？
請不要使用 22 作為端口！<br>
我們現在全面採用 `cloudflared` 作為主要穿透手段，如果你有需要 web 以外的連線，請在電腦上安裝 `cloudflared client` 即可連線 TCP/UDP 協議等（像是 Minecraft 伺服器）等

| CCP預設使用容器的 Port | 對應地址 |
|---|---|
| 22 | `ssh.calou.cc:<port>` |
| 3000 | `web-<yourname>.calou.cc` |
| 3100 | `dev-<yourname>.calou.cc` |

## 我可以用自己的網域嗎？
可以，如果你有自己的網域，也會使用 `cloudflared tunnel` ，我們允許你使用 `chcfd <token>` 更改 tunnel 的導向。

## 重啟你的容器
```shell
sudo kill 1
```
大概10秒內會完成重啟的動作，記得重新連線。
