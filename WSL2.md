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
