##  爬蟲練習 ##

#### 基本概念 ####

爬蟲基本概念就是希望透過對網路頁面內容回歸存取並在其中獲取所希望得到的資料內容
 
基本步驟:
1. 網站分析 <br>
  ``` 必須先了解網站的結構，譬如網頁各項按鈕頁面之間的連結關係，是否有入口頁面的引導需要處理，網站甚至網頁原始碼是否有經過js渲染```
2. 獲取數據 <br>
  ``` 透過Http request get反覆提取網頁原始碼內容```
3. 資料結構分析 <br>
  ``` 分析原始碼內容 ```
4. 整理內容 <br>
  ``` 將獲取的資料整理顯示以及儲存 ```

#### BeautifulSoup ####

[BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/)為一Python函式庫套件用以分析HTML源碼的內容, 
透過一些簡易的語法操作即可讓使用者獲取想要的內容
```
soup = BeautifulSoup(response.text, 'lxml')
articles = soup.find_all('div', 'r-ent')  // 提取所有div區塊含有r-ent tag的區塊內容
for article in articles:
    meta = article.find('div', 'title').find('a') or NOT_EXIST  
```

#### 練習1: Ptt資料 ####

<img src="https://github.com/momo457121/Crawler/blob/master/crawler_ptt.png" width="500">

此網頁為PTT movie版內容並且由於網頁無任何渲染隱藏內容，因此選用此頁面作為練習BeautifulSoup語法的練習

透過分析網頁原始碼結構可以得知每個文章標題被包入的一個div class "r-ent"的區塊中
因此可透過soup獲取所有r-ent的內容
<br>
另外可從"btn-group-paging"區塊得知其包含上/下頁面的對應url連結
<br>
<br>
有了以上這些基本了解即可透過迴圈反覆query提取數頁的資料內容

#### 待練習項目 ####
1. selenium+phantomjs
2. scrapy
