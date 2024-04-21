title: 'Maven,ant打包差異'
author: Wang wei-hsiang
date: 2024-03-18 20:55:37
tags:
---
專案需要給別人做打包

對方使用ant

但打包完之後呼叫部屬完api會失效

---

排查

兩邊編譯出的檔案反編譯看不出差異

但細看檔案大小會有不同

推測編譯的結果有問題

![](./images/Maven-ant打包差異-1/1.png) <br>

縮小範圍,是專案裡的@annotation在反序列化的時候導致的

在編譯config中添加說明即可

![](./images/Maven-ant打包差異-1/2.jpg) <br>