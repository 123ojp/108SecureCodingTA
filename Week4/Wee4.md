---
title: 108 網頁  
tags: 大學 , 助教 , 安全程式
---


# 安全程設設計 
## Web安全 10/01

---

## 大綱
- 電腦安全
- 網頁安全

---

## 電腦安全
* 預設使用者輸入永遠是危險的
* Secure by Default 原則 
* 服務越多漏洞越多

---

## 電腦安全
* 駭客只挑最弱的環節打
* 資訊安全的強度取決於最弱的那個環節
* 被黑從來不是在你知道的那個點上
* 攻擊是一個點，防守是一個面

---

![](https://i.imgur.com/yxrYvu4.png)


---

## 電腦安全
- 沒有絕對安全，只有成本問題
    - 是防禦者的成本，也是駭客的成本
- 防禦不是一直補，而是引導駭客做你想要讓他做的事
    - Honeypot 

---

## 網頁安全

- 一直有網頁遭到攻擊
![](https://i.imgur.com/iYMSdvy.png)

---

![](https://i.imgur.com/tyC7wEW.png)

---

![](https://i.imgur.com/GmKYH9d.png)

---

![](https://i.imgur.com/CFGGt3U.png)

---

## 通訊協定-HTTP
- 不只網頁走這協定 許多程式api也走http
    - Pokemon
    - 神魔之塔
    - Google apps

---

- 為了解決新的開發上的問題，Web系統越來越複雜
    - Ex :xampp(apache + php + MySQL)
- 現在有許多框架，開源的服務，往往造成一有漏洞就是通殺
- Ｗeb架構有千千百百種
    - 不但需要符合眾多瀏覽器，也有多款伺服器

---

- 由於網頁是由一堆程式疊起來的
- 沒有人能能保證哪個基石會出狀況
- 所以 讓網頁安全是很困難的
![](https://i.imgur.com/89sBKbw.png)

---

## Web 包含的範圍

HTML、CSS、JavaScript、PHP、Python、
Ruby、Java、Git、Svn、HTTP、Cookie、
Base64、URL Encode、MD5、AES、
SHA、WAF …… etc

---

![](https://i.imgur.com/6oCqYu6.png)


---

![](https://i.imgur.com/9D2a9KA.png)


---

![](https://i.imgur.com/LUAOB4h.png)

---

## Client-Server 架構

![](https://i.imgur.com/inR5gyp.png)

---

## 前後端簡略版本

![](https://i.imgur.com/ZFumghZ.png)

---

### 前端
* HTML (最重要)
* CSS (排版美觀)
* Javascript (互動)

---

### 後端

* 程式語言(php,asp,python…)
* 伺服器軟體(apache,nginx…)
* 資料庫(MySQL,OracleDB…)

---

## Http 請求方法
![](https://i.imgur.com/HmtT29X.png)

---

![](https://i.imgur.com/l16v3zF.png)

---


![](https://i.imgur.com/RjiAvJG.png)

---


![](https://i.imgur.com/rnFc9J2.png)


---

![](https://i.imgur.com/hKGFCTV.png)

---

![](https://i.imgur.com/eubtfjA.png)

---

### HTTP Method

- 第一行是HTTP Request的方法
    - 常見的方法 `GET、POST`
- 接下來Header & Body 
- (不是HTML的那個`<head> <body>`)

---

### HTTP Method
- 瀏覽器就是透過HTTP跟web server 溝通，來獲取呈現在user面前的網頁內容。
- Header與Body之間使用 `<CRLF>` 斷行
    - print(“\r\n”)

---

### HTTP Method
- GET
    - 最常見的HTTP Method
    - 在瀏覽器網址列打完網址，按Enter，就是送出GET請求
    - 可以用url傳參數 
        `http://aa.bb/?a=123&b=456`

---

### HTTP Method
- POST
    - 常見用於按扭轉跳、表單送出、傳送帳號密碼等等
    - 上傳檔案
    - 在 resquests header 換行後 附加

---

### HTTP Method
- 其他Method
    - HEAD 
    - OPTIONS
    - TRACE
    - …

---

### HTTP Status code

|code|定義|
|---|---|
200| 請求已成功，請求所希望的回應頭或資料體將隨此回應返回。
301 |被請求的資源已永久移動到新位置
403 |伺服器已經理解請求，但是拒絕執行它。
404 |請求失敗，請求所希望得到的資源未被在伺服器上發現。
451 |該存取因法律的要求而被拒絕。
500 |伺服器遇到了一個未曾預料的狀況

---

### HTTP Request Headers
- HOST
    - vhost
- Accept: text/html; text/plain
- Accept-Encoding: gzip
- Accept-Language: en

---

### HTTP Request Headers
- Referer
    - 從哪裡轉跳過來
    - 圖片防盜連
    - 許多瀏覽器強制賦予，並不能修改
- User-Agent
    - 告訴Server 你用的瀏覽器 作業系統 等等資訊
    - 自動切換成手機版網頁就是看這個


---

### HTTP Request Headers
- Cookie
    - 網站為了辨識使用者，或者延續上一個或之前的工作狀態，所以會產生一個機制來儲存各個使用者的狀態。
    - 在Server 端稱之為Session
        - 使用javascript 或 Header(set-cookies)設定
    - 存在Client端，叫做Cookie 
        - (透過Header送出去，讓Server辨識)
    - 如果可以偽造，就可以提升權限or擁有平行的權限

---

### 反向代理 (Request Headers)
- Client-ip
- X-Forwarded-For
- 這兩者是在於反向代理時，讓後端server確認來源ip所加上的header
- 新增這個header可能可以成功欺騙ip位子
![](https://i.imgur.com/IXCY5N5.png)

---

### HTTP Response Headers
- Server: nginx/apache …
    - 標示 Server 的版本甚至OS的版本

- Location : http://www.example.com
    - 用來轉跳頁面，通常搭配 301使用

---

### HTTP Response Headers
- Content-Length: 32
    - body 有 32 bytes

- Content-Type: (MIME type)
	- application/x-www-form-urlencode
	- application/json
	- text/html
	- text/plain
	- multipart/…  (boundary needed)


---



## 何謂 Socket
- 想像你寫了一個會幫你把兩個數字加起來的程式
- 介面就是 終端機 
- 而兩台電腦用網路溝通 就是Socket
- 啟用一個Socket個會佔據兩邊電腦一個port

---

## Ip & port
![](https://i.imgur.com/0tEa6Tp.png)

---

## 特殊ip
- 0.0.0.0  他已經不是ip 他代表這台電腦的所有介面
    - Ex. 今天有三張網路卡 如果想一起用 就用0.0.0.0
- 255.255.255.255
    - 如果對這ip ping 就是對這區網內所有ip丟封包(廣播)
- 127.0.0.1
    - 每個電腦都有的ip，代表自己
- 內網
    - 10.x.x.x、172.16.x.x∼172.31.x.x、192.168.x.x
    - 這三個網段是給私人網路（內網）


---

##  用ncat簡單建立socket吧
- 使用ncat 建立Socket
- 安裝 ： sudo apt install nmap

![](https://i.imgur.com/XItufwy.png)


---

## ncat

裝完之後 開兩個終端機 分別輸入

- `ncat -l -p 10000`
- `ncat 127.0.0.1 10000`

---

## ncat

- 在兩邊都輸入一些東西 並按enter 觀察

---

## 變數

- 參數說明 `–p` 代表哪個port
- `–l` 代表 監聽哪個端口 並等待連線
- 127.0.0.1 代表自己電腦

---

## 情境
- 今天想要讓使用者連進來回答問題
	- 可以

---

### 首先寫一個 test.c
```clike=
//引入標頭檔
#include <stdio.h>

//main為主函式
int main(){
    //printf為印出字串
    printf("Give me Two NUm");
    //宣告兩個整數變數
    int a ;
    int b;
    //%d 表整數
    scanf("%d %d",&a,&b);//輸入兩個整數並存入a跟b
    printf("=%d",a+b);//印出a+b答案
}
```


---

- 用Gcc編譯他
- `gcc  test.c –o a.out`
- 並用ncat 讓他變成socket的連接口
- `ncat -kl -vc "./a.out"  -p 10000`
![](https://i.imgur.com/T6IWCCb.png)

---

- 另外一邊連連看
- `ncat 127.0.0.1 10000`
- ![](https://i.imgur.com/80Qq1o7.png)

---

### 來試試看作假的http server
```clike=
#include<stdio.h>
int main(){
scanf("\n");
printf("HTTP/1.1 200 OK\nServer:fake\n\n<h1>test</h1>");
}
```
- `gcc test.c -o a.out`
- `ncat -kl -vc "./a.out"  -p 10000`
- http://127.0.0.1:10000/

---

### WOW
![](https://i.imgur.com/DFHrBmj.png)


---


---

## 基礎上玩了 來打CTF吧
![](https://i.imgur.com/V3It4NC.png)

----

![](https://i.imgur.com/AgjAHka.png)


---

![](https://i.imgur.com/Yv6c8dK.png)

----

![](https://i.imgur.com/d6Tqi7a.png)

---

![](https://i.imgur.com/ms6F44t.png)

----

### 觀察network 發現302轉跳
![](https://i.imgur.com/4Wwm0D3.png)

----

解法:
- 使用 ubuntu curl 指令
- 他不會理301、302轉址
`curl http://140.134.25.138:10002/`
![](https://i.imgur.com/6CFmL1A.png)

----

- 另外我們可以加上 「-i」參數、查看header
`curl http://140.134.25.138:10002/ -i `
![](https://i.imgur.com/j7gLKlm.png)

---

![](https://i.imgur.com/feoKmE8.png)

----

![](https://i.imgur.com/wFBOC5s.png)

---

![](https://i.imgur.com/c2nKZxg.png)

----

- Robots.txt 
- 是一個給搜尋引擎的參考 
- 可以讓搜尋引擎不要搜集下列資料
- ![](https://i.imgur.com/WPclt72.png)
- http://140.134.25.138:10004/robots.txt
- 他說不能讓搜尋引擎看 我當然要看啊

----

![](https://i.imgur.com/KePMDIS.png)

---

![](https://i.imgur.com/tAMuilt.png)


----

- 大家用git時候
- git 會幫你建立「.git」資料夾
- 放commit紀錄
- ![](https://i.imgur.com/eMn35Ur.png)

----

- 在網頁上看到 Forbidden(403) 
- 通常都是 有這個資料夾
![](https://i.imgur.com/y781gfa.png)


----

- 現在新型態伺服器會把資料夾弄成404
- 使用 /.git/index 查看有沒有這個檔案

----

### 如果 「.git」大家都能讀取
- 造成 原始碼外洩

----

- 我們使用這個工具： https://github.com/BugScanTeam/GitHack
- 看到工具怎麼使用？
- 先安裝git
- `sudo apt install git` 
- 在git clone下載
- `git clone https://github.com/BugScanTeam/GitHack.git`

----

- 看到剛剛載的專案「GitHack」 cd 進去
![](https://i.imgur.com/fq7rqta.png)
![](https://i.imgur.com/f0D0rc4.png)


----

- Github上有使用說明
- ![](https://i.imgur.com/GxupUcR.png)

----

### 試試看
- 請使用Python2
- `python2 GitHack.py http://140.134.25.138:10005/.git/`


---

![](https://i.imgur.com/Ps7jUky.png)

---

![](https://i.imgur.com/X030UkW.png)


----

### cat 原始檔
- 在其他CTF 「git leak」和其他題目會混著用
- 叫你用gitleak拿程式碼在找漏洞之類 

- ![](https://i.imgur.com/y22zg3B.png)

---

![](https://i.imgur.com/h7rDAIY.png)


---

- 用同樣方 法自己試試看這個吧
- DS_Store 是 mac 會自動建立輔助系統的檔案
![](https://i.imgur.com/pJJ3vF1.png)
### 工具提示： DS_Store exploit

---

![](https://i.imgur.com/z4UP75f.png)

`python2 ds_store_exp.py 140.134.25.138:10006/.DS_Store`

---

![](https://i.imgur.com/iMBPyGW.png)


---

![](https://i.imgur.com/HYfsjIL.png)

----

- 開宗明義就跟你講
- 你要用 localhost (127.0.0.1)
- (ip位子)
![](https://i.imgur.com/uUiesO1.png)


----

### 記得一開始的requests header?
- X-Forwarded-For
- 把他放在requests header再丟出去就好拉
- 使用curl 或 python  或 chrome 插件

----

![](https://i.imgur.com/rs92Btd.png)

----

![](https://i.imgur.com/k7P1eEl.png)

