# 书签笔记

此列表为一些容易忽略、忘记的nvim操作。仅供我自己参考。

- 这个补全菜单的导航方式令人困惑。你可能需要把这部分内容加入书签或做些笔记，直到你习惯为止！
- 或者，如果我不想进入插入模式，我会使用 $ 符号（Shift+4），这是普通模式下"将光标移动到当前行末尾"的命令。
- 如果你需要移动更远，可以使用 Control-f 和 Control-b 快捷键（向前forward和向后backward），它们会滚动整整一页文本。我不太喜欢这些，因为我永远不确定光标最终会在哪里，这让我感到迷失方向。但如果你需要快速滚动某些内容到可见区域以使用查找模式，它们会很有用。与 Control-d 和 Control-u 不同，Control-f 和 Control-b 可以加上数字前缀，所以你可以输入 5<Control-f> 来向前滚动 5 页。

  要逐行滚动窗口，使用 Control-y 和 Control-e。我不知道为什么选择这些快捷键。它们没有任何助记含义。我很容易忘记它们，所以我从不使用它们。这些快捷键接受数字前缀，所以如果你能记住它们，它们对于微调文本位置很有用。这些快捷键的主要优点是除非光标会滚动出屏幕，否则它们不会移动光标，所以如果你正在处理某一行并需要更好的可见性但不想移动光标，你可以使用 Control-y 和 Control-e。**(Control-f 和 Control-b、Control-y 和 Control-e可以用作其他操作的快捷键)**
- 我专门使用的相对光标快捷键是 zt、zb 和 zz。它们分别将光标所在行移动到屏幕的顶部、底部或中间。当移动到顶部或底部时，会在光标上方或下方保留几行作为上下文。

  还有一些命令也会将光标移动到窗口的第一列，但与其记住那些快捷键，我建议将前面的命令与 0 组合使用，比如 zt0、zb0 和 zz0。**0 命令就是"移动到行首"的意思**。如果你的键盘有 Home 键，你也可以使用它，但在很多键盘上 0 更容易按到。
- 要进入查找模式，按 f 键。和 Seek 模式一样，屏幕的一部分会变暗，提示你需要输入另一个字符。输入后，光标后所有该字符的实例都会被高亮显示。例如，fs 将高亮显示当前光标位置后所有的字母 s。**（很垃圾的一个模式，可以屏蔽掉）**
- 相反，你只需要进入普通模式并按 w 键就可以移动到下一个词的开头。如果你想移动到当前词的末尾，使用 e 键。如果你已经在当前词的末尾，e 将移动到下一个词的末尾。总的来说，你可能偶尔会听到 w、e 和 b 命令被称为"web"词。这只是表示"按词移动"。这些可能是你最常用的移动命令，比单个光标位置的移动更常用，这是因为大多数编辑操作往往涉及更改或删除一个词或一系列词。
- 如果你熟悉正则表达式，你可能知道 ^ 用于匹配文本开头或行首，$ 用于匹配结尾，所以使用这两个键绑定来匹配当前行的开头和结尾的助记方式可能不会像最初看起来那么难记。

  然而，这两个命令之间存在一定的不对称性：

  - $ (Shift-4) 命令简单地表示"移动到行尾"，即结束换行符之前的最后一个字符，不管那个字符是什么。
  - ^ 或插入符号 (Shift-6) 表示"移动到这一行文本的开头"。这里的"文本的"很重要：如果你的行开头有空白（比如缩进），^ 不会移动到最左边的列，而是移动到第一个非空白字符。

  要移动到行的最开始位置，使用 0 键。0 是唯一一个映射到命令的数字键，因为其他数字键都用来开始计数。但用 0 开始计数没有意义，所以我们可以用它来表示"移动到第零列"。
- 我们还没有讨论编辑器分屏或打开新标签页的内容，但是为了将来参考：实际上不同的窗口可以有不同的工作目录。改变当前窗口目录的命令是 :lcd，是"local change directory"的缩写。这可以成为同时处理多个项目的强大方式（例如，如果你是一个同时负责后端和前端项目的全栈开发者）。不过，LazyVim 的"Root"目录概念可以半自动化处理这个问题。
- Neo-tree 会将根目录或当前工作目录显示为最顶层目录。如果你需要向"上"导航到更高层级的目录，你需要使用退格键。
- 需要注意的是，keys 字段会与 LazyVim（extras）为 mini.files 提供的默认配置中的 keys 进行合并。如果出现冲突（比如 space fm），**我们的配置会覆盖默认值**。
- 你已经学过的导航命令，比如 s、f、hjkl 和 web 等，统称为动作命令（motion commands）。它们的作用是将光标从当前位置移动到新位置。大多数动作命令前面都可以加上数字（count），所以导航模式总是遵循 <数字><动作> 的格式
- 当你执行任何动词后，你可以导航到文档中的另一个位置，然后用一个键重复那个动词：.（这是一个句点，在这个上下文中通常被称为"点重复"）。
- 作为快捷方式，你也可以使用 [% 和 ]%，其中 % 键基本上就是"当前包围我的任何括号"的占位符。它们会跳转到当前所在的括号、花括号、尖括号或方括号的开头或结尾。（可以把%改成@符号）
- 当你输入 ] 并暂停等待菜单时，会看到如下选项：
- 如果你正在编辑的文件启用了拼写检查（或者你通过 <Space>us 手动启用了它），可以使用 [s 和 ]s 在拼写错误之间跳转。这一点在我刚开始写这本书时让我有点困惑，因为我原以为 ]d 会带我跳转到拼写错误的波浪下划线处，但实际上需要用 ]s。
- 这是我最喜欢的方括号组合快捷键：[h 和 ]h 允许你跳转到下一个 git "hunk"（代码块）。如果你不熟悉这个词（或者你认为这个词指的是帅哥），"git hunk" 指的是文件中那些包含了尚未暂存或提交的修改的区域。我的很多编辑工作都涉及在一个大文件的三四个地方进行修改。例如，我可能需要在文件顶部添加一个导入语句，在文件的其他地方修改一个函数调用的参数，然后在第三个地方修改接收该参数的函数。一旦开始编辑，我可能需要在这些位置之间来回跳转。]h 和 [h 非常适合这种情况，而且我不需要记住跳转历史或添加命名标记（本质上是书签）。
- 举个例子，一个常见的对象是括号：(。如果你输入命令 di(，会删除一对匹配的括号内的所有文本。但如果你输入 da(，则会删除括号内的所有文本以及两端的 ( 和 )。要查看 LazyVim 中的许多可能的文本对象，输入 da 并暂停。这是我看到的内容：
- 这有点像 git 分支的概念，只不过你的历史记录是针对每个按键自动跟踪的。不过，使用原始的 Neovim 命令处理撤销历史的分支可能会感觉很笨拙（如果你够勇敢的话，可以阅读 :help undo-branches）。相反，我建议配置和安装 undotree 插件。
- 对象 "、' 和 ` 用于操作被双引号、单引号或反引号包围的文本。如果你使用命令 ci"，你将在两个引号之间进入插入模式，其中字符串内的所有内容都被删除。但如果你使用 da"，它还会删除引号本身。
- 如果你想操作整个缓冲区，使用 ag 或 ig 文本对象。所以 cag 是删除所有内容并重新开始的最快方法，而 yig 会复制缓冲区，这样你就可以把它粘贴到 pastebin 或聊天机器人中。g 可能看起来是一个奇怪的选择，但它与 gg 和 G 跳转到文件开头或结尾的事实有一个对称性。如果你需要一个助记符，可以把 yig 理解为"yank in global"（在全局中复制）。
- 举个具体例子，命令 drAth2w 会删除从标签 h 处的"At"这个词开始的两个词，然后将光标跳回到删除开始前的位置。换句话说，它相当于命令 sAthd2w<Control-o>，这会查找到标签 h 处的"At"这个词，然后删除两个词，并使用 Control-o 跳回到你之前的历史位置。远程命令稍短一些，但这是另一个我倾向于忘记使用的功能。我的大脑在意识到"删除"模式之前就进入了"移动光标"模式，所以当我意识到本可以远程完成时，已经太晚了。