---
title: Steam合卡賺錢心得和小工具
tags: []
id: '252'
categories:
  - - Game
    - Steam
date: 2020-06-14 18:06:17
---

如題，本篇主要介紹如何透過Steam來賺錢，話先說在前頭，盈虧自負，本人不保證本篇教學的獲利與否

在此預設你的帳號已非[受限制的帳號](https://support.steampowered.com/kb_article.php?ref=3330-IAGK-7663)(有交易紀錄)，且有啟用Steam Guard也過了[交易託管期](https://support.steampowered.com/kb_article.php?ref=1047-edfm-2932&l=traditional%20chinese#itemhold)  
合卡賺錢原理很簡單：**從市集買寶珠=>寶珠合成遊戲的卡片擴充包=>拆包賣卡賺取價差** 每天進行這樣的Loop  
在這之前必須得先了解幾點先備知識(?)
<!-- more -->
*   Steam 市場的機制，從市集上買下來的商品有7天冷卻期，7天過後才能將其售出，這也包含寶珠和用受限制寶珠所合成的卡包
*   在市集上架商品成交後Steam約莫會抽15%的手續費
*   必有擁有遊戲才能合成該款遊戲的卡包
*   卡片有分普卡和閃卡，前者量多價低好賣，後者量少價高但不一定賣得出去。卡包有低機率會出閃卡
*   卡包每24hr只能合成一包
*   合卡所需寶珠數是根據該遊戲的總卡數而不同，總卡數越多需要的寶珠越少

  

  

而會在市集上購買卡片的族群大都是收藏或合徽章用，由於必須要擁有該遊戲才能合卡包，以下列出幾點我挑遊戲的看法

*   遊戲本體還算有興趣或已擁有(重要!畢竟你要投入購買遊戲本體的金額作為成本)
*   卡片的市場流通量還算OK(否則賣不出去)
*   遊戲受眾的腦粉程度(?)(或者是說，受眾合徽章的機率)
*   合卡獲利在$2 up (太低可能會因市場起伏賠錢)  
    

不過現在寶珠價格和卡片售價其實我覺得有些不成比例w，以往一堆遊戲都能獲利，現在能獲利的標的不多ww**(除了P4G)**，以下列出幾款我以前有在合的遊戲作為參考

*   Djmax Respect V (超賺w而且我腦粉，賣不出去自己合徽章也爽)
*   Monster Hunter World
*   The Witcher(當初上Netflix連帶卡片價格也水漲船高)
*   Rabi rabi
*   Date a Live, Stein;Gate, Neko %%全套(沒興趣，純粹合卡  
    

  

  


我約莫是上次冬特開始操作的，印象中當初計算一天獲利約20-30twd, 最後獲利至少可以把純粹合卡遊戲的本體成本(打平後額外賺了約莫1k-2k，不過都是以前了，近幾個月沒有標的ww**(除了P4G)**，以下為我個人之前的操作方法

1.  (Init.)寶珠價格可接受時購入 每天合卡所需寶珠數\*7 等待冷卻期結束  
    (在等待冷卻期的時候同時也可以每天合卡，不過合完的卡包是不能上架販售的，能販售時有低機率會價格下跌導致賠錢)
2.  (Loop)以當日寶珠價格計算獲利，合卡並馬上上架販售，並購入差不多數量的寶珠，將物品庫內的寶珠量約保持在 每天合卡所需寶珠數\*7 左右的數量，以確保每天都能夠有足夠的已冷卻寶珠合卡

當初是簡單寫隻程式丟排程掛著自動合卡，所以就只要晚上用電腦時要留意賣卡就行跟留意寶珠數量，操作上並不會對生活造成太大的影響，手遊的每日都比他麻煩多了(X  
不過一般的話必須每個卡包自己手動點合成，請自行斟酌合卡數量w

* * *

感覺寫的有點鬆散(?)最後附上一些會用到好用的小Chrome套件  
[Steam Cards Helper](https://chrome.google.com/webstore/detail/steam-cards-helper/fcjodomkmeimmpmhlnnpgjfjlpbnmohd) : 本文重點小弟自己寫的套件，會在商店頁面加入一顆按鈕，可以計算該遊戲合卡的獲利情形  
目前僅能在台區的steam使用(市集預設價格是以台幣計價)，其他地區計算可能會有錯誤  
若對Code有疑慮的話同時也有開源在[Github](https://github.com/www10177/SteamCardsHelper)上，也歡迎來給顆Star

![](https://od.ristw.dev/?/2020/SteamCardHelper/p4g.jpg)

[Steam Inventory Helper](https://chrome.google.com/webstore/detail/steam-inventory-helper/cmeakgjggjdlcpncigglobpjbkabhmjl)：批次販售卡片，能自動代入市場價格，印象中也能夠批次開卡包，每天拆完卡包後就靠這個直接賣

大概是這樣，想享受每天抽卡的快感嗎?快加入合卡的世界吧(X)