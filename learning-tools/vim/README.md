# Vim 配置笔记

> OS：Ubuntu 18.04

上古神器 Vim 配置记录，个人 [.vimrc](<https://github.com/Joee1995/AI-Learning-Notes/blob/master/学习工具/Vim/vimrc>) 配置文件

## 安装

```
zhou@zhou-ubuntu:~$ sudo apt-get install vim
```

## 新手指南

```
zhou@zhou-ubuntu:~$ vimtutor
```

## 基本使用

参考：[Vim 基本使用方法](<https://blog.51cto.com/13525470/2053771>)

参考：[Vim 键位映射 map](<https://blog.csdn.net/zgqxiexie/article/details/72973662>)

参考：[Vim 使用 map 自定义快捷键](<https://blog.csdn.net/jasonding1354/article/details/45372007>)

个人基本配置 `~/.vimrc` (超简易版)：

```
set fenc=utf-8
set fencs=utf-8,usc-bom,euc-jp,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8
set expandtab
set tabstop=4
set softtabstop=4
set shiftwidth=4
set cursorcolumn
set cursorline
set number

syntax on
filetype on
filetype plugin indent on
filetype indent on
```

使 `~/.vimrc` 保存立即生效

```
autocmd BufWritePost $MYVIMRC source $MYVIMRC
```

## 插件管理

参考：[Vim-plug：极简 Vim 插件管理器](<https://linux.cn/article-9751-1.html>)

参考：[VIM 插件管理工具 vim-plug 简明教程](<https://hiberabyss.github.io/2018/03/21/vim-plug-introduction/>)

参考：[Vim 配置及插件安装管理](<https://blog.csdn.net/namecyf/article/details/7787479>)

安装 vim-plug 插件管理

```
zhou@zhou-ubuntu:~$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
> https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

管理插件示例：

“lightline.vim” 插件，在 `~/.vimrc` 添加如下行

```
call plug#begin('~/.vim/plugged')
Plug 'itchyny/lightline.vim'
call plug#end()
```

修改完成后重启 Vim 或重新加载

```
zhou@zhou-ubuntu:~$ source ~/.vimrc
```

打开 Vim 编辑器

```
zhou@zhou-ubuntu:~$ vim

# 检查插件状态
:PlugStatus

# 安装配置文件 ~/.vimrc 中声明的插件
:PlugInstall

# 更新插件
:PlugUpdate

# 删除插件，需要先将配置文件中的相应声明注释
:PlugClean

# 升级 vim-plug 本身
:PlugUpgrade
```

个人插件配置 `~/.vimrc` (持续更新)：

```
" Plugins will be downloaded under the specified directory.
call plug#begin('~/.vim/plugged')

" Declare the list of plugins.
Plug 'junegunn/vim-plug'

Plug 'scrooloose/nerdtree'
Plug 'Xuyuanp/nerdtree-git-plugin'

Plug 'SirVer/ultisnips'
Plug 'honza/vim-snippets'

Plug 'lervag/vimtex', { 'for': 'tex' }
Plug 'xuhdev/vim-latex-live-preview', { 'for': 'tex' }

" List ends here. Plugins become visible to Vim after this call.
call plug#end()

" Plug nerdtree
let g:NERDTreeWinPos = "right"
let NERDTreeShowHidden=0
let NERDTreeIgnore = ['\.pyc$', '__pycache__']
let g:NERDTreeWinSize=35

map <leader>nn :NERDTreeToggle<cr>
map <leader>nb :NERDTreeFromBookmark<Space>
map <leader>nf :NERDTreeFind<cr>

" Plug nerdtree-git-plugin
let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ 'Ignored'   : '☒',
    \ "Unknown"   : "?"
    \ }

" Plug ultisnips
let g:UltiSnipsExpandTrigger='<tab>'
let g:UltiSnipsJumpForwardTrigger='<tab>'
let g:UltiSnipsJumpBackwardTrigger='<s-tab>'
let g:UltiSnipsEditSplit='vertical'
let g:UltiSnipsSnippetDirectories=["zhou-snippets"]

" Plug vimtex
let g:tex_flavor='latex'
let g:vimtex_view_method='zathura'
let g:vimtex_quickfix_mode=0
set conceallevel=1
let g:tex_conceal='abdmg'

" Plug vim-latex-live-preview
autocmd Filetype tex setl updatetime=1
let g:livepreview_previewer='zathura'
" let g:livepreview_cursorhold_recompile=0
```

## 奈斯的插件

插件：[SirVer/ultisnips](<https://github.com/SirVer/ultisnips>)

插件：[honza/vim-snippets](<https://github.com/honza/vim-snippets>)

参考：[VIM 代码片段插件 ultisnips 使用教程](<https://blog.51cto.com/10245818/2167828>)

参考：[简述 Vim 插件——UltiSnips 配置代码片段](<https://blog.csdn.net/guchuanhang/article/details/72953770>)

参考：[vim 入坑指南（六）插件 UltiSnips](<https://vimzijun.net/2016/10/30/ultisnip/>)

插件：[lervag/vimtex](<https://github.com/lervag/vimtex>)

参考：[vimtex documentation](<https://github.com/lervag/vimtex/blob/master/README.md>)

插件：[xuhdev/vim-latex-live-preview](<https://github.com/xuhdev/vim-latex-live-preview>)

参考：[Lively Previewing LaTeX PDF Output](<https://github.com/xuhdev/vim-latex-live-preview/blob/master/README.md>)

插件：[scrooloose/nerdtree](<https://github.com/scrooloose/nerdtree>)

插件：[Xuyuanp/nerdtree-git-plugin](<https://github.com/Xuyuanp/nerdtree-git-plugin>)

## Vim 打造

参考：[Vim 神器的打造方式](<https://www.cnblogs.com/yangshunde/p/7775010.html>)

参考：[V 字君的 Vimpress](<https://vimzijun.net/categories/>)