<h1 align="center">Vim config for PHP</h1>
bstdn@qq.com
2016-05-18 20:00:00


## 【谢谢】

## 【正文】
---

<h2 name="1">1 安装</h2>
清空 .vim/ 目录，安装 vundle:

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

复制 或 软链 .vimrc 至 ~/ home目录下

安装插件，进入 vim 执行:

```
:PluginInstall
```

要卸载插件，先在 .vimrc 中注释或者删除对应插件配置信息，然后在 vim 中执行

```
:PluginClean
```

批量更新，只需执行

```
:PluginUpdate
```

<h2 name="2">2 主题风格</h2>

```
可以去 http://vimcolorschemetest.googlecode.com/svn/html/index-c.html 慢慢选
* 素雅 solarized（https://github.com/altercation/vim-colors-solarized ）
* 多彩 molokai（https://github.com/tomasr/molokai ）
* 复古 phd（http://www.vim.org/scripts/script.php?script_id=3139 ）
 ```
在 .vimrc 中选用某个主题：

```
" 配色方案
set background=dark
colorscheme solarized
"colorscheme molokai
"colorscheme phd
```

<h2 name="3">3 快捷键</h2>

```
" 定义快捷键的前缀，即<Leader>
let mapleader=";"
```

```
" vim 自身（非插件）快捷键

" 定义快捷键到行首和行尾
nmap LB 0
nmap LE $

" 设置快捷键将选中文本块复制至系统剪贴板
vnoremap <Leader>y "+y
" 设置快捷键将系统剪贴板内容粘贴至vim
nmap <Leader>p "+p

" 定义快捷键关闭当前分割窗口
nmap <Leader>q :q<CR>
" 定义快捷键保存当前窗口内容
nmap <Leader>w :w<CR>
" 定义快捷键保存所有窗口内容并退出 vim
nmap <Leader>WQ :wa<CR>:q<CR>
" 不做任何保存，直接退出 vim
nmap <Leader>Q :qa!<CR>

" 设置快捷键遍历子窗口
" 依次遍历
nnoremap nw <C-W><C-W>
" 跳转至右方的窗口
nnoremap <Leader>lw <C-W>l
" 跳转至方的窗口
nnoremap <Leader>hw <C-W>h
" 跳转至上方的子窗口
nnoremap <Leader>kw <C-W>k
" 跳转至下方的子窗口
nnoremap <Leader>jw <C-W>j
" 定义快捷键在结对符之间跳转
nmap <Leader>M %


" 正向遍历同名标签
nmap <Leader>tn :tnext<CR>
" 反向遍历同名标签
nmap <Leader>tp :tprevious<CR>
```

```
" 基于语义的代码导航

nnoremap <leader>jc :YcmCompleter GoToDeclaration<CR>
" 只能是 #include 或已打开的文件
nnoremap <leader>jd :YcmCompleter GoToDefinition<CR>
```

```
" 查找

" 使用 ctrlsf.vim 插件在工程内全局查找光标所在关键字，设置快捷键。快捷键速记法：search in project
nnoremap <Leader>sp :CtrlSF<CR>

" 快捷替换
let g:multi_cursor_next_key='<S-n>'
let g:multi_cursor_skip_key='<S-k>'
```

```
" 工程文件浏览

" 使用 NERDTree 插件查看工程文件。设置快捷键，速记：file list
nmap <C-n> :NERDTreeToggle<CR>
```

```
" 多文档编辑
 
" 显示/隐藏 MiniBufExplorer 窗口
map <Leader>bl :MBEToggle<cr>

" buffer 切换快捷键
map <S-Right> :MBEbn<cr>
map <S-Left> :MBEbp<cr>
```

```
" 快速移动

let g:EasyMotion_leader_key = 'f'
```

```
" 搜索多个文件

" vimgrep /匹配模式/[g][j] 要搜索的文件/范围

nmap <C-j> :cn<CR> "查找下一个
nmap <C-k> :cp<CR> "查找上一个
nmap <Leader>co :copen<CR> "打开quickfix
nmap <Leader>cq :cclose<CR> "关闭qucikfix


" 快速搜索和替换多个文件
<Leader>vv or :Grep: <Leader>vv命令将在文件中搜索当前光标下的单词
        :Grep word将搜索"word", 如果加叹号:Grep !word表示全词匹配的方式搜索
        Grep也可以带参数, 比如:Grep -ir word, r表示递归目录. i表示不区分大小写.
<Leader>vV : 全词匹配搜索, 同:Grep !word;
<Leader>va : 与vv相似, 搜索结果append在上次搜索结果之后;
<Leader>vA : 与vV相似, 搜索结果append在上次搜索结果之后;
<Leader>vr or :Replace :替换;
<Leader>vo or :GrepOptions: 打开选项菜单;
```
