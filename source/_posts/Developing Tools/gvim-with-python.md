---
title: GVIM with Python Support(Windows)
tags: []
id: '152'
categories:
  - - VIM
date: 2020-06-01 12:55:11
---

早點在研究Vim 上python的Autocomplete([Jedi-vim](https://github.com/davidhalter/jedi-vim))時，遇到vim抓不到python的問題(Can not load python36.dll blablabla)，抓不到dll小事，問題是我電腦是python38阿ww不想亂改名把環境弄得很亂，以下簡單紀錄
<!-- more -->
**找不到pythonxx.dll**  
在.vimrc(\_vimrc)裡加入以下command即可

"記得換成你的路徑
set pythonhome=C:\\Python38
set pythonthreedll=C:\\Python38\\python38.dll

重開vim後可用:version來確認路徑是否正確  
或者是用:py3 print('Vim with python')來測試  
若還是不行的話確認一下vim和python3的版本  
我後來是發現vim 32bit, python3 64bit才導致會跳cannot load python36.dll  
重灌64bit的vim就都搞定了