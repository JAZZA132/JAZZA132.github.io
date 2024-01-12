title: '大資料壓縮傳輸,JBOSS_wildfly 7.4中的GZIP 壓縮啟用'
author: Wang wei-hsiang
date: 2023-12-28 14:41:01
tags: jboss
---
公司專案回應並且渲染到前端畫面的時間過長大約要到20秒

user一定不能接受所以嘗試解決

首先查到前台拿到資料loading大約才2秒,問題出在程式與server的回應時間

討論決議先嘗試啟用gzip以縮短響應時間

---

HTTP 壓縮可以大大提高瀏覽網站的速度，它的原理是，在客戶端請求網頁後，從伺服器端將網頁檔案壓縮，再下載到客戶端，由客戶端的瀏覽器負責解壓縮並瀏覽。 相對於普通的瀏覽流程HTML ,CSS,Javascript , Text ，它可以節省40%左右的流量。 更重要的是，它可以對動態產生的，包括CGI、PHP , JSP , ASP , Servlet,SHTML等輸出的網頁也能壓縮，壓縮效率驚人。

---

## xml修改

1.

jboss-eap-7.4\standalone\configuration\standalone.xml

```jsx
<subsystem xmlns="urn:jboss:domain:undertow:1.2">   <!-- SEARCH FOR THIS: urn:jboss:domain:undertow -->
  <buffer-cache name="default"/>  
  <server name="default-server">  
  <http-listener name="default" socket-binding="http"/>  
  <host name="default-host" alias="localhost">  
  (...)

  <!-- ADD THIS FOR GZIP COMPRESSION -->
  <filter-ref name="gzipFilter" predicate="exists['%{o,Content-Type}'] and regex[pattern='(?:application/javascript|text/css|text/html|text/xml|application/json)(;.*)?', value=%{o,Content-Type}, full-match=true]"/>  
  <!-- /GZIP COMPRESSION -->

  </host>  
  </server>  
(...)  
  <filters>  
  (...)  

  <!-- ADD THIS FOR GZIP COMPRESSION -->
  <gzip name="gzipFilter"/>  
  <!-- /GZIP COMPRESSION -->

  </filters>  
</subsystem>
```

設定都在<subsystem>標籤之中,filters標籤需要額外手動添加

2.

右鍵點擊開啟content-encoding
![](./images/1.png) <br>
![](./images/2.png) <br>
![](./images/3.png) <br>


成功

## management console jboss

1.

![](./images/4.png)

![](./images/5.png)



先添加Name

2.

![](./images/6.png)

![](./images/7.png)



點擊filters

3.

![](./images/8.png)

添加name跟邏輯,重啟