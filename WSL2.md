# WSL2環境メモ

## WSL2 (Ubuntu)
Microsoft Store からUbuntu-20.04をインストール

WSL2をデフォルト[PowerShell]
```
> wsl --set-default 2
```

Ubuntu-20.04を起動

パッケージの更新[bash]
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install python-is-python3 mlocate

$ sudo apt install docker.io
$ sudo usermod -a -G docker user1

```



## Windows Terminal
[setting.json]
```
{
     "acrylicOpacity": 0.9,
     "cursorShape":"filledBox" ,
     "fontFace": "BIZ UDゴシック",
     "guid": "{07b52e3e-de2c-5db4-bd2d-ba144ed6c273}",
     "hidden": false,
     "name": "Ubuntu-20.04",
     "source": "Windows.Terminal.Wsl",
     "startingDirectory": "//wsl$/Ubuntu-20.04/home/%USERNAME%",
     "useAcrylic": true
}
```

## VSCode と fish

VSCodeをインストール

WSL2にfishをインストール
[bash]
```
$ sudo apt install fish
$ fish
<W> fish: Error while searching for command '/mnt/c/Program Files (x86)/...'
access: Input/output error
```
WSL2がPATHに追加するWindowsのPATHがfishのコマンド補完と相性が悪い模様。

[WSLでWindowsのPATHを引き継がないようにする方法](https://qiita.com/raccy/items/456a7158f588670c0850)

しかし、これをやると下記のWSL2からVSCodeの呼び出しが出来なくなる模様。
```
$ code .
```

```rm /etc/wsl.conf```など色々いじっていたらfishが何も言わなくなった。理由は不明。

## tmux
マウス選択でコピー
```
bind-key    -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-selection-and-cancel 'cat | clip.exe'
```
https://qiita.com/yujiG/items/b6971684dd97235f73f9

clip.exeでクリップボードにデータを送れる（逆はclip.exeではできない）
https://kashewnuts.github.io/2020/06/11/wsl2.html
https://www.atmarkit.co.jp/ait/articles/1903/14/news060.html


https://github.com/zchee/tmux-ja/blob/master/tmux-ja.rst
https://qh73xebitbucketorg.readthedocs.io/ja/latest/2.Tools/tmux/tips/
https://blog.monochromegane.com/blog/2013/12/12/tmux-no-prefix/

## X
MobaXTermが簡単
https://qiita.com/vega77/items/f00323e8ce64bfa1fdd6



## Docker
systemctl
https://github.com/DamionGans/ubuntu-wsl2-systemd-script
