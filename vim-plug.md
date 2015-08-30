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
2. 插件列表书写格式，Plug '此处是路径 或 网址'
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

#### CTRLP