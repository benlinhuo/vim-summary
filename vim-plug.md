## vim 插件的安装和插件配置

#### Neovim

我们可以先关注下 Neovim，它是在 vim 的基础上，为了适应新的使用潮流而应运而生的产物。它的官网 [http://neovim.io/](http://neovim.io/)。

neovim 配置文件和 vim 不同，配置如下：
1. 用 .nvimrc 替换了 .vimrc 
2. 用 .nvim 替换了 .vim
3. 用 .nviminfo 替换了 .viminfo


#### 插件管理器

有一个很牛逼的人搞了个插件管理器，这下子可方便了很多。网址：[vim-plug](https://github.com/junegunn/vim-plug)

安装：
```javascript
下载 plug.vim ，然后将它放到目录 ~/.vim/autoload。因为在autoload下，所以当我们启动终端的时候，会自动启动里面的内容。也就是插件就被应用了

curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

因为是插件管理器，自然就会有插件列表了。具体语法可参照上述给的网址学习。需要说明的几点：

1. 插件的列表内容和列表配置，都需要写在 .vimrc 中
2. 插件列表书写格式，Plug '此处是路径 或 网址 ，又或是 仓库名'
3. 当我们把配置都写好以后，就可以安装或者更新插件了。终端：vim +PlugInstall +qall (也可以是 PlugUpdate)。安装完以后，每个插件会在目录 .vim/plugged 下生成关于自己的目录。

关于插件的配置可参照 [vimrc](./vimrc)，也可根据自己的需求加插件

关于插件的一个国外网站 [vim](http://vimawesome.com/)

#### Plug - THE NERD TREE

它允许我们打开一个文件目录，vim 是以树形目录结构展示的（一般 IDE 都有），可以方便的浏览项目的总体目录结构等等功效，当然关于 vim 的所有搜索查找的用法都是适用的。Enter 键盘可以直接打开或关闭一个文件目录

NerdTree 在 .vimrc 中常用配置如下：
```javascript
" 在 vim 启动的时候默认开启 NERDTree（autocmd 可以缩写为 au）
autocmd VimEnter * NERDTree

" 按下 F2 调出/隐藏 NERDTree
map  :silent! NERDTreeToggle  或者   map <F2> :NERDTreeToggle<CR>

" 将 NERDTree 的窗口设置在 vim 窗口的右侧（默认为左侧）
let NERDTreeWinPos="right"

" 当打开 NERDTree 窗口时，自动显示 Bookmarks
let NERDTreeShowBookmarks=1

" 关闭 vim 时，如果打开的文件除了 NERDTree ，没有其他文件时，它自动关闭，减少了多次按 :q!
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTreeType") &&b:NERDTreeType == "primary") | q | endif
```

针对 NerdTREE 命令

切换工作台和目录
```javascript
ctrl + w + h    光标 focus 左侧树形目录
ctrl + w + l    光标 focus 右侧文件显示窗口
ctrl + w + w    光标自动在左右侧窗口切换
ctrl + w + r    移动当前窗口的布局位置
```

```javascript
o       在已有窗口中打开文件、目录或书签，并跳到该窗口
go      在已有窗口 中打开文件、目录或书签，但不跳到该窗口
t       在新 Tab 中打开选中文件/书签，并跳到新 Tab
T       在新 Tab 中打开选中文件/书签，但不跳到新 Tab
i       split 一个新窗口打开选中文件，并跳到该窗口
gi      split 一个新窗口打开选中文件，但不跳到该窗口
s       vsplit 一个新窗口打开选中文件，并跳到该窗口
gs      vsplit 一个新 窗口打开选中文件，但不跳到该窗口
!       执行当前文件
O       递归打开选中 结点下的所有目录
x       合拢选中结点的父目录
X       递归 合拢选中结点下的所有目录
e       Edit the current dif

双击    相当于 NERDTree-o
中键    对文件相当于 NERDTree-i，对目录相当于 NERDTree-e

D       删除当前书签

P       跳到根结点
p       跳到父结点
K       跳到当前目录下同级的第一个结点
J       跳到当前目录下同级的最后一个结点
k       跳到当前目录下同级的前一个结点
j       跳到当前目录下同级的后一个结点

C       将选中目录或选中文件的父目录设为根结点
u       将当前根结点的父目录设为根目录，并变成合拢原根结点
U       将当前根结点的父目录设为根目录，但保持展开原根结点
r       递归刷新选中目录
R       递归刷新根结点
m       显示文件系统菜单
cd      将 CWD 设为选中目录

I       切换是否显示隐藏文件
f       切换是否使用文件过滤器
F       切换是否显示文件
B       切换是否显示书签

q       关闭 NerdTree 窗口
?       切换是否显示 Quick Help
```

切换标签页
```javascript
:tabnew [++opt选项] ［＋cmd］ 文件      建立对指定文件新的tab
:tabc   关闭当前的 tab
:tabo   关闭所有其他的 tab
:tabs   查看所有打开的 tab
:tabp   前一个 tab
:tabn   后一个 tab

标准模式下：
gT      前一个 tab
gt      后一个 tab

MacVim 还可以借助快捷键来完成 tab 的关闭、切换
cmd+w   关闭当前的 tab
cmd+{   前一个 tab
cmd+}   后一个 tab
```

#### phpfolding
其实 vim 自身就内置了折叠的功能，只不过不是很流畅。如下语法可以使用内置的折叠功能：
autocmd FileType c,cpp setl fdm=syntax | setl fen （表示如果发现文件类型为c或者cpp，就启用折叠功能）

内置或该插件都可以使用如下命令打开和关闭折叠：
```javascript
zo      打开光标下的折叠 (open)
zc      关闭光标下的折叠 (close)
zO      循环打开光标下的折叠，也就是说，如果存在多级折叠，每一级都会被打开
zC      循环关闭光标下的折叠
```

#### CTRLP
它主要是用来查找一些文件（只是文件，不能查找目录的）。当我处于某个项目的子目录时，他会自动向上查找是否有.git/.svn/.hg等文件，如果有的话，它就认为是一个项目目录，也就是即使自己当前在子目录下，也可以查找到该子目录之上的项目目录中文件；如果没有的话，就认为当前目录是它的查找范围。它支持模糊匹配。

一个使用路径：vim -> ctrl+p -> 输入要查找的文件名或路径名 -> 通过上下键是可以移动选中的文件名的 -> Enter 键便可以自动打开该文件(此处也有多种打开方式，如下：)

```javascript
多种打开方式
ctrl + t      在新的tab中打开
ctrl + v      在竖直试图中打开
ctrl + h      在水平试图中打开
ctrl + o
```

它还有一个功能是创建一个文件：我们可以按下 ctrl+p 输入文件名 ，按下 ctrl + y 便可以创建这个文件，且可以通过 vim 操作进行保存。等下次不需要重启 vim ，这个文件就自动出现在了我们的搜索列表中了。

ctrl+p 默认是按照文件路径进行匹配的，我们可以使用 ctrl+d 进行切换，变成文件名匹配，此时就只会按照文件名进行匹配了，会忽略前面的文件路径。再按一次 ctrl+d ，则就又可以按照文件路径进行匹配了。

ctrl+p 模式下，敲 ctrl+f 则可以切换到 buffers （缓冲区）范围下进行查找；再敲 ctrl+f 则又切换到 mru files 模式，则查找范围变成了最近打开的文件列表。同时打开多个文件：敲 ctrl+j+k ，然后可以通过上下箭头移动，当我们确定某个文件，使用 ctrl+z 进行标注，多次标注之后，当确定后，敲 ctrl+o 以竖直屏幕打开刚刚选定的多个文件。

ctrlP 的部分配置
```javascript
# 多个文件默认以竖直方式打开
let g:ctrlp_open_multiple_files = 'v'  

# 设置查找的文件列表，可以忽略一些文件
set wildignore+=*/tmp/*,*.so,*.swp,*.zip
let g:ctrlp_custom_ignore = {
    \ 'dir': '\v[\/]\.(git)$',
    \ 'file': '\v\.(log|jpg|png|jpeg)$',
    \
}
```

####NerdTree

####TagBar







