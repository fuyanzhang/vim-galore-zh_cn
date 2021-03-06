# vim-galore 中文翻译

[![掘金翻译计划](https://rawgit.com/aleen42/badges/master/src/juejin_translation.svg)](https://github.com/xitu/gold-miner/)

> Vim from zero to hero - Vim 从入门到精通

- 原文地址：https://github.com/mhinz/vim-galore
- 原文作者：Marco Hinz
- 本文地址：https://github.com/wsdjeg/vim-galore-zh_cn

## [简介](#简介-1)

- [什么是 Vim](#什么是-vim)
- [Vim 哲学](#vim-哲学)
- [入门](#入门)
- [精简的 vimrc](#精简的-vimrc)
- [我正在使用的是什么样的 Vim](#我正在使用什么样的-vim)
- [备忘录](#备忘录)

## [基础](#基础-1)

- [缓冲区，窗口，标签](#缓冲区窗口标签)
- [当前缓冲区，加载缓冲区，缓冲区列表，命名缓冲区](#已激活已载入已列出已命名缓冲区)
- [参数列表](#参数列表)
- [按键映射](#按键映射)
- [映射占位符](#映射占位符)
- [寄存器](#寄存器)
- [范围](#范围)
- [标注](#标注)
- [补全](#补全)
- [动作，操作符，文本对象](#动作操作符文本对象)
- [自动命令](#自动命令)
- [变更历史，跳转历史](#变更历史跳转历史)
- [内容变更历史记录](#内容变更历史记录)
- [全局位置信息表，局部位置信息表](#全局位置信息表局部位置信息表)
- [宏](#宏)
- [颜色主题](#颜色主题)
- [折叠](#折叠)
- [会话](#会话)
- [局部化](#局部化)

## [用法](#用法-1)

- [获取离线帮助](#获取离线帮助)
- [获取离线帮助(备选)](#获取离线帮助备选)
- [获取在线帮助](#获取在线帮助)
- [执行自动命令](#执行自动命令)
  - [用户自定义事件](#用户自定义事件)
  - [内部自带事件](#内部自带事件)
- [剪贴板](#剪切板)
  - [剪贴板使用 (Windows, OSX)](#剪贴板使用-windows-osx)
  - [剪贴板使用 (Linux, BSD, ...)](#剪贴板使用-linux-bsd-)
- [打开文件时恢复光标位置](#打开文件时恢复光标位置)
- [备份文件，交换文件，撤销文件以及 viminfo 文件的处理](#备份文件交换文件撤销文件以及-viminfo-文件的处理)
- [编辑远程文件](#编辑远程文件)
- [插件管理](#插件管理)
- [片段插入](#片段插入)
- [使用外部程序和过滤器](#使用外部程序和过滤器)
- [MatchIt](#matchit)

## [技巧](#技巧-1)

- [聪明的使用 n 和 N](#聪明的使用-n-和-n)
- [聪明的使用命令行历史](#聪明的使用命令行历史)
- [智能 Ctrl-l](#智能-ctrl-l)
- [禁用错误报警声音和图标](#禁用错误报警声音和图标)
- [快速移动当前行](#快速移动当前行)
- [快速添加空行](#快速添加空行)
- [快速编辑自定义宏](#快速编辑自定义宏)
- [快速跳转到源(头)文件](#快速跳转到源头文件)
- [在 GUI 中快速改变字体大小](#在-gui-中快速改变字体大小)
- [根据模式改变光标类型](#根据模式改变光标类型)
- [防止水平滑动的时候失去选择](#防止水平滑动的时候失去选择)
- [重新载入保存文件](#重新载入保存文件)
- [智能当前行](#智能当前行)
- [更快的关键字补全](#更快的关键字补全)

## [命令](#命令-1)

- [:global](#global---在所有匹配行执行命令) - 在所有匹配行执行命令
- [:normal and :execute](#normal-and-execute---脚本梦之队) - 脚本梦之队
- [:redir](#redir---重定向消息) - 重定向消息

## [调试](#调试-1)

- [常规建议](#常规建议)
- [查看启动日志](#查看启动日志)
- [查看运行时日志](#查看运行时日志)
- [调整日志等级](#调整日志等级)
- [Vim 脚本调试](#vim-脚本调试)
- [语法文件调试](#语法文件调试)

## [杂项](#杂项-1)

- [附加资源](#附加资源)
- [Vim 配置集合](#vim-配置集合)
- [内置插件](#内置插件)
- [将 Control 映射到 CapsLock](#将-control-映射到-capslock)
- [复活节彩蛋](#复活节彩蛋)
- [为何使用 hjkl](#为何使用-hjkl)

## [怪癖](#怪癖-1)

- [编辑小文件很慢](#编辑小文件很慢)
- [编辑大文件很慢](#编辑大文件很慢)
- [新行用于 NUL](#新行用于-nul)
- [相同部分粘贴 (要不为什么我总要设置‘粘贴’?)](#相同部分粘贴-要不为什么我总要设置粘贴)
- [在终端使用 Esc 延时](#在终端使用-esc-延时)
- [无法重复函数中执行的搜索](#无法重复函数中执行的搜索)

## [主题列表](#主题列表-1)

## [插件列表](content/plugins.md)

## [Neovim](content/neovim.md)

---

# 简介

## 什么是 Vim？
[Vim](http://www.vim.org) 是一个历史悠久的文本编辑器，可以追溯到 [qed](https://en.wikipedia.org/wiki/QED_(text_editor))。[Bram
Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar) 于 1991 年发布初始版本。

该项目托管在 [vim.org](http://www.vim.org/index.php)。

获取 Vim：用包管理器安装或者直接到 vim.org [下载](http://www.vim.org/download.php)。

讨论使用相关问题最好使用 [vim_use](https://groups.google.com/forum/#!forum/vim_use) 邮件列表或者使用 IRC([Freenode](https://freenode.net)) 的 `#vim` 频道。

欢迎加入我们的中文讨论群：[![QQ](https://img.shields.io/badge/QQ%e7%be%a4-121056965-blue.svg)](https://jq.qq.com/?_wv=1027&k=43DB6SG)

项目在 [Github](https://github.com/vim/vim) 上开发，项目讨论请订阅 [vim_dev](https://groups.google.com/forum/#!forum/vim_dev) 邮件列表。

通过阅读 [Why, oh WHY, do those #?@! nutheads use vi?](http://www.viemu.com/a-why-vi-vim.html) 来对 Vim 进行大致的了解。

## Vim 哲学

Vim 采用模式编辑的理念，即它提供了多种模式，按键在不同的模式下作用不同。你可以在 _普通模式_ 下浏览文件，在 _插入模式_ 下插入文本，在 _可视模式_ 下选择行，在 _命令模式_ 下执行命令等等。起初这听起来可能很复杂，但是这有一个很大的优点：不需要通过同时按住多个键来完成操作，大多数时候你只需要依次按下这些按键即可。越常用的操作，所需要的按键数量越少。

和模式编辑紧密相连的概念是“操作符”和“动作”。_操作符_开始一些行为，例如：修改，删除，或者选择文本。之后你要用一个_动作_来指定需要操作的文本区域。比如，要改变括号内的文本，需要执行 `ci(` （读做 _change inner parentheses_）；删除整个段落的内容，需要执行 `dap` （读做：_delete
around paragraph_）。

如果你能看见 Vim 老司机操作，你会发现他们使用 Vim 脚本语言就如同钢琴师弹钢琴一样。复杂的操作只需要几个按键就能完成。他们甚至不用刻意去想，因为这已经成为[肌肉记忆](https://en.wikipedia.org/wiki/Muscle_memory)了。这减少[认识负荷](https://en.wikipedia.org/wiki/Cognitive_load)并帮助人们专注于实际任务。

## 入门

Vim 自带一个交互式的教程，内含你需要了解的最基础的信息，你可以通过终端运行以下命令打开教程：

```
$ vimtutor
```

不要因为这个看上去很无聊而跳过，按照此教程多练习。你以前用的 IDE 或者其他编辑器很少是有“模式”概念的，因此一开始你会很难适应模式切换。但是你 Vim 使用的越多，[肌肉记忆](https://en.wikipedia.org/wiki/Muscle_memory) 将越容易形成。

Vim 基于一个 [vi](https://en.wikipedia.org/wiki/Vi) 克隆，叫做 [Stevie](https://en.wikipedia.org/wiki/Stevie_(text_editor))，支持两种运行模式："compatible" 和 "nocompatible"。在兼容模式下运行 Vim 意味着使用 vi 的默认设置，而不是 Vim 的默认设置。除非你新建一个用户的 `vimrc` 或者使用 `vim -N` 命令启动 Vim，否则就是在兼容模式下运行 Vim！请大家不要在兼容模式下运行 Vim。

下一步

1. 创建你自己的 [vimrc](#精简的-vimrc)。
2. 在第一周准备[备忘录](#备忘录)。
3. 通读[基础](#基础-1)章节了解 Vim 还有哪些功能。
4. 按需学习！Vim 是学不完的。如果你遇到了问题，先上网寻找解决方案，你的问题可能已经被解决了。Vim 拥有大量的参考文档，知道如何利用这些参考文档很有必要：[获取离线帮助](#获取离线帮助)。
5. 浏览[附加资源](#附加资源)。

最后一个建议：使用[插件](#插件管理)之前，请先掌握 Vim 的基本操作。很多插件都只是对 Vim 自带功能的封装。

## 精简的 vimrc

用户的 vimrc 配置文件可以放在 `~/.vimrc`，或者为了更好的分离放在 `~/.vim/vimrc`，后者更便于通过版本控制软件备份和同步整个配置，比方说 Github。

你可以在网上找到许多精简的 vimrc 配置文件，我的版本可能并不是最简单的版本，但是我的版本提供了一套我认为良好的，非常适合入门的设置。

最终你需要阅读完那些设置，然后自行决定需要使用哪些。:-)

精简的 vimrc 地址：[minimal-vimrc](contents/minimal-vimrc.vim)

如果你有兴趣，这里是我（原作者）的 [vimrc](https://github.com/mhinz/dotfiles/blob/master/vim/vimrc)。

**建议**：大多数插件作者都维护不止一个插件并且将他们的 vimrc 放在 Github 上展示（通常放在叫做 "vim-config" 或者 "dotfiles" 的仓库中），所以当你发现你喜欢的插件时，去插件维护者的 Github 主页看看有没有这样的仓库。

## 我正在使用什么样的 Vim

使用 `:version` 命令将向你展示当前正在运行的 Vim 的所有相关信息，包括它是如何编译的。

第一行告诉你这个二进制文件的编译时间和版本号，比如：7.4。接下来的一行呈现 `Included patches: 1-1051`，这是补丁版本包。因此你 Vim 确切的版本号是  7.4.1051。

另一行显示着一些像 `Tiny version without GUI` 或者 `Huge version with GUI` 的信息。很显然这些信息告诉你当前的 Vim 是否支持 GUI，例如：从终端中运行 `gvim` 或者从终端模拟器中的 Vim 内运行 `:gui` 命令。另一个重要的信息是 `Tiny` 和 `Huge`。Vim 的特性集区分被叫做 `tiny`，`small`，`normal`，`big` and `huge`，所有的都实现不同的功能子集。

`:version` 主要的输出内容是特性列表。`+clipboard` 意味这剪贴板功能被编译支持了，`-clipboard` 意味着剪贴板特性没有被编译支持。

一些功能特性需要编译支持才能正常工作。例如：为了让 `:prof` 工作，你需要使用 `huge` 模式编译的 Vim，因为那种模式启用了 `+profile` 特性。

如果你的输出情况并不是那样，并且你是从包管理器安装 Vim 的，确保你安装了 `vim-x`，`vim-x11`，`vim-gtk`，`vim-gnome` 这些包或者相似的，因为这些包通常都是 `huge` 模式编译的。

你也可以运行下面这段代码来测试 Vim 版本以及功能支持：

```vim
" Do something if running at least Vim 7.4.42 with +profile enabled.
if (v:version > 704 || v:version == 704 && has('patch42')) && has('profile')
  " do stuff
endif
```

相关帮助：

```
:h :version
:h feature-list
:h +feature-list
```

## 备忘录

为了避免版权问题，我只贴出链接：

- http://people.csail.mit.edu/vgod/vim/vim-cheat-sheet-en.png
- https://cdn.shopify.com/s/files/1/0165/4168/files/preview.png
- http://www.nathael.org/Data/vi-vim-cheat-sheet.svg
- http://michael.peopleofhonoronly.com/vim/vim_cheat_sheet_for_programmers_screen.png
- http://www.rosipov.com/images/posts/vim-movement-commands-cheatsheet.png

或者在 Vim 中快速打开备忘录：[vim-cheat40](https://github.com/lifepillar/vim-cheat40)。

# 基础

## 缓冲区，窗口，标签

Vim 是一个文本编辑器。每次文本都是作为**缓冲区**的一部分显示的。每一份文件都是在他们自己独有的缓冲区打开的，插件显示的内容也在它们自己的缓冲区中。

缓冲区有很多属性，比如这个缓冲区的内容是否可以修改，或者这个缓冲区是否和文件相关联，是否需要同步保存到磁盘上。

**窗口** 是缓冲区上一层的视窗。如果你想同时查看几个文件或者查看同一文件的不同位置，那样你会需要窗口。

请别把他们叫做_分屏_。你可以把一个窗口分割成两个，但是这并没有让这两个窗口完全_分离_。

窗口可以水平或者竖直分割并且现有窗口的高度和宽度都是可以被调节设置的，因此，如果你需要多种窗口布局，请考虑使用标签。

**标签页** （标签）是窗口的集合。因此使用标签当你想使用多种窗口布局的时候。

简单的说，如果你启动 Vim 的时候没有附带任何参数，你会得到一个包含着一个呈现一个缓冲区的窗口的标签。

顺带提一下，缓冲区列表是全局可见的，你可以在任何标签中访问任何一个缓冲区。

## 已激活，已载入，已列出，已命名，缓冲区

用类似 `vim file1` 的命令启动 Vim 。这个文件的内容将会被加载到缓冲区中，你现在有一个**已载入的缓冲区**。如果你在 Vim 中保存这个文件，缓冲区内容将会被同步到磁盘上（写回文件中）。

由于这个缓冲区也在一个窗口上显示，所以他也是一个**已激活的缓冲区**。如果你现在通过 `:e file2` 命令加载另一个文件，`file1` 将会变成一个**隐藏的缓冲区**，并且 `file2` 变成已激活缓冲区。

使用 `:ls` 我们能够列出所有可以列出的缓冲区。插件缓冲区和帮助缓冲区通常被标记为不可以列出的缓冲区，因为那并不是你经常需要在编辑器中编辑的常规文件。通过 `:ls!` 命令可以显示被放入缓冲区列表的和未被放入列表的缓冲区。

**未命名的缓冲区**是一种没有关联特定文件的缓冲区，这种缓冲区经常被插件使用。比如 `:enew` 将会创建一个无名临时缓冲区。添加一些文本然后使用 `:w /tmp/foo` 将他写入到磁盘，这样这个缓冲区就会变成一个**已命名的缓冲区**。

## 参数列表

[全局缓冲区列表](#缓冲区窗口标签)是 Vim 的特性。在这之前的 vi 中，仅仅只有参数列表，参数列表在 Vim 中依旧可以使用。

每一个通过 shell 命令传递给 Vim 的文件名都被记录在一个参数列表中。可以有多个参数列表：默认情况下所有参数都被放在全局参数列表下，但是你可以使用 `:arglocal` 命令去创建一个新的本地窗口的参数列表。

使用 `:args` 命令可以列出当前参数。使用 `:next`，`:previous`，`:first`，`:last` 命令可以在切换在参数列表中的文件。通过使用 `:argadd`，`:argdelete` 或者 `:args` 等命令加上一个文件列表可以改变参数列表。

偏爱缓冲区列表还是参数列表完全是个人选择，我的印象中大多数人都是使用缓冲区列表的。

然而参数列表在有些情况下被大量使用：批处理
使用 `:argdo`！ 一个简单的重构例子：

```vim
:args **/*.[ch]
:argdo %s/foo/bar/ge | update
```

这条命令将替换掉当前目录下以及当前目录的子目录中所有的 C 源文件和头文件中的“foo”，并用“bar”代替。

相关帮助：`:h argument-list`

## 按键映射

使用 `:map` 命令家族你可以定义属于你自己的快捷键。该家族的每一个命令都限定在特定的模式下。从技术上来说 Vim 自带高达 12 中模式，其中 6 种可以被映射。另外一些命令作用于多种模式：

|    递归    |   非递归      | 模式                            |
|-----------|---------------|----------------------------------|
| `:map`    | `:noremap`    | normal, visual, operator-pending |
| `:nmap`   | `:nnoremap`   | normal                           |
| `:xmap`   | `:xnoremap`   | visual                           |
| `:cmap`   | `:cnoremap`   | command-line                     |
| `:omap`   | `:onoremap`   | operator-pending                 |
| `:imap`   | `:inoremap`   | insert                           |

例如：这个自定义的快捷键只在普通模式下工作。

```vim
:nmap <space> :echo "foo"<cr>
```

使用 `:nunmap <space>` 可以取消这个映射。

对于更少数，不常见的模式（或者他们的组合），查看 `:h map-modes`。

到现在为止还好，对新手而言有一个问题会困扰他们：`:nmap` 是**递归执行**的！结果是，右边执行可能的映射。

你自定义了一个简单的映射去输出“Foo”：

```vim
:nmap b :echo "Foo"<cr>
```

但是如果你想要映射 `b` （回退一个单词）的默认功能到一个键上呢？

```vim
:nmap a b
```

如果你敲击<kbd>a</kbd>，我们期望着光标回退到上一个单词，但是实际情况是“Foo”被输出到命令行里！因为在右边，`b` 已经被映射到别的行为上了，换句话说就是 `:echo "Foo"<cr>`。

解决此问题的正确方法是使用一种_非递归_的映射代替：

```vim
:nnoremap a b
```

经验法则：除非递归是必须的，否则总是使用非递归映射。

通过不给一个右值来检查你的映射。比如`:nmap` 显示所以普通模式下的映射，`:nmap <leader>` 显示所有以 `<leader>` 键开头的普通模式下的映射。

如果你想禁止用标准映射，把他们映射到特殊字符 `<nop>` 上，例如：`:noremap <left> <nop>`。

相关帮助：

    :h key-notation
    :h mapping
    :h 05.3

## 映射占位符

映射占位符（Leader 键）本身就是一个按键映射，默认为 <kbd>\\</kbd>。我们可以通过在 `map` 中调用 `<leader>` 来为把它添加到其他按键映射中。

```vim
nnoremap <leader>h :helpgrep<space>
```

这样，我们只需要先按 <kbd>\\</kbd> 然后连续按 <kbd>\\h</kbd> 就可以激活这个映射 `:helpgrep<space>`。如果你想通过先按 <kbd>空格</kbd> 键来触发，只需要这样做：

```vim
let mapleader = ' '
nnoremap <leader>h :helpgrep<space>
```

另外，还有一个叫 `<localleader>` 的，可以把它理解为局部环境中的 `<leader>`，默认值依然为 <kbd>\\</kbd>。当我们需要只对某一个条件下（比如，特定文件类型的插件）的缓冲区设置特别的 `<leader>` 键，那么我们就可以通过修改当前环境下的 `<localleader>` 来实现。

**注意**：如果你打算设置 Leader 键，请确保在设置按键映射之前，先设置好 Leader 键。如果你先设置了含有 Leader 键的映射，然后又修改了 Leader 键，那么之前映射内的 Leader 键是不会因此而改变的。你可以通过执行 `:nmap <leader>` 来查看普通模式中已绑定给 Leader 键的所有映射。

请参阅 `:h mapleader` 与 `:h maploacalleader` 来获取更多帮助。

## 寄存器

寄存器就是存储文本的地方。我们常用的「复制」操作就是把文本存储到寄存器，「 粘贴」 操作就是把文本从寄存器中读出来。顺便，在 Vim 中复制的快捷键是 <kbd>y</kbd>，粘贴的快捷键是 <kbd>p</kbd>。

Vim 为我们提供了如下的寄存器：

| 类型 | 标识 | 读写者 | 是否为只读 | 包含的字符来源 |
| ---- | ---- | ------ | ---------- | -------------- |
| Unnamed | `"` | vim | 否 | 最近一次的复制或删除操作 (`d`, `c`, `s`, `x`, `y`) |
| Numbered | `0`至`9` | vim | 否 | 寄存器 `0`: 最近一次复制。寄存器 `1`: 最近一次删除。寄存器 `2`: 倒数第二次删除，以此类推。对于寄存器 `1` 至 `9`，他们其实是只读的最多包含 9 个元素的队列。这里的队列即为数据类型 [queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type)) |
| Small delete | `-` | vim | 否 | 最近一次行内删除 |
| Named | `a`至`z`, `A`至`Z` | 用户 | 否 | 如果你通过复制操作存储文本至寄存器 `a`，那么 `a` 中的文本就会被完全覆盖。如果你存储至 `A`，那么会将文本添加给寄存器 `a`，不会覆盖之前已有的文本 |
| Read-only | `:`与`.`和`%` | vim | 是 | `:`: 最近一次使用的命令，`.`: 最近一次添加的文本，`%`: 当前的文件名 |
| Alternate buffer | `#` | vim | 否 | 大部分情况下，这个寄存器是当前窗口中，上一次访问的缓冲区。请参阅 `:h alternate-file` 来获取更多帮助 |
| Expression | `=` | 用户 | 否 | 复制 VimL 代码时，这个寄存器用于存储代码片段的执行结果。比如，在插入模式下复制 `<c-r>=5+5<cr>`，那么这个寄存器就会存入 10 |
| Selection | `+`和`*` | vim | 否 | `*` 和 `+` 是 [剪贴板](#剪贴板) 寄存器 |
| Drop | `~` | vim | 是 | 最后一次拖拽添加至 Vim 的文本（需要 "+dnd" 支持，暂时只支持 GTK GUI。请参阅 `:help dnd` 及 `:help quote~`） |
| Black hole | `_` | vim | 否 | 一般称为黑洞寄存器。对于当前操作，如果你不希望在其他寄存器中保留文本，那就在命令前加上 `_`。比如，`"_dd` 命令不会将文本放到寄存器 `"`、`1`、`+` 或 `*` 中 |
| Last search pattern | `/` | vim | 否 | 最近一次通过 `/`、`?` 或 `:global` 等命令调用的匹配条件 |

只要不是只读的寄存器，用户都有权限修改它的内容，比如：

```vim
:let @/ = 'register'
```

这样，我们按 <kbd>n</kbd> 的时候就会跳转到单词"register" 出现的地方。

有些时候，你的操作可能已经修改了寄存器，而你没有察觉到。请参阅 `:h registers` 获取更多帮助。

上面提到过，复制的命令是 <kbd>y</kbd>，粘贴的命令是 <kbd>p</kbd> 或者 <kbd>P</kbd>。但请注意，Vim 会区分「字符选取」与「行选取」。请参阅 `:h linewise` 获取更多帮助。

**行选取**：
命令 `yy` 或 `Y` 都是复制当前行。这时移动光标至其他位置，按下 `p` 就可以在光标下方粘贴复制的行，按下 `P` 就可以在光标上方粘贴至复制的行。

**字符选取**：
命令 `0yw` 可以复制第一个单词。这时移动光标至其他位置，按下 `p` 就可以在当前行、光标后的位置粘贴单词，按下 `P` 就可以在当前行、光标前的位置粘贴单词。

**将文本存到指定的寄存器中**：
命令 `"aY` 可以将当前行复制，并存储到寄存器 `a` 中。这时移动光标至其他位置，通过命令 `"AY` 就可以把这一行的内容扩展到寄存器 `a` 中，而之前存储的内容也不会丢失。

为了便于理解和记忆，建议大家现在就试一试上面提到的这些操作。操作过程中，你可以随时通过 `:reg` 来查看寄存器的变化。

**有趣的是**：
在 Vim 中，`y` 是复制命令，源于单词 "yanking"。而在 Emacs 中，"yanking" 代表的是粘贴（或者说，重新插入刚才删掉的内容），而并不是复制。

## 范围

范围 (Ranges) 其实很好理解，但很多 Vim 用户的理解不到位。

- 很多命令都可以加一个数字，用于指明操作范围
- 范围可以是一个行号，用于指定某一行
- 范围也可以是一对通过 `,` 或 `;` 分割的行号
- 大部分命令，默认只作用于当前行
- 只有 `:write` 和 `:global` 是默认作用于所有行的

范围的使用是十分直观的。以下为一些例子（其中，`:d` 为 `:delete` 的缩写）：

| 命令 | 操作的行 |
| ---- | -------- |
| `:d` | 当前行 |
| `:.d` | 当前行 |
| `:1d` | 第一行 |
| `:$d` | 最后一行 |
| `:1,$d` | 所有行 |
| `:%d` | 所有行（这是 `1,$` 的语法糖） |
| `:.,5d` | 当前行至第 5 行 |
| `:,5d` | 同样是当前行至第 5 行 |
| `:,+3d` | 当前行及接下来的 3 行 |
| `:1,+3d` | 第一行至当前行再加 3 行 |
| `:,-3d` | 当前行及向上的 3 行（Vim 会弹出提示信息，因为这是一个保留的范围） |
| `:3,'xdelete` | 第三行至[标注](#标注) 为 x 的那一行 |
| `:/^foo/,$delete` | 当前行以下，以字符 "foo" 开头的那一行至结尾 |
| `:/^foo/+1,$delete` | 当前行以下，以字符 "foo" 开头的那一行的下一行至结尾 |

需要注意的是，`;` 也可以用于表示范围。区别在于，`a,b` 的 `b` 是以当前行作为参考的。而 `a;b` 的 `b` 是以 `a` 行作为参考的。举个例子，现在你的光标在第 5 行。这时 `:1,+1d` 会删除第 1 行至第 6 行，而 `:1;+1d` 会删除第 1 行和第 2 行。

如果你想设置多个寻找条件，只需要在条件前加上 `/`，比如：

```vim
:/foo//bar//quux/d
```

这就会删除当前行之后的某一行。定位方式是，先在当前行之后寻找第一个包含 "foo" 字符的那一行，然后在找到的这一行之后寻找第一个包含 "bar" 字符的那一行，然后再在找到的这一行之后寻找第一个包含 "quux" 的那一行。删除的就是最后找到的这一行。

有时，Vim 会在命令前自动添加范围。举个例子，如果你先通过 `V` 命令进入行选取模式，选中一些行后按下 `:` 进入命令模式，这时候你会发现 Vim 自动添加了 `'<,'>` 范围。这表示，接下来的命令会使用之前选取的行号作为范围。但如果后续命令不支持范围，Vim 就会报错。为了避免这样的情况发生，有些人会设置这样的按键映射：`:vnoremap foo :<c-u>command`，组合键 <kbd>Ctrl + u</kbd> 可以清除当前命令行中的内容。

另一个例子是在普通模式中按下 `!!`，命令行中会出现 `:.!`。如果这时你如果输入一个外部命令，那么当前行的内容就会被这个外部命令的输出替换。你也可以通过命令 `:?^$?+1,/^$/-1!ls` 把当前段落的内容替换成外部命令 `ls` 的输出，原理是向前和向后各搜索一个空白行，删除这两个空白行之间的内容，并将外部命令 `ls` 的输出放到这两个空白行之间。

请参阅以下两个命令来获取更多帮助：

```vim
:h cmdline-ranges
:h 10.3
```

## 标注

你可以使用标注功能来标记一个位置，也就是记录文件某行的某个位置。

| 标注 | 设置者 | 使用 |
| ---- | ------ | ---- |
| `a`-`z` | 用户 | 仅对当前的一个文件生效，也就意味着只可以在当前文件中跳转 |
| `A`-`Z` | 用户 | 全局标注，可以作用于不同文件。大写标注也称为「文件标注」。跳转时有可能会切换到另一个缓冲区 |
| `0`-`9` | viminfo | `0` 代表 viminfo 最后一次被写入的位置。实际使用中，就代表 Vim 进程最后一次结束的位置。`1` 代表 Vim 进程倒数第二次结束的位置，以此类推 |

如果想跳转到指定的标注，你可以先按下 `'`、`g'`、`\`` 或 `g\`` 然后按下标注名。

如果你想定义当前文件中的标注，可以先按下 `m` 再按下标注名。比如，按下 `mm` 就可以把当前位置标注为 `m`。在这之后，如果你的光标切换到了文件的其他位置，只需要通过 `'m` 或者 `\`m` 即可回到刚才标注的行。区别在于，`'m` 会跳转回被标记行的第一个非空字符，而 `\`m` 会跳转回被标记行的被标记列。根据 viminfo 的设置，你可以在退出 Vim 的时候保留小写字符标注。请参阅 `:h viminfo-'` 来获取更多帮助。

如果你想定义全局的标注，可以先按下 `m` 再按下大写英文字符。比如，按下 `mM` 就可以把当前文件的当前位置标注为 `M`。在这之后，就算你切换到其他的缓冲区，依然可以通过 `'M` 或 `\`M` 跳转回来。

关于跳转，还有以下的方式：

| 按键 | 跳转至 |
| ---- | ------ |
| `'[` 与 `` `[ `` | 上一次修改或复制的第一行或第一个字符 |
| `']` 与 `` `] `` | 上一次修改或复制的最后一行或最后一个字符 |
| `'<` 与 `` `< `` | 上一次在可视模式下选取的第一行或第一个字符 |
| `'>` 与 `` `> `` | 上一次在可视模式下选取的最后一行或最后一个字符 |
| `''` 与 `` `' `` | 上一次跳转之前的光标位置 |
| `'"` 与 `` `" `` | 上一次关闭当前缓冲区时的光标位置 |
| `'^` 与 `` `^ `` | 上一次插入字符后的光标位置 |
| `'.` 与 `` `. `` | 上一次修改文本后的光标位置 |
| `'(` 与 `` `( `` | 当前句子的开头 |
| `')` 与 `` `) `` | 当前句子的结尾 |
| `'{` 与 `` `{ `` | 当前段落的开头 |
| `'}` 与 `` `} `` | 当前段落的结尾 |

标注也可以搭配 [范围](#范围) 一起使用。前面提到过，如果你在可视模式下选取一些文本，然后按下 `:`，这时候你会发现命令行已经被填充了 `:'<,'>`。对照上面的表格，现在你应该明白了，这段代表的就是可视模式下选取的范围。

请使用 `:marks` 命令来显示所有的标注，参阅 `:h mark-motions` 来获取关于标注的更多帮助。

## 补全

Vim 在插入模式中为我们提供了多种补全方案。如果有多个补全结果，Vim 会弹出一个菜单供你选择。

常见的补全有标签、项目中引入的模块或库中的方法名、文件名、字典及当前缓冲区的字段。

针对不同的补全方案，Vim 为我们提供了不同的按键映射。这些映射都是在**插入模式中**通过 <kbd>Ctrl</kbd> + <kbd>x</kbd> 来触发：

| 映射 | 类型 | 帮助文档 |
| ---- | ---- | -------- |
| `<c-x><c-l>` | 整行 | `:h i^x^l` |
| `<c-x><c-n>` | 当前缓冲区中的关键字 | `:h i^x^n` |
| `<c-x><c-k>` | 字典（请参阅 `:h 'dictionary'`）中的关键字 | `:h i^x^k` |
| `<c-x><c-t>` | 同义词字典（请参阅 `:h 'thesaurus'`）中的关键字 | `:h i^x^t` |
| `<c-x><c-i>` | 当前文件以及包含的文件中的关键字 | `:h i^x^i` |
| `<c-x><c-]>` | 标签 | `:h i^x^]` |
| `<c-x><c-f>` | 文件名 | `:h i^x^f` |
| `<c-x><c-d>` | 定义或宏定义 | `:h i^x^d` |
| `<c-x><c-v>` | Vim 命令 | `:h i^x^v` |
| `<c-x><c-u>` | 用户自定义补全（通过 `'completefunc'` 定义） | `:h i^x^u` |
| `<c-x><c-o>` | Omni Completion（通过 `'omnifunc'` 定义） | `:h i^x^o` |
| `<c-x>s` | 拼写建议 | `:h i^Xs` |

尽管用户自定义补全与 Omni Completion 是不同的，但他们做的事情基本一致。共同点在于，他们都是一个监听当前光标位置的函数，返回值为一系列的补全建议。用户自定义补全是由用户定义的，基于用户的个人用途，因此你可以根据自己的喜好和需求随意定制。而 Omni Completion 是针对文件类型的补全，比如在 C 语言中补全一个结构体（struct）的成员（members），或者补全一个类的方法，因而它通常都是由文件类型插件设置和调用的。

如果你设置了 `'complete'` 选项，那么你就可以在一次操作中采用多种补全方案。这个选项默认包含了多种可能性，因此请按照自己的需求来配置。你可以通过 `<c-n>` 来调用下一个补全建议，或通过 `<c-p>` 来调用上一个补全建议。当然，这两个映射同样可以直接调用补全函数。请参阅 `:h i^n` 与 `:h 'complete'` 来获得更多帮助。

如果你想配置弹出菜单的行为，请一定要看一看 `:h 'completeopt'` 这篇帮助文档。默认的配置已经不错了，但我个人（原作者）更倾向于把 "noselect" 加上。

请参阅以下文档获取更多帮助：
```vim
:h ins-completion
:h popupmenu-keys
:h new-omni-completion
```

## 动作，操作符，文本对象

**动作**也就是指移动光标的操作，你肯定很熟悉 `h`、`j`、`k` 和 `l`，以及 `w` 和 `b`。但其实，`/` 也是一个动作。他们都可以搭配数字使用，比如 `2?the<cr>` 可以将光标移动到倒数第二个 "the" 出现的位置。

以下会列出一些常用的动作。你也可以通过 `:h navigation` 来获取更多的帮助。

**操作符**是对某个区域文本执行的操作。比如，`d`、`~`、`gU` 和 `>` 都是操作符。这些操作符既可以在普通模式下使用，也可以在可视模式下使用。在普通模式中，顺序是先按操作符，再按动作指令，比如 `>j`。在可是模式中，选中区域后直接按操作符就可以，比如 `Vjd`。

与动作一样，操作符也可以搭配数字使用，比如 `2gUw` 可以将当前单词以及下一个单词转成大写。由于动作和操作符都可以搭配数字使用，因此 `2gU2w` 与执行两次 `gU2w` 效果是相同的。

请参阅 `:h operator` 来查看所有的操作符。你也可以通过 `:set tildeop` 命令把 `~` 也变成一个操作符

值得注意的是，动作是单向的，而**文本对象**是双向的。文本对象不仅作用于符号（比如括号、中括号和大括号等）标记的范围内，也作用于整个单词、整个句子等其他情况。

文本对象不能用于普通模式中移动光标的操作，因为光标还没有智能到可以向两个方向同时跳转。但这个功能可以在可视模式中实现，因为在对象的一端选中的情况下，光标只需要跳转到另一端就可以了。

文本对象操作一般用 `i` 或 `a` 加上对象标识符操作，其中 `i` 表示在对象内（英文 inner）操作，`a` 表示对整个对象（英文 around）操作，这时开头和结尾的空格都会被考虑进来。举个例子，`diw` 可以删除当前单词，`ci(` 可以改变括号中的内容。

文本对象同样可以与数字搭配使用。比如，像 `(((  )))` 这样的文本，假如光标位于最内层的括号上或最内层的括号内，那么 `d2a(` 将会删除从最内层开始的两对括号，以及他们之间的所有内容。其实，`d2a(` 这个操作等同于 `2da(`。在 Vim 的命令中，如果有两处都可以接收数字作为参数，那么最终结果就等同于两个数字相乘。在这里，`d` 与 `a(` 都是可以接收参数的，一个参数是 1，另一个是 2，我们可以把它们相乘然后放到最前面。

请参阅 `:h text-objects` 来获取更多关于文本对象的帮助。

## 自动命令

在特定的情况下，Vim 会传出事件。如果你想针对这些事件执行回调方法，那么就需要用到自动命令这个功能。

如果没有了自动命令，那你基本上是用不了 Vim 的。自动命令一直都在执行，只是很多时候你没有注意到。不信的话，可以执行命令 `:au` ，不要被结果吓到，这些是当前有效的所有自动命令。

请使用 `:h {event}` 来查看 Vim 中所有事件的列表，你也可以参考 `:h autocmd-events-abc` 来获取关于事件的更多帮助。

一个很常用的例子，就是针对文件类型执行某些设置：

```vim
autocmd FileType ruby setlocal shiftwidth=2 softtabstop=2 comments-=:#
```

但是缓冲区是如何知道当前的文件中包含 Ruby 代码呢？这其实是另一个自动命令检测的到的，然后把文件类型设置成为 Ruby，这样就触发了上面的 `FileType` 事件。

在配置 vimrc 的时候，一般第一行加进去的就是 `filetype on`。这就意味着，Vim 启动时会读取 `filetype.vim` 文件，然后根据文件类型来触发相应的自动命令。

如果你勇于尝试，可以查看下 `:e $VIMRUNTIME/filetype.vim`，然后在输出中搜索 "Ruby"。这样，你就会发现其实 Vim 只是通过文件扩展名 `.rb` 判断某个文件是不是 Ruby 的。

**注意**：对于相同事件，如果有多个自动命令，那么自动命令会按照定义时的顺序执行。通过 `:au` 就可以查看它们的执行顺序。

```vim
au BufNewFile,BufRead *.rb,*.rbw setf ruby
```

`BufNewFile` 与 `BufRead` 事件是被写在 Vim 源文件中的。因此，每当你通过 `:e` 或者类似的命令打开文件，这两个事件都会触发。然后，就是读取 `filetype.vim` 文件来判断打开的文件类型。

简单来说，事件和自动命令在 Vim 中的应用十分广泛。而且，Vim 为我们留出了一些易用的接口，方便用户配置适合自己的事件驱动回调。

请参阅 `:h autocommand` 来获取更多帮助

## 变更历史，跳转历史

在 Vim 中，用户最近 100 次的文字改动都会被保存在**变更历史**中。如果在同一行有多个小改动，那么 Vim 会把它们合并成一个。尽管内容改动会合并，但作用的位置还是会只记录下最后一次改动的位置。

在你移动光标或跳转的时候，每一次的移动或跳转前的位置会被记录到**跳转历史**中。类似地，跳转历史也可以最多保存 100 条记录。对于每个窗口，跳转记录是独立的。但当你分离窗口时（比如使用 `:split` 命令），跳转历史会被复制过去。

Vim 中的跳转命令，包括 `'`、`` ` ``、`G`、`/`、`?`、`n`、`N`、`%`、`(`、`)`、`[[`、`]]`、`{`、`}`、`:s`、`:tag`、`L`、`M`、`H` 以及开始编辑一个新文件的命令。

| 列表 | 显示所有条目 | 跳转到上一个位置 | 跳转到下一个位置 |
| ---- | ------------ | ---------------- | ---------------- |
| 跳转历史 | `:jumps` | `[count]<c-o>` | `[count]<c-i>` |
| 变更历史 | `:changes` | `[count]g;` | `[count]g,` |

如果你执行第二列的命令显示所有条目，这时 Vim 会用 `>` 标记来为你指示当前位置。通常这个标记位于 1 的下方，也就代表最后一次的位置。

如果你希望关闭 Vim 之后还保留这些条目，请参阅 `:h viminfo-'` 来获取更多帮助。

**注意**：上面提到过，最后一次跳转前的位置也会记录在[标注](#标注)中，也可以通过连按 <kbd>\`\`</kbd> 或 <kbd>''</kbd> 跳转到那个位置

请参阅以下两个命令来获取更多帮助：

```vim
:h changelist
:h jumplist
```

## 内容变更历史记录

Vim 会记录文本改变之前的状态。因此，你可以使用「撤销」操作 <kbd>u</kbd> 来取消更改，也可以通过「重做」操作 <kbd>Ctrl + r</kbd> 来恢复更改。

值得注意的是，Vim 采用 [tree](https://en.wikipedia.org/wiki/Tree_(data_structure)) 数据结构来存储内容变更的历史记录，而不是采用 [queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))。你的每次改动都会成为存储为树的节点。而且，除了第一次改动（根节点），之后的每次改动都可以找到一个对应的父节点。每一个节点都会记录改动的内容和时间。其中，「分支」代表从任一节点到根节点的路径。当你进行了撤销操作，然后又输入了新的内容，这时候就相当于创建了分支。这个原理和 git 中的 branch（分支）十分类似。

考虑以下这一系列按键操作：

```vim
ifoo<esc>
obar<esc>
obaz<esc>
u
oquux<exc>
```

那么现在，Vim 中会显示三行文本，分别是 "foo"、"bar" 和 "quux"。这时候，存储的树形结构如下：

```
     foo(1)
       /
    bar(2)
   /      \
baz(3)   quux(4)
```

这个树形结构共包含四次改动，括号中的数字就代表时间顺序。

现在，我们有两种方式遍历这个树结构。一种叫「按分支遍历」，一种叫「按时间遍历」。

撤销 <kbd>u</kbd> 与重做 <kbd>Ctrl + r</kbd> 操作是按分支遍历。对于上面的例子，现在我们有三行字符。这时候按 <kbd>u</kbd> 会回退到 "bar" 节点，如果再按一次 <kbd>u</kbd> 则会回退到 "foo" 节点。这时，如果我们按下 <kbd>Ctrl + r</kbd> 就会前进至 "bar" 节点，再按一次就回前进至 "quux" 节点。在这种方式下，我们无法访问到兄弟节点（即 "baz" 节点）。

与之对应的是按时间遍历，对应的按键是 `g-` 和 `g+`。对于上面的例子，按下 `g-` 会首先回退到 "baz" 节点。再次按下 `g-` 会回退到 "bar" 节点。

| 命令/按键 | 执行效果 |
| --------- | -------- |
| `[count]u` 或 `:undo [count]` | 回退到 `[count]` 次改动之前 |
| `[count]<c-r>` 或 `:redo [count]` | 重做 `[count]` 次改动 |
| `U` | 回退至最新的改动 |
| `[count]g-` 或 `:earlier [count]?` | 根据时间回退到 `[count]` 次改动之前。"?" 为 "s"、"m"、"h"、"d" 或 "f"之一。例如，`:earlier 2d` 会回退到两天之前。`:earlier 1f` 则会回退到最近一次文件保存时的内容 |
| `[count]g+` 或 `:later [count]?` | 类似 `g-`，但方向相反 |

内容变更记录会储存在内存中，当 Vim 退出时就会清空。如果需要持久化存储内容变更记录，请参阅[备份文件，交换文件，撤销文件以及viminfo文件的处理](#备份文件交换文件撤销文件以及viminfo文件的处理)章节的内容。

如果你觉得这一部分的内容难以理解，请参阅 [undotree](https://github.com/mbbill/undotree)，这是一个可视化管理内容变更历史记录的插件。类似的还有 [vim-mundo](https://github.com/simnalamburt/vim-mundo)。

请参阅以下链接获取更多帮助：

```vim
:h undo.txt
:h usr_32
```

## 全局位置信息表，局部位置信息表

在某一个动作返回一系列「位置」的时候，我们可以利用「全局位置信息表」和「局部位置信息表」来存储这些位置信息，方便以后跳转回对应的位置。每一个存储的位置包括文件名、行号和列号。

比如，编译代码是出现错误，这时候我们就可以把错误的位置直接显示在全局位置信息表，或者通过外部抓取工具使位置显示在局部位置信息表中。

尽管我们也可以把这些信息显示到一个空格缓冲区中，但用这两个信息表显示的好处在于接口调用很方便，而且也便于浏览输出。

Vim 中，全局位置信息表只能有一个，但每一个窗口都可以有自己的局部位置信息表。这两个信息表的外观看上去很类似，但在操作上会稍有不同。

以下为两者的操作比较：

| 动作 | 全局位置信息表 | 局部位置信息表 |
| ---- | -------------- | -------------- |
| 打开窗口 | `:copen` | `:lopen` |
| 关闭窗口 | `:cclose` | `:lclose` |
| 下一个条目 | `:cnext` | `:lnext` |
| 上一个条目 | `:cprevious` | `:lprevious` |
| 第一个条目 | `:cfirst` | `:lfirst` |
| 最后一个条目 | `:clast` | `:llast` |

请参阅 `:h :cc` 以及底下的内容，来获取更多命令的帮助。

**应用实例**：
如果我们想用 `grep` 递归地在当前文件夹中寻找某个关键词，然后把输出结果放到全局位置信息表中，只需要这样：

```vim
:let &grepprg = 'grep -Rn $* .'
:grep! foo
<grep output - hit enter>
:copen
```

执行了上面的代码，你就能看到所有包含字符串 "foo" 的文件名以及匹配到的相关字段都会显示在全局位置信息表中。

## 宏

你可以在 Vim 中录制一系列按键，并把他们存储到[寄存器](#寄存器)中。对于一些需要临时使用多次的一系列操作，把它们作为宏保存起来会显著地提升效率。对于一些复杂的操作，建议使用 Vim 脚本来实现。

- 首先，按下 <kbd>q</kbd>，然后按下你想要保存的寄存器，任何小写字母都可以。比如我们来把它保存到 `q` 这个寄存器中。按下 `qq`，你会发现命令行里已经显示了 "recording @q"。
- 如果你已经录制完成，那么只需要再按一次 <kbd>q</kbd> 就可以结束录制。
- 如果你想调用刚才录制的宏，只需要 `[count]@q`
- 如果你想调用上一次使用的宏，只需要 `[count]@@`

**实例1**：

一个插入字符串 "abc" 后换行的宏，重复调用十次：

```vim
qq
iabc<cr><esc>
q
10@q
```

（对于上面这个功能，你同样可以通过如下的按键： <kbd>o</kbd><kbd>a</kbd><kbd>b</kbd><kbd>c</kbd> 然后 <kbd>ESC</kbd> 然后 <kbd>1</kbd><kbd>0</kbd><kbd>.</kbd> 来实现）。

**实例2**：

一个在每行前都加上行号的宏。从第一行开始，行号为 1，后面依次递增。我们可以通过 <kbd>Ctrl</kbd> + <kbd>a</kbd> 来实现递增的行号，在定义宏的时候，它会显示成 `^A`。

```vim
qq
0yf jP0^A
q
1000 @q
```

这里能实现功能，是因为我们假定了文件最多只有 1000 行。但更好的方式是使用「递归」宏，它会一直执行，知道不能执行为止：

```vim
qq
0yf jP0^A@q
q
@q
```

（对于上面这个插入行号的功能，如果你不愿意使用宏，同样可以通过这段按键操作来实现：`:%s/^/\=line('.') . '. '`）。

这里向大家展示了如何不用宏来达到相应的效果，但要注意，这些不用宏的实现方式只适用于这些简单的示例。对于一些比较复杂的自动化操作，你确实应该考虑使用宏。

请参阅以下文档获取更多帮助：

```vim
:h recording
:h 'lazyredraw'
```

## 颜色主题

颜色主题可以把你的 Vim 变得更漂亮。Vim 是由多个组件构成的，我们可以给每一个组件都设置不同的文字颜色、背景颜色以及文字加粗等等。比如，我们可以通过这个命令来设置背景颜色：

```vim
:highlight Normal ctermbg=1 guibg=red
```

执行后你会发现，现在背景颜色变成红色了。请参阅 `:h :highlight` 来获取更多帮助。

其实，颜色主题就是一系列的 `:highlight` 命令的集合。

事实上，大部分颜色主题都包含两套配置。一套适用于例如 xterm 和 iTerm 这样的终端环境（使用前缀 `cterm`），另一套适用于例如 gvim 和 MacVim 的图形界面环境（使用前缀 `gui`）。对于上面的例子，`ctermbg` 就是针对终端环境的，而 `guibg` 就是针对图形界面环境的。

如果你下载了一个颜色主题，并且在终端环境中打开了 Vim，然后发现显示的颜色与主题截图中差别很大，那很可能是配置文件只设置了图形界面环境的颜色。反之同理，如果你使用的是图形界面环境，发现显示颜色有问题，那就很可能是配置文件只设置了终端环境的颜色。

第二种情况（图形界面环境的显示问题）其实不难解决。如果你使用的是 Neovim 或者 Vim 7.4.1830 的后续版本，可以通过打开[真彩色](https://zh.wikipedia.org/wiki/真彩色)设置来解决显示问题。这就可以让终端环境的 Vim 使用 GUI 的颜色定义，但首先，你要确认一下你的终端环境和环境内的组件（比如 tmux）是否都支持真彩色。可以看一下[这篇文档](https://gist.github.com/XVilka/8346728)，描述的十分详细。

请参阅以下文档或链接来获取更多帮助：

- `:h 'termguicolors'`
- [主题列表](#主题列表)
- [自定义主题中的颜色](#自定义主题中的颜色)

## 折叠

每一部分文字（或者代码）都会有特定的结构。对于存在结构的文字和代码，也就意味着它们可以按照一定的逻辑分割成不同区域。Vim 中的折叠功能，就是按照特定的逻辑把文字和代码折叠成一行，并显示一些简短的描述。折叠功能涉及到很多操作，而且折叠功能可以嵌套使用。

在 Vim 中，有以下 6 中折叠类型：

| 折叠方式 | 概述 |
| -------- | ---- |
| diff | 在「比较窗口」中折叠未改变的文本 |
| expr | 使用 `'foldexpr'` 来创建新的折叠逻辑 |
| indent | 基于缩进折叠 |
| manual | 使用 `zf`、`zF` 或 `:fold` 来自定义折叠 |
| marker | 根据特定的文本标记折叠（通常用于代码注释） |
| syntax | 根据语法折叠，比如折叠 `if` 代码块 |

**注意**：折叠功能可能会显著地影响性能。如果你在使用折叠功能的时候出现了打字卡顿之类的问题，请考虑使用 [FastFold 插件](https://github.com/Konfekt/FastFold)。这个插件可以让 Vim 按需更新折叠内容，而不是一直调用。

请参阅以下文档获取更多帮助：

```vim
:h usr_28
:h folds
```

## 会话

如果你保存了当前的「视图」（请参阅 `:h :mkview`），那么当前窗口、配置和按键映射都会被保存下来（请参阅 `:h :loadview`）。

「会话」就是存储所有窗口的相关设置，以及全局设置。简单来说，就是给当前的 Vim 运行实例拍个照，然后把相关信息存储到会话文件中。存储之后的改动就不会在会话文件中显示，你只需要在改动后更新一下会话文件就可以了。

你可以把当前工作的「项目」存储起来，然后可以在不同的「项目」之间切换。

现在就来试试吧。打开几个窗口和标签，然后执行 `:mksession Foo.vim`。如果你没有指定文件名，那就会默认保存为 `Session.vim`。这个文件会保存在当前的目录下，你可以通过 `:pwd` 来显示当前路径。重启 Vim 之后，你只需要执行 `:source Foo.vim`，就可以恢复刚才的会话了。所有的缓冲区、窗口布局、按键映射以及工作路径都会恢复到保存时的状态。

其实 Vim 的会话文件就只是 Vim 命令的集合。你可以通过命令 `:vs Foo.vim` 来看看会话文件中究竟有什么。

你可以决定 Vim 会话中究竟要保存哪些配置，只需要设置一下 `'sessionoptions'` 就可以了。

为了方便开发，Vim 把最后一次调用或写入的会话赋值给了一个内部变量 `v:this_session`。

请参阅以下文档来获取更多帮助：

```vim
:h Session
:h 'sessionoptions'
:h v:this_session
```

## 局部化

以上提到的很多概念，都有一个局部化（非全局）的版本：

| 全局 | 局部 | 作用域 | 帮助文档 |
| ---- | ---- | ------ | -------- |
| `:set` | `:setlocal` | 缓冲区或窗口 | `:h local-options` |
| `:map` | `:map <buffer>` | 缓冲区 | `:h :map-local` |
| `:autocmd` | `:autocmd * <buffer>` | 缓冲区 | `:h autocmd-buflocal` |
| `:cd` | `:lcd` | 窗口 | `:h :lcd` |
| `:<leader>` | `:<localleader>` | 缓冲区 | `:h maploacalleader` |

变量也有不同的作用域，详细内容请参考 [Vim scripting 的文档](http://vimdoc.sourceforge.net/htmldoc/usr_41.html)。

# 用法
## 获取离线帮助
## 获取离线帮助(备选)
## 获取在线帮助
## 执行自动命令
### 用户自定义事件
### 内部自带事件
## 剪贴板
## 剪贴板使用 (Windows, OSX)
## 剪贴板使用 (Linux, BSD, ...)
## 打开文件时恢复光标位置
## 备份文件，交换文件，撤销文件以及 viminfo 文件的处理
## 编辑远程文件
## 插件管理
## 片段插入
## 使用外部程序和过滤器
## MatchIt

# 技巧
## 聪明的使用 n 和 N
## 聪明的使用命令行历史
## 智能 Ctrl-l
## 禁用错误报警声音和图标
## 快速移动当前行
## 快速添加空行
## 快速编辑自定义宏
## 快速跳转到源(头)文件
## 在 GUI 中快速改变字体大小
## 根据模式改变光标类型
## 防止水平滑动的时候失去选择
## 重新载入保存文件
## 智能当前行
## 更快的关键字补全

# 命令
## :global - 在所有匹配行执行命令
## :normal and :execute - 脚本梦之队
## :redir - 重定向消息

# 调试
## 常规建议
## 查看启动日志
## 查看运行时日志
## 调整日志等级
## vim 脚本调试
## 语法文件调试

# 杂项
## 附加资源
## Vim 配置集合
## 内置插件
## 将 Control 映射到 CapsLock
## 复活节彩蛋
## 为何使用 hjkl

# 怪癖
## 编辑小文件很慢
## 编辑大文件很慢
## 新行用于 NUL
## 相同部分粘贴 (要不为什么我总要设置‘粘贴’?)
## 在终端使用 Esc 延时
## 无法重复函数中执行的搜索
## 主题列表

# 插件列表

# Neovim

## 加入我们

可以协助我们核对翻译，或者从[章节列表](CONTRIBUTING.md)中认领章节进行翻译。

## 致谢：

- [Linux 中国翻译组](https://github.com/LCTT)
- [掘金翻译计划](https://github.com/xitu/gold-miner)
