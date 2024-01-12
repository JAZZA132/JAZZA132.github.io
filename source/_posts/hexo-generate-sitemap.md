title: hexo 產生 sitemap
author: Wang wei-hsiang
tags:
  - hexo
date: 2023-12-25 10:40:43
---
今天寫完日誌  
想要放到google console search上面供人家搜尋  
這時就必須放上sitemap  
這可以讓google的爬蟲知道可以過來爬取這份網頁
以下參考github文件  
https://github.com/hexojs/hexo-generator-sitemap

<h2>hexo-generator-sitemap</h2>

Generate sitemap.

Install  

``` 
npm install hexo-generator-sitemap --save 
```

You can configure this plugin in _config.yml.  


```
sitemap:
  path: 
    - sitemap.xml
    - sitemap.txt
  template: ./sitemap_template.xml
  template_txt: ./sitemap_template.txt
  rel: false
  tags: true
  categories: true
```
     
* path - Sitemap path. (Default: sitemap.xml)
* template - Custom template path. This file will be used to generate sitemap.xml (See default xml template)
* template_txt - Custom template path. This file will be used to generate sitemap.txt (See default txt template)
* rel - Add rel-sitemap to the site's header. (Default: false)
* tags - Add site's tags
* categories - Add site's categories

<h2>Exclude Posts/Pages</h2>

Add sitemap: false to the post/page's front matter.  
```
sitemap:
  path: 
    - sitemap.xml
    - sitemap.txt
  template: ./sitemap_template.xml
  template_txt: ./sitemap_template.txt
  rel: false
  tags: true
  categories: true
```