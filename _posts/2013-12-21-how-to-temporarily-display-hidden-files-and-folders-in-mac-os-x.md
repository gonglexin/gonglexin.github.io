---
title: Mac 下临时显示隐藏的文件和文件夹
categories: [tech]
---

今天遇到一个问题, 在使用 Github 的 Mac 客户端的时候, 想直接导入已经 clone 到本地的 repo, 但是这个 repo 目录是一个以 . 为开头的格式命名的隐藏目录, 在打开的文件选择窗口里面是无法看到的。

以前我一般是打开终端输入如下命令:
```shell
defaults write com.apple.finder AppleShowAllFiles TRUE; killall Finder
```

这条命令有一个不便利的地方就是执行之后系统就会一直显示那些隐藏文件，往往等你操作完之后，你又需要把值重新设置回去:
```shell
defaults write com.apple.finder AppleShowAllFiles FALSE; killall Finder
```

今天才发现，原来在选择文件的时候, 只需要按下 **`Command + Shift + .`** 组合键就可以临时地显示隐藏文件了。当然这不仅仅适用于这一个软件，Mac 下所有软件的文件选择窗口都是可以这么做的。

参考: [http://www.tekrevue.com/tip/how-to-temporarily-see-hidden-files-folders-in-mac-os-x/](http://www.tekrevue.com/tip/how-to-temporarily-see-hidden-files-folders-in-mac-os-x/)
