# [第一章：介绍与安装](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_introduction_and_installation)

这本书是为那些被模态编辑强大功能所吸引，却因为即便是入门教程中也充斥着大量配置内容而感到望而生畏或索然无味的开发者们所写。

我猜你可能是一位 Visual Studio Code 用户（这确实是一个很棒的编辑器，我也用过几年），当然你也可能是从其他各种集成开发环境和代码编辑器转向模态编辑的。你可能听说过 Vim，现在想要尝试一下。

## [1.1. 为什么选择 Vim](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_why_vim)

Vim 有着非常悠久的历史。它创建于90年代早期，是对（更加）古老的 Vi 编辑器（创建于70年代）的改进。"Vim" 这个名字实际上是 "Vi, improved"（Vi的改进版）的缩写。而它的前身 Vi，则是 "Visual"（可视化）的简称，因为它是对更早期（1971年）的一个名为 ed 的非可视化行编辑器的改进。

> 有趣的是，ed 这个编辑器在现代 Unix 系统中仍然可用。如果你使用 MacOS 或 Linux 环境，你很可能可以在任何终端中输入 ed 来访问它。（如果你不小心尝试了的话，按 Control-D 可以退出）。现在你对 ed 的了解和我一样多了，相信我，你也不会想知道更多了。

你可能还熟悉 ed 的另一个分支版本：sed（流编辑器）。直到今天，它仍然被用于在 shell 管道中修改文本。

ed 命令还被扩展出了另一个行编辑器，叫做 ex，这个编辑器现在基本不再单独使用了，但它作为 Vim 的一个子模式被（广泛地）使用着。事实上，如果你安装了 Neovim 并在命令行中输入 ex，你会得到一个功能非常受限的 Neovim 实例，它只支持 ex 命令。

这确实是一个相当复杂的家族树，但仅凭血统并不能很好地预示质量，正如任何第四代显贵都能证明的那样。

使用任何一个编辑器都有很多原因，但对于 Vim 来说，以下几点尤为突出：

**健康效益**
这对我来说是最重要的一点。在我职业生涯早期，我大量使用 Vim，不过和许多开发者一样，在 2015 年 VS Code 发布后就转向了它。我在键盘前花费了大量时间，到了 2020 年，我被重复性劳损（RSI）折磨得如此严重，以至于我花了六个月的时间完全靠语音编程（一篇关于这个话题的博客文章让我获得了超出预期的关注）。一个朋友建议我重新转向模态编辑，这对我来说产生了巨大的改变。绝大多数 Vim 按键操作不需要用同一只手同时按住多个键，这极大地减轻了腕管综合症的困扰。

**性能表现**
大多数 IDE 都有某种"vi 模拟"层或插件，让你可以在不完全切换到新编辑器的情况下获得一些模态编辑的健康效益。但是等待 VS Code 启动并加载所有你熟悉和喜爱的扩展已经成为许多人的一种冥想练习（或者是重返社交媒体刷屏的机会）。相比之下，当我加载我的 LazyVim 配置时，它会很贴心地告诉我加载所需的时间：56.98 毫秒。对于我这个反应迟钝的人类来说，这简直是瞬间完成。

**开发效率**
这是一个有争议且主观的话题。工具的好坏取决于使用者的水平，我当然知道有一些优秀的程序员能够熟练运用他们的 VS Code、Emacs 或 JetBrains 配置。尽管如此，我真的相信一个精心调教的 Vim 配置可以超越它们所有。

**开放生态系统**
自从 Nadella 掌舵以来，我非常敬佩微软对开源软件的态度，但 VS Code 正在显示出越来越多的专有锁定迹象（尤其是在其 AI 集成方面）。相比之下，Neovim 生态系统是一个充满活力的开放社区，每周都会出现一些在 VS Code 中永远不会尝试的创新插件。

## [1.2. 为什么特别选择 Neovim](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_why_neovim_specifically)

如果你决定使用 Vim，你很快就会发现有两个现代变体：Vim 和 Neovim。它们都是 90 年代原始开源 Vim 代码的直系后裔。Neovim 于 2014 年从 Vim 分支出来，其愿景是重构并现代化其代码库和功能集。

这两者都在积极维护中，且都有潜力让人感觉精致现代，尽管要实现这种潜力需要一些配置。它们各自都拥有非常强大的插件生态系统，但 Neovim 有一个杀手级特性：除了其兄弟版本使用的原生 VimScript 外，它还引入了 Lua 编程语言用于插件开发（和配置）。

仅就 Lua 本身而言，并不会使 Neovim 本质上比 Vim 更好。然而，虽然大多数 Vim 插件也能在 Neovim 上运行，但反过来却并不总是如此，而且有一些同类最佳的 Lua 插件只能在 Neovim 上运行。

就本书而言，你的选择已经替你做好了：本书所讲的 LazyVim 发行版只能在 Neovim 上运行。

## [1.3. LazyVim 简介](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_introducing_lazyvim)

Vim 和 Neovim 的主要缺点是，虽然它们有能力提供与任何其他 IDE 相同（或更好）的现代编辑体验，但它们的初始状态并非如此。Vim 一直保持着与过时的 vi 工具的兼容传统，而 Neovim 也只是略微偏离了这一传统。当你首次安装 Neovim 时，你得到的是一个相当朴素的代码编辑体验。

2020 年当我从习惯了 VS Code 带来的出色功能后重新转向 Vim 时，我花了两周时间才让配置达到我想要的状态，之后的几个月里我还在不断调整。最终的配置包含了大约 300 行 Vimscript，后来我将其移植为约 250 行 Lua 代码。说实话，我一向热衷于定制，我的 VS Code 配置实际上比这两者都要长！但我也得承认，VS Code 的开箱即用体验确实要好得多。

我研究了几个所谓的 Neovim "发行版"（预配置安装包）。我不会详细比较，但 LazyVim 是目前最出色的赢家，主要是因为它在开箱即用的简单体验和相对容易的定制配置之间取得了平衡。

需要明确的是，LazyVim 就是 Vim。编辑体验是完全一致的。它不像 Neovim 那样是 Vim 的新迭代或版本。相反，LazyVim 是一种理念；它始于对现代开发最佳插件配置的共识，以及让这些插件能够很好地协同工作的配置（让不同插件的键位绑定不相互冲突是手动管理编辑器配置时的主要痛点之一）。

但如果你在使用 LazyVim 时抱着这样的心态：这种体验将比你之前使用过的任何编辑体验都要好，并且接受你需要重新训练一些键盘肌肉记忆，你会发现它的设计非常周到。根据我的经验，这正是 2020 年代模态编辑体验应有的样子。

## [1.4. 选择终端](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_choosing_a_terminal)

如果你已经看到这里，你可能觉得已经准备好安装 Neovim 了。实际上，你还有一个决定要做。

Neovim 可以在许多不同的环境中运行（你甚至可以在 Visual Studio Code 内运行它！）默认情况下它是一个终端程序，但也有大量的图形界面（GUI）可用。我几乎尝试过所有这些界面，老实说，我认为它们相比于直接在终端中运行 Neovim 并没有任何本质上的优势。

我们将在本书后面简要讨论如何将 Neovim 连接到几个 GUI，但对于入门来说，我建议在终端中运行 Neovim。具体来说，是一个非常好的终端。

要获得最佳的 Vim 编辑体验，你需要一个 GPU 加速的终端。这是什么意思？基本上就是你将使用设计用于渲染照片级真实视频的芯片来渲染源代码。这听起来就像用它来做人工智能一样合理，对吧？

你需要自行研究以下选项，所以可以请教你喜欢的搜索引擎或当下流行的 AI 聊天机器人来帮你决定：

**Kitty Terminal**
这是我个人的首选。我发现它文档完善、配置简单且功能齐全。

**Alacritty**
可能是原始速度方面的赢家，但配置比较笨拙，功能也较少。

**Wezterm**
有一些非常巧妙的功能，但我发现文档不够完善，而且在使某些功能正常工作时遇到了困难。

**Windows Terminal**
如果你是 Windows 用户，它确实声称支持 GPU 加速，不过我发现 Neovim 在其中偶尔会出现无响应的情况。

**Warp Terminal**
如果你已经是 Warp 的用户而且离不开它，Neovim 也可以在其中运行。我发现使用体验有点卡顿，而且我不太喜欢 Warp 的外观和感觉（以及需要登录才能使用的事实）。

所以安装其中的一个或多个，直到你找到一个你喜欢的。如果你愿意，你也可以使用其他终端模拟器。你可能甚至不会注意到体验有什么不足，但我可以保证，如果你之后切换到 GPU 加速的体验，你会注意到这种改进。

## [1.5. 设置终端字体](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_setting_up_your_terminal_font)

LazyVim 及其插件在终端中看起来非常漂亮，你几乎不会相信它们不是 GUI 应用程序。为了实现这一点，它们依赖于包含大量编程相关字形的特殊字体。最显著的是，这让你可以看到代表你打开的文件类型的图标，同时还能在终端中提供漂亮的边框和类似窗口的行为。

要获得最佳的 LazyVim 体验，你需要安装这些特殊字体中的一个，并配置你的终端来使用它。实际上，即使你不是重度 Neovim 用户，你也应该在终端中使用这些字体。许多现代终端应用（这说法听起来有点怪，是吧？）在安装了这些字体后都会看起来更好。

访问 Nerd Fonts 网站以获取更多信息。如果你使用 Kitty，你只需要安装 NerdFontsSymbolsOnly 字体，如果在你配置的等宽字体中找不到某些符号，它会自动从该字体中提取符号。对于其他终端，你可能需要按照 Nerd Fonts 网站上讨论的那样安装和配置一个"打补丁的"字体。有很多选择可供选择。

你可以从许多最流行的编程字体中进行选择。下载和安装它们在很大程度上取决于操作系统，所以我就让 Nerd Fonts 网站上的指南来为你解释这个过程。

## [1.6. 安装 Neovim](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_install_neovim)

Neovim 几乎可以在任何能安装软件的地方运行，它只依赖标准的系统依赖项。主要的问题是，无论你使用哪种操作系统，你都有太多的选择！

你可以访问 Neovim 主页并点击"Install Now"按钮，从 Neovim 开发者那里获取针对你所选择（或不得不使用）的操作系统的最新安装说明。

### [1.6.1. 我应该安装哪个版本？](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_which_version_should_i_install)

与其发布周期相比，Neovim 的开发进度非常快，所以人们经常使用最新的每日构建版本。我很少在从 Github 主分支构建的版本中遇到 bug，所以通常来说是安全的。我通常在新的稳定版本发布时使用它，然后当某个插件更新说"如果你使用 Neovim 每日构建版本，这里有个很酷的新功能"时，我就会改为安装最新的 Neovim 构建版本。

我建议现在先从最新的稳定版 Neovim 开始，在写作本文时是 0.10.0 版本。如果可能的话，避免使用更老的版本。LazyVim 确实倾向于添加来自每日发布版本的功能，所以如果你开始像我一样对这个发行版感到兴奋，切换到预发布版本将是一个很自然的进展。

### [1.6.2. Windows](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_windows)

在 Windows 上，我建议使用 Windows Subsystem for Linux（WSL）并在其中进行所有开发。WSL 远超出了本书的范围，但微软和许多在线教程都对其有很好的文档说明。一旦你选择了一个兼容 WSL 的 Linux 发行版，设置好并在你选择的终端中运行它，你就可以使用下面的 Linux 安装说明来安装 Neovim。

如果你有理由或偏好在原生 Windows 上开发，最简单的方法是从 GitHub 上 neovim/neovim 仓库的 Releases 部分获取 MSI 安装程序。

如果你已经在使用 Winget、Chocolatey 或 Scoop 来管理你的 Windows 机器上的包，它们各自都有 Neovim 包。

请注意，如果你使用 Windows 而不使用 WSL，你还需要安装一个 C 编译器才能获得 treesitter 支持（这基本上意味着更好的语法高亮和代码导航支持）。遗憾的是，这不是一个简单的任务。这在 nvim-treesitter/nvim-treesitter GitHub 仓库中有文档说明，所以我在这里不会详细介绍。

### [1.6.3. MacOS](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_macos)

在 MacOS 上，大多数开发者都使用 Homebrew，所以如果你还没有安装它，我建议按照 brew.sh 上的说明进行安装。

一旦你安装并运行了 brew，使用命令 brew install neovim 就可以安装 Neovim。

如果你想追求最新特性，brew install --HEAD neovim 将安装最新的 Neovim 每日构建版本，这个版本可能是稳定的，但不能保证。

我发现相比其他 MacOS 上安装 Neovim 的选项，brew 的体验要友好得多，所以如果你还不是 Homebrew 用户，我强烈建议设置它。随着我们在 LazyVim 的旅程中深入，你会想要安装其他开源工具，而 brew 将是获取所有这些工具最简单的方式。

如果你不想使用 Homebrew，事情就会有点烦人。Neovim 开发团队并不维护 MacOS 安装程序，所以你必须下载一个 tarball 并解压它，然后从系统路径中的某个位置链接到二进制文件。如果你不知道这些是什么意思，说实话，还是用 Homebrew 吧，它更简单！

### [1.6.4. Linux](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_linux)

如果在你的发行版的默认包管理器中找不到 Neovim，那你用的确实是一个非常特别的 Linux 发行版！

所以只需运行 sudo pacman -S neovim、sudo apt install neovim、sudo dnf install neovim，或者使用你偏好的其他特殊包管理器的相应命令即可。

不过，一些发行版附带的 Neovim 版本可能非常过时。如果你想要每日构建版本，你可以在 neovim/neovim GitHub Releases 页面找到相关说明，或者需要深入研究你的发行版的文档。

在不太可能出现的情况下，如果你的 Linux 发行版没有自带 C 编译器，你还需要安装一个。对于大多数发行版来说，只需安装 gcc 包就可以了。

## [1.7. 尝试原始的 Neovim（如果你敢的话）](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_try_neovim_raw_if_you_dare)

安装完 Neovim 后，你可以通过在之前几节安装的终端中简单地输入 nvim（或者 nvim <文件名> 来打开特定文件）来尝试使用它。如果 Neovim 安装正确并且在你的系统路径中，你会看到一个视觉上不太吸引人的编辑器，看起来就像是从 90 年代的某个程序分叉出来的，而且刻意让它看起来像是 70 年代写的。

所以，至少它很诚实？

不幸的是，你现在被困住了。为了省去你疯狂地在 Google 上搜索"如何退出 Vim"，这里告诉你退出的命令是：先按 Escape，然后输入三个字符 :q!，最后按 Enter。因此，整个操作序列是 <Escape> <冒号> q <感叹号> <Enter>。

说真的，"如何退出 Vim"是 Google 上"如何退出..."这个搜索词的前三个自动补全之一。显然只有三星电视和 MacOS 的全屏模式比它更难退出！在我们深入了解 vim 的思维模型和命令模式后，我们就会明白为什么这个咒语是有效的。

> 如果你想的话，可以运行命令 <Escape>:Tutor<Enter> （如果失败的话，可以在终端使用命令：vimtutor）来打开一个交互式文本文件，你可以在学习 Neovim 基础知识的同时阅读和编辑它。我确实建议你在某个时候完成这个教程，但现在可能不是最佳时机。在 Vim 教程中很多"正常"的操作在使用 LazyVim 时都是不同的（而且更好！）。本书的其余部分并不假设你已经完成了这个教程。

## [1.8. 安装 LazyVim](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_install_lazyvim)

现在你已经安装并运行了 Neovim，让我们来配置它，让它看起来像是这个世纪开发的产品。

安装 LazyVim 需要使用一些 git 操作。既然你在阅读这本书，我假设你是一名软件开发者，因此对 git 有一定的了解。

在不同的操作系统上安装 LazyVim 的 git 命令基本相同，只是路径和环境变量略有不同。

### [1.8.1. 从零开始](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_start_with_a_clean_slate)

> 如果你已经有了 Neovim 配置，并且想在不丢失现有配置的情况下尝试 LazyVim，可以设置环境变量 NVIM_APPNAME=lazyvim。直接跳到下面的"克隆启动模板"部分，然后克隆到 ~/.config/lazyvim 目录而不是 ~/.config/nvim。如果你想让这些更改永久生效，可以在你的 shell 启动文件中设置 NVIM_APPNAME，或者将 lazyvim 配置文件夹重命名为 nvim。

首先，删除或备份所有现有的 Neovim 状态。如果你以前从未使用过 Neovim，这一步基本上是可选的，但我建议确保以下目录已被删除或移动：

**清理：适用于 WSL 的 Windows、MacOS 和 Linux**
删除或备份（使用 mv 而不是 rm）以下目录：

```bash
$ rm -rf ~/.config/nvim
$ rm -rf ~/.local/share/nvim
$ rm -rf ~/.local/state/nvim
$ rm -rf ~/.cache/nvim
```

**清理：不使用 WSL 的 Windows**
在 Windows 上，配置和数据文件夹的位置与 Unix 系统略有不同，但基本思路是一样的。只需使用 Powershell 命令替代 Unix 核心工具：

```bash
$ Move-Item $env:LOCALAPPDATA\nvim $env:LOCALAPPDATA\nvim.bak
$ Move-Item $env:LOCALAPPDATA\nvim-data $env:LOCALAPPDATA\nvim-data.bak
```

### [1.8.2. 安装其他推荐的依赖项](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_install_other_recommended_dependencies)

我强烈建议安装 lazygit、ripgrep 和 fd，LazyVim 使用这些工具来提供增强的 git、字符串搜索和文件搜索功能。大多数操作系统的包管理器都可以轻松安装这些工具。你可以在它们各自的 GitHub 仓库中找到更具体的安装说明：

- [jesseduffield/lazygit](https://github.com/jesseduffield/lazygit)
- [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)
- [sharkdp/fd](https://github.com/sharkdp/fd)

### [1.8.3. 克隆 LazyVim 启动模板](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_clone_the_lazyvim_starter_template)

你将使用 git clone 命令下载启动模板并将其复制到 Neovim 的用户配置目录中，然后删除 .git 文件夹。

这个启动模板就是字面意思：一个起点。所以你永远不需要从这个仓库拉取更改。相反，LazyVim 会自己管理自身和所有插件的更新。启动模板之所以是一个 git 仓库，仅仅是因为这样对 LazyVim 维护者来说更容易维护。从你的角度来看，你只是在下载仓库的当前状态，不需要知道它的过去或未来状态。

**克隆启动仓库：WSL、MacOS 和 Linux**
在 Unix 系统上，使用以下命令：

```bash
$ git clone https://github.com/LazyVim/starter ~/.config/nvim
$ rm -rf ~/.config/nvim/.git
```

**克隆启动仓库：不使用 WSL 的 Windows**
在原生 Windows 上，使用以下命令：

```bash
$ git clone https://github.com/LazyVim/starter $env:LOCALAPPDATA\nvim
$ Remove-Item $env:LOCALAPPDATA\nvim\.git -Recurse -Force
```

## [1.9. 仪表盘（Dashboard）](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_the_dashboard)

好了，你已经完成了本书最困难的部分，现在终于可以开始使用 LazyVim 了！使用与之前相同的终端命令：nvim。

当 LazyVim 设置一切并下载它认为必要的插件时，你会看到一连串的活动。你可能会看到它编译和安装一堆 treesitter 语法解析器；如果你看到"Show More"（显示更多）的消息，可以使用 G（即 Shift+g）跳到末尾。

一旦所有内容都安装完成，你会在一个由 Lazy.nvim 插件管理的窗口中看到已安装插件的摘要，我们稍后会讨论这个插件。现在，当你看到 Lazy.nvim 界面时，可以按 q 键。插件会将其解释为"退出 Lazy.nvim"，窗口就会关闭。

现在你可以看到 LazyVim 的仪表盘，这是你每次启动 LazyVim 时首先看到的界面。比起开箱即用的 Neovim 体验，这个界面要友好得多：

<img src="mymedia\dashboard-dark.png" alt="dashboard dark" style="zoom:50%;" />

如你所见，有几个命令可以通过单个按键与仪表盘进行交互。当然，最重要的是按 q 键退出！

这些选项大多是不言自明的，但我们会在后面的章节中深入讨论其中的一些选项。

## [1.10. Lazy.nvim 插件管理器](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_lazy_nvim_plugin_manager)

当你第一次打开 LazyVim 时，它会检查是否有可更新的插件，并在一个消息通知中给你一个概览，看起来会像这样：

<img src="mymedia\plugin-updates-dark.png" alt="plugin updates dark" style="zoom:50%;" />

由于 Neovim 默认非常基础，LazyVim 预装了大量实用的插件。而且这些插件很可能已经过时了，因为 Neovim 世界的插件开发速度快得惊人。

在很久以前，插件管理完全是手动过程。在不那么久远但仍然是过去的日子里，插件管理由各种插件来完成，但总感觉缺少些什么。

然后出现了名为 Lazy.nvim 的插件管理器，它是由后来创建 LazyVim 的同一个人开发的。虽然两者都由同一个人维护，但不要把 Lazy.nvim 插件管理器与 LazyVim 本身混淆。Lazy.nvim 严格来说只是一个插件管理器，而 LazyVim 是一个插件和配置的集合。Lazy.nvim 是其中的一个插件。

Lazy.nvim 有许多出色的功能，最显著的是只在需要时加载插件（因此名为"Lazy"），这使得你的编辑器启动速度非常快。它还有一个很好的用户界面来管理插件的安装和更新。

你可以在仪表盘中简单地按 l 键来访问这个界面，在仪表盘中标记为 Lazy。这个标签可能应该标记为 Lazy Plugin Manager 会更清楚一些，但现在你已经知道 Lazy 的含义了，所以不会忘记。

如果你没有主动显示仪表盘，你可以随时通过进入空格模式来显示插件管理器。我们将在下一章详细介绍空格模式，但现在：首先确保你处于普通模式，方法是检查活动窗口的左下角。如果不是，按 Esc 键进入普通模式。然后按空格键进入空格模式，再按 l 键调出 Lazy.nvim 插件管理器。

（别担心，这些按键绑定在一周之内就会成为你的第二天性。）

Lazy.nvim 插件管理器界面看起来是这样的：

<img src="mymedia\plugin-manager-dark.png" alt="plugin manager dark" style="zoom:50%;" />

弹出的这个窗口被称为浮动窗口。你会在不同的情况下看到这些窗口，通常是在需要处理交互数据时。这个特定的浮动窗口有它自己的一套按键绑定。这些按键绑定列在顶部，要注意它们都是大写的，所以在使用时需要按 Shift 键。

通常，我使用的唯一 Lazy.nvim 按键绑定是 S，用于同步（Sync）。这相当于在一个操作中同时运行安装（install）、清理（clean）和更新（update）。它确保实际安装的插件版本与 LazyVim 配置中指定的版本完全一致。

所以当"Plugin Updates"（插件更新）通知弹出时，只需按 Space-l，然后按 S，等待同步完成。之后按 q 关闭 Lazy.nvim 插件模式和浮动窗口，返回你之前的工作。

## [1.11. 关于管理点文件的说明](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_a_note_on_managing_dot_files)

如果你在多台不同的电脑上工作，你很快就会发现你不想在所有电脑上分别设置 LazyVim 配置。LazyVim 没有类似 VS Code 的"设置同步"功能，虽然存在这样的插件。

我推荐的替代方案是将你的配置文件存储在 git 仓库中。你可能会发现还有一些其他文件也想保存在那里，比如你的终端配置文件、.gitconfig 和 .zshrc / .bashrc / .config/fish/config.fish。

如果你使用 GitHub Codespaces，你可能已经用 git 管理了一些点文件。如果没有，我个人建议遵循 Atlassian 博客上那篇优秀的文章[《Dotfiles: Best way to store in a bare git repository》](https://www.atlassian.com/git/tutorials/dotfiles)（点文件：在裸 git 仓库中存储的最佳方式）中的建议。

在像 LazyVim 这样的发行版出现之前，人们很常见地将他们的 Vim 配置存储在公共仓库中，并相互借鉴想法。这种做法现在还没有完全消失，你可以在 GitHub 上的 [dusty-phillips/dotfiles](https://github.com/dusty-phillips/dotfiles) 仓库中找到我自己的点文件。

## [1.12. 总结](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/#_summary)

在本章中，我们简要讨论了 Vim、Neovim 和 LazyVim 的历史，以及它们为什么在今天仍然具有重要意义。然后我们介绍了 GPU 加速终端和 Nerd Fonts 的重要性。

我们弄清楚了如何在你使用的任何操作系统上安装 Neovim 及其依赖项，最后从其起始模板安装了 LazyVim。

在下一章中，我们将讨论 Vim 的核心特性：模态编辑，并深入探讨在 LazyVim 中用键盘可以做的许多事情。

# [第二章：什么是模态编辑？](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_what_is_modal_editing_anyway)

正如仪表盘上的字母所示，LazyVim 是以键盘为中心的编辑器。尽可能多的操作都可以在不需要在鼠标和键盘之间来回切换的情况下完成。当然，你仍然可以使用鼠标。你可以点击编辑器中的任何位置，与弹出的按钮和对话框进行交互，使用滚轮或触控板手势进行滚动，通过拖动边框来调整编辑器窗格的大小。但是，这些操作都可以使用键盘来完成，而且通常效率更高。

更重要的是，你可以通过最多按住两个键，甚至只需要一个键就能完成大多数操作。你很少需要将手指扭曲成痛苦（且危险）的姿势去按 Control + Shift + Alt + <某个键>。

Vim 是如何做到这一点的？答案是模式编辑（Modal editing）。

## [2.1. 模式编辑入门](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_introduction_to_modal_editing)

在 LazyVim 中，"模式"简单来说就是根据当前激活的模式，不同的按键会有不同的含义。例如，当你启动编辑器时，你处于"仪表盘模式"（Dashboard Mode），该模式下每个按键最常见的解释都直接列在仪表盘上。这种在特定模式下按键绑定的可发现性是 LazyVim 的一个普遍特点，相比原生 Neovim 不透明的默认行为来说是一个巨大的改进。

为了更好地理解这一点，按下空格键进入"空格模式"（Space mode）。空格模式是 LazyVim 特有的概念；它在原生 Neovim 安装中并不存在（不过如果你想在不使用 LazyVim 的情况下获得空格模式，你可以通过安装各种插件来重现这个效果）。

进入空格模式后，屏幕底部会弹出一个菜单。它看起来会像这样（我的菜单包含一些自定义设置，所以你的可能会有所不同）：

<img src="mymedia\space-mode-dark.png" alt="space-mode-dark" style="zoom:50%;" />

这是一个很大的菜单。现在我们需要关注的重点是 f 键，我们将用它来理解模式编辑。

如果你在仪表盘模式下按 f 键，会打开一个查找文件（Find file）对话框，这个对话框使用了我们稍后会讨论的选择器插件。但是，当你在空格模式下，按 f 键则会打开文件/查找（file/find）其空格模式的子菜单。

这就是模式编辑的核心含义：同一个按键的行为取决于当前的模式。正如空格模式菜单底部所示，你可以按 Escape 键退出空格模式并返回到仪表盘。现在就试试吧。

现在你回到了仪表盘模式，你可以按 n 键创建一个新的空白缓冲区（buffer）。

请特别注意缓冲区左下角，你会看到 INSERT 这个词：

<img src="mymedia\insert-mode-dark.png" alt="insert mode dark" style="zoom:50%;" />

还记得我说过空格模式是 LazyVim 特有的概念吗？插入模式（Insert mode）则是最初 Vi 编辑器的概念，后来的 Vim、Neovim，以及现在的 LazyVim 都继承了这一特性。在插入模式下，绝大多数按键的行为都和你在其他编辑器中的预期一样：它们会插入文本。所以你可以像平常一样正常打字。

在插入模式下，你可以使用 Control 和 Alt 键来访问一些快捷键。例如，你可以按 Control-r 进入"寄存器"（Registers）迷你模式，这会弹出一个你可以从中粘贴内容的"寄存器"列表。我们将在第 8 章详细介绍寄存器。现在，你只需要知道在插入模式下，按 Control-r 后跟加号键（即 Shift-=）将会从剪贴板中粘贴文本。

然而，对于任何非文本输入的操作（包括粘贴文本），你会更经常地切换到普通模式（Normal mode）来执行。普通模式是另一个主要的 Vim 模式，自 Vi 时代就存在了。

要从插入模式切换到普通模式，按 Escape 键。光标会从一条竖线变成一个方块，左下角的指示器也会变成蓝色的 NORMAL：

<img src="mymedia\normal-mode-dark.png" alt="normal mode dark" style="zoom:50%;" />

在普通模式下，按键的行为与插入模式完全不同。比如按 p 键，它不会在文档中输入字母 p，而是会从系统剪贴板中粘贴内容。

Vim 和 Neovim 的一些功能虽然不太容易发现，但它们的快捷键设计得很容易记忆。大多数情况下，执行某个操作的快捷键都会使用该操作相关的首字母。你可能会认为 p 代表"paste"（粘贴），但其实这个概念比剪贴板的概念要早得多。如果你觉得理解成"paste"更容易，那也没问题，但在 Vim 的术语中，它实际上代表"put"（放置），在本书中我们也会使用这个词。

来看个不同的例子：在插入模式下按 Control-r 会弹出寄存器列表，但在普通模式下却是执行"redo"（重做）操作。如果你想在普通模式下访问寄存器列表，需要按 "（引号，即 Shift-单引号）键。

如果这些听起来很混乱，也不用担心。你的大脑和肌肉记忆会比你想象的更快适应，你也始终会明白，普通模式下的行为与插入模式下的不同。

我很少在插入模式下使用非文本输入的命令，而是习惯先切换回普通模式再执行这些命令。这样做并不会增加太多按键次数，而且避免了同时按住多个键的麻烦。

从插入模式退出到普通模式，统一使用 Escape 键。这就带来一个重要问题：你会频繁使用这个键，但是每次都要把手从主行移动到左上角的 Escape 键再移回来，这样的操作效率其实不高。

对于这个问题，有几个常见的解决方案：

- 如果你使用的是可自定义的键盘，你可以把 Escape 键放在更方便按到的位置。这就是我的做法。我用的是 Kinesis Advantage 360 键盘，虽然这个键盘的设计看起来有点奇特，但我把 Escape 键重新映射到了"拇指区"，这样按起来就和 Enter、空格、退格键一样方便了。

- 你的操作系统一般都支持键盘重映射。很多使用模式编辑器的用户会把几乎用不到的 Capslock 键改成 Escape 键。（对于非模式编辑器的用户来说，可能会更喜欢把 Capslock 改成经常需要按住的 Control 键，特别是在笔记本键盘上）。

- Neovim 本身也支持键位重映射。我们稍后会在 LazyVim 部分详细讨论如何设置。一个常见的做法是把一些在输入文本时不太可能连续按到的组合键映射成 Escape 键。比如，你可以设置在插入模式下按 jk、jj 或 ;; 来切换到普通模式。我试过这种方法，但不太喜欢，因为当你按下第一个键时，Neovim 会等待看你是要输入命令还是继续输入文本，这个延迟让我觉得不太舒服，不过你可能会喜欢这种方式。

- 另外，Control-C 组合键也可以退出插入模式，这个是默认就有的，不需要额外设置。不过我个人不太喜欢这种方式，因为需要按两个键，而且在我用的 Dvorak 键盘上，按 Control-C 比在 qwerty 键盘上要难得多，毕竟在 qwerty 键盘上 C 键就在底排靠近 Control 键的位置。

现在暂时不用急着改键位设置，先试着习惯现有的 Escape 键位置，看看是否真的觉得不方便。

当你进入普通模式后，肯定还是要回到插入模式来输入文本的。有几种不同的方法可以做到这一点。下面介绍几个最常用的：

i 键可以在光标当前位置之前插入文本。这意味着你可以（虽然很笨拙）通过重复按 i <Escape> i <Escape> 来向左移动光标。当你按 i 键时，你可以在当前位置之前插入文本，然后按 Escape 退出插入模式，这时光标就会停在新的"之前"位置。

有时候，你可能想在光标当前位置之后进入插入模式。这时就要用 a 键了（记忆方法：i 代表 Insert Before（在前插入），a 代表 Append 或 After（在后添加））。

在浏览文档时，你会发现经常需要在这两种模式之间切换，因为我们后面要讲到的各种导航命令，有时会把光标放在你需要插入的位置之前，有时会放在之后。所以记住这两个命令都很重要。

还有两个非常常用的操作是在当前行的最开始或最末尾插入文本。虽然你可以先用导航命令移动到行首或行尾，然后再用 i 和 a，但直接用 I 和 A 命令会更方便（注意这两个是大写字母，需要按住 Shift 键）。

### [2.1.1. 关于按键助记的说明](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_a_note_on_keybinding_mnemonics)

这些相关的按键绑定通常会被分配给同一个字母的小写和大写版本。你会发现小写版本通常表示"做某事"，而大写版本要么表示"做同样的事情，但范围更大"，要么表示"做相反的事情"，具体取决于情况。在这里，i 和 a 表示"在光标前后插入一个字符"，而 I 和 A 则表示"在光标前后插入，但范围更大（即在行首或行尾）"。

举个"做相反的事情"的例子，看看 o 和（按住 Shift 的）O 键，这是另外两种进入插入模式的方式。

o 键用于在当前行下方创建新行并进入插入模式。对于"做相反的事情"的情况，大写的 O 表示"在当前行上方创建新行并进入插入模式"。

> 助记口诀"Open（打开）一个新行在上方/下方"可以帮你记住这个不太容易记住的 o 命令。

最后一个需要按两个键的有用命令是 gi。这是先按一下 g 再按一下 i。它的意思是"转到上次进入插入模式的位置，并再次进入插入模式"。在这种情况下，g 键实际上是切换到一个我称之为"Go To（转到）"的小模式，不过并非所有从这个模式可以访问的命令都严格与"转到"有关。你可以在普通模式下按 g 键，然后等待窗口底部弹出菜单，就能看到"Go To"模式下所有可用的命令列表：

<img src="mymedia\goto-mode-dark.png" alt="Go To Mode" style="zoom:50%;" />

我们稍后会介绍大部分命令，但请注意其中有 i 键，标注为"Move to the last insertion and INSERT（移动到最后插入的位置并进入插入模式）"。所以如果你忘记了如何返回上次插入点，可以进入 Go To 模式并查看菜单来找到 i。

反复练习所有这些命令（a、i、o、A、I、O 和 gi），输入一些文本，然后按 Escape 返回普通模式。然后再试一次。用鼠标在文本中移动光标（我保证我们很快就会学习键盘导航），在不同位置尝试这些命令，看看它们的行为。

要充分熟悉在普通模式和插入模式之间的切换。你可能认为会在插入模式下花费大部分时间，但事实是代码的编辑频率远高于新写代码，你会经常在这两种模式之间切换。

## [2.2. 可视模式](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_visual_mode)

LazyVim 从其前辈那里继承的另一个主要模式是"可视"模式。可视模式用于选择文本。通常，你可以进入可视模式，然后使用许多与普通模式相同的导航键来移动光标。由于我们还没有介绍这些导航按键，我会把可视模式的详细讨论推迟到第 8 章，到那时我们会有必要的基础知识。

## [2.3. 命令模式](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_command_mode)

命令模式与我们之前看到的其他模式不同，其他模式大多是子菜单或编辑器级别的"主要"模式。你可以在普通模式下使用 :（即 Shift+分号）进入命令模式。在 LazyVim 中，这会弹出一个小部件，你可以在其中输入所谓的"Ex 命令"。这个名称来自 vi 的前身 ex，这些年来除了作为 Vim 的一部分外，它基本上已不再被使用。

本质上，你可以在这个小部件中输入各种命令，并期望产生特定的行为。它实际上更类似于 Sublime Text 和 VS Code 普及的命令面板，尽管体验很不一样。

你已经从第 1 章知道一个 ex 命令了！还记得 <Escape><Colon>q!<Enter> 这个退出编辑器的命令吗？现在你知道了 Escape 是从任何模式返回到普通模式。冒号用于切换到命令模式，q 是 quit（退出）的简写（如果你不在意按键次数，也可以输入完整的 quit）。感叹号表示"不保存"，回车键表示"提交 ex 命令"。

举个例子，让我们看看 write 这个 ex 命令。输入 : 后面跟着 write myfile.txt，像这样：

<img src="mymedia\command-mode-write-dark.png" alt="command mode write dark" style="zoom:50%;" />

按回车键确认并执行命令，这将以给定的名称保存文件。

> 大多数命令可以缩写为它们最短的唯一公共前缀。你通常可以输入 :w myfile.txt 而不是 :write myfile.txt。最常用的命令甚至有特殊的组合命令，比如 :wq 会保存并退出，不过你可能会更喜欢使用 :x，因为它更短。

命令模式有点奇特。它有点像插入模式，因为你可以在其中输入文本，一些在插入模式下有效的快捷键在命令模式中也有效（包括用 Control-r 从寄存器中粘贴）。但其他快捷键在命令模式中的行为是不同的。最重要的一个是 Tab 键，它会对命令执行一种"tab 补全"。例如，:q<Tab> 会弹出一个像这样的菜单：

<img src="mymedia\command-tab-dark.png" alt="command tab dark" style="zoom:50%;" />

这个补全菜单的导航方式令人困惑。你可能需要把这部分内容加入书签或做些笔记，直到你习惯为止！

首先，如果你想在菜单中选择不同的条目，你肯定会认为可以使用方向键，对吧？确实可以，但这很混乱，因为你需要用左右键来实现上下移动。我知道！这很让人费解，对吧？

这主要是因为菜单在 LazyVim 中的外观与原始 Vim 不同，但按键映射没有改变。所以我建议使用 Tab 和 Shift-Tab 来选择菜单中的不同条目。这更容易记住，也更容易形成肌肉记忆：按一次 Tab 显示菜单，再次按 Tab 可以在菜单条目中循环选择。

其次，确认这些菜单条目时有一些细微差别。在上面的例子中，你可以直接按 Enter 确认选择并执行它。然而，有时你可能想确认选择后继续编辑命令。一个很好的例子是 :e 或 :edit 命令。

这个命令用于打开文件系统中的文件，但你必须输入完整的文件路径。例如，如果你有以下目录结构：

```bash
.
└── foo
    ├── bar
    └── baz
    │   └── fizz.txt
```

...并且你已经打开了 Neovim，要打开 fizz.txt 文件，你需要输入以下内容：

```
:e foo/baz/fizz.txt
```

如果需要访问深层嵌套的目录，这样输入会很麻烦。幸运的是，你可以使用 tab 补全功能。你可以输入 :e f<tab>b<tab><tab><tab> 来选择 foo/baz，但此时菜单仍然是打开的：

<img src="mymedia\edit-baz-dark.png" alt="edit baz dark" style="zoom:50%;" />

如果你现在按 Enter，它会打开 baz 文件夹而不是仅仅确认选择，这不是你想要的。如果再按 Tab，它会继续在菜单中循环。

相反，你有几个选择。向下箭头键会（不直观地）"进入"选中的目录，让你可以在其中的文件间使用 tab 切换。或者，使用 Control-y（y 代表"yes"）组合键。这将确认 baz 的选择并关闭菜单，但保持你在命令模式中。现在你可以再次按 tab 来补全命令中的 fizz.txt 部分。

可以重新映射这些键使其更像其他软件，说实话我认为这是 LazyVim 应该默认做的事情之一。不过我还没有找到我喜欢的组合，所以我就继续使用默认的键位绑定。

你可能不会在命令模式下花太多时间。例如，在 LazyVim 中有更简单的方法来打开文件，退出编辑器也是如此。如果你需要处理更复杂的命令历史，还有一个特殊的窗口可以让你用插入模式和普通模式来编辑命令，我们稍后会介绍。

现在，记住 <Tab> 和 Control-y，你就能在需要时导航命令菜单了。

顺便说一下，最重要的命令是 :help。Vim 是在人们还没有随时访问互联网的时候创建的，所以它有一个传统，就是将所有文档都随编辑器一起发布。例如，如果你记不住粘贴文本的快捷键，可以试试 :help put。或者，如果你想知道 Control-R 快捷键的作用，可以试试 :help CTRL-R。当然，Vim 的帮助文档也已经被你喜欢的搜索引擎和 AI 聊天机器人包揽了，所以如果你愿意的话也可以用这些新方式来查询。

## [2.4. 总结](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-2/#_summary_2)

在本章中，我们熟悉了模态编辑的概念和 LazyVim 最重要的模式。随着我们学习的深入，还会遇到其他的小模式，但掌握普通模式、插入模式和命令模式（以及它们之间的切换方法）将让你在 LazyVim 的使用之路上走得更远。

在下一章中，我们将学习在文档中移动光标的各种不同方法。

# [第三章：光标移动](https://lazyvim-ambitious-devs.phillips.codes/course/chapter-3/#_getting_around)





