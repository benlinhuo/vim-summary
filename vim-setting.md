##vim 的配置

vim 的配置主要是为了能让我们在使用的时候看着更舒服，工作效率更高。

在 UBUNTU 中，vim 的配置文件所在路径：/etc/vim/vimrc。

mac 中，路径是：~/.vimrc，如果我们发现当前路径下没有该文件，可以自己新建，也可以 cp /usr/share/vim/vimrc ~/.vimrc 。注意，该文件中注释一行是英文字符双引号“。

具体的配置内容如下：

1. 显示行号：set nu
2. 语法高亮：syntax on
3. 自动缩进对齐：
```javascript
set autoindent 
set smartindent 智能对齐，对类似 C 语言编写有用
```
4. 突出当前行：set cursorline
5. 显示状态栏 (默认值为 1, 无法显示状态栏)：set laststatus=2
6. 设定配色方案为 molokai ：colorscheme molokai
7. 关闭 vi 兼容模式：set nocompatible
8. 打开状态栏标尺：set ruler
9. 每行最多列数：set colorcolumn=120  

以下是一些不常用的配置，或者通过插件可以更好的配置项：

1. 设定 << 和 >> 命令移动时的宽度为 4：set shiftwidth=4
2. 设定 tab 长度为 4：set tabstop=4
3. 覆盖文件时不备份：set nobackup
4. 自动切换当前目录为当前文件所在的目录：set autochdir
5. 开启插件：filetype plugin indent on
6. 设置备份时的行为为覆盖：set backupcopy=yes
7. 搜索时忽略大小写，但在有一个或以上大写字母时仍保持对大小写敏感：set ignorecase smartcase
8. 禁止在搜索到文件两端时重新搜索：set nowrapscan
9. 输入搜索内容时就显示搜索结果：set incsearch
10. 搜索时高亮显示被找到的文本：set hlsearch 
11. 关闭错误信息响铃：set noerrorbells 
12. 关闭使用可视响铃代替呼叫：set novisualbell 
13. 置空错误铃声的终端代码：set t_vb=   
14. 插入括号时，短暂地跳转到匹配的对应括号：set showmatch
15. 短暂跳转到匹配括号的时间：set matchtime=2 
16. 设置魔术：set magic  
17. 允许在有未保存的修改时切换缓冲区，此时的修改由 vim 负责保存：set hidden
18. 隐藏工具栏：set guioptions-=T 
19. 隐藏菜单栏：set guioptions-=m
20. 开启新行时使用智能自动缩进：set smartindent 
21. 不设定在插入状态无法用退格键和 Delete 键删除回车符：set backspace=indent,eol,start
22. 设定命令行的行数为 1：set cmdheight=1 
23. 设置在状态行显示的信息：set statusline=\ %<%F[%1*%M%*%n%R%H]%=\ %y\ %0(%{&fileformat}\ %{&encoding}\ %c:%l/%L%)\
24. 开始折叠：set foldenable    
25. 设置语法折叠：set foldmethod=syntax   
26. 设置折叠区域的宽度：set foldcolumn=0
27. 设置折叠层数为：setlocal foldlevel=1
28. 设置为自动关闭折叠 ：set foldclose=all 
29. 用空格键来开关折叠：nnoremap <space> @=((foldclosed(line('.')) < 0) ? 'zc' : 'zo')<CR>














