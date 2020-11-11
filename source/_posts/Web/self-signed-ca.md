---
title: 自簽CA憑證
tags: []
id: '50'
categories:
  - - Web
date: 2020-05-19 22:54:22
---

前幾天在搞 HTTPS MITM遇到的問題，直接信任自己簽的self-signed cert. 瀏覽器還是會跳警告，而且在ios上還是過不了。而要處理這個問題的話不僅僅要簽一組憑證，還要搞一組CA憑證出來
<!-- more -->
簡單的說，HTTPS加密需要一組公鑰、私鑰，而每組金鑰/憑證會對應到Server的domain，你可以自己簽發這一組憑證並安裝在server，問題是一般瀏覽器連線到你的server的時候會發現你的憑證是自己簽的，雖然是成功走https(http with SSL)，但是還是會跳出警告說憑證不安全。

一般來說，對外開放服務的SSL憑證得透過**數位憑證認證機構**(CA)簽發才能受到瀏覽器/系統的認可。至於如何Client得知你的憑證是否是通過合格的CA發布的？實際上你的services的公鑰是透過CA再加密過的，而Client必須擁有CA的所發布的公鑰才能解開。而系統會預裝世界上受到大家信任的CA的公鑰。

以下是我想到的可能會用到自簽CA憑證來簽發SSL證書的幾個情境：

*   測試環境
*   內網、不能用certbot去簽
*   HTTPS MITM：需要某domain的私鑰，但是你又不是該domain的擁有者  
    

## Tutorial

個人操作平台是windows 10, 用從git資料夾裡面co出來的openssl(X

*   設定windows openssl.cnf的環境變數(不設的話產生公鑰的時候要用-config OPENSSL\_CNF\_PATH來設定位置
*   產生CA的一組憑證
*   忘記會不會跳出叫你填資料的表單了，有跳的話這邊可以隨便填不一定要跟domain name一致

Set OPENSSL\_CONF="C:\\openssl\\openssl.cnf"
openssl genrsa -out myCA.key 2048
openssl req -x509 -sha256 -new -key myCA.key -out myCA.cer -days 730 -subj /CN="DO\_NOT\_TRUST My Custom CA "

先將下面存成v3.ext並放在同個資料夾內(記得改EXAMPLE.com跟IP)  
沒加v3.ext的的這些資訊的話chrome和ios都還是會跳警告(local issuer的樣子)

authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName =@alt\_names

\[alt\_names\]
DNS.1 = EXAMPLE.COM
IP.1 = 127.0.0.1

*   這邊的CN變數是你要簽發的domain，記得換掉
*   如果要用同組CA憑證簽多個domain的話重跑一次這邊就可了(v3.ext也要記得改)

SET CN=EXAMPLE.com
openssl genrsa -out %CN%.key 2048
openssl req -new -out %CN%.req -key %CN%.key -subj /CN=%CN%
openssl x509 -req -sha256 -in %CN%.req -out %CN%.cer -CAkey myCA.key -CA myCA.cer -days 365 -CAcreateserial -CAserial serial-sha256 -extfile v3.ext

弄完後記得要把myCA.cer存到各os的信任區  
windows 直接點兩下安裝，然後指定位置到受信任的根憑證類似這樣的名字  
ios先想辦法把myCA.cer傳過去(mail, web...)點開後去**設定->一般->描述檔**安裝，安裝完後記得去**一般->關於本機->憑證信任設定**信任他

特別提醒一下別隨便信任別人給你的CA憑證，且也要保管好你自己的CA私鑰，windows無感，看ios把信任憑證藏那麼深大概就知道這是件很嚴重的事

擁有設備所信任CA公鑰所對應私鑰的人，可以產生被該設備所信任的任何domain的憑證。講白點，你去到假的網站，你完完全全不會發現，網址完全無誤，Https憑證也不會有任何問題。所以，用完後記得刪掉憑證或好好保管之