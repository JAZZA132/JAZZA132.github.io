---
title: 當git rebase後悔了,又不想放棄原本的修改,調整指令教學
author: Wang wei-hsiang
tags:
  - git
categories:
  - git
date: 2023-11-16 09:44:00
keywords: 當git rebase後悔了,又不想放棄原本的修改,調整指令教學
---
# 當git rebase後悔了,又不想放棄原本的修改,調整指令教學

```
A - B - C - F (master)
         \
          D - E (feature, origin/feature)
```

rebase之後變成

```
A - B - C - F (master)
              \
               D - E (feature)
```

這時候如果我後悔了,想要取消該次rebase,不想要F了,但想保留D、E,該如何做呢?使用reset應該是會把DE都清除掉的樣子

使用 git rebase -i {commit 的hash},進入到vim介面
可以整理commit紀錄
有提交過的紀錄會已pick描述
剔除不想要的commit即可
當想要存檔離開的時候使用鍵盤左上角esc,輸入   :wq 即可 ,記得”:”也要輸入