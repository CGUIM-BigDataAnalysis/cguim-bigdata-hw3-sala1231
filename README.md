長庚大學 大數據分析方法 作業三
================

install.packages("rvest")
=========================

網站資料爬取
------------

``` r
library(rvest) ##第一次使用要先安裝 install.packages("rvest")
PTTJ1<-"https://www.ptt.cc/bbs/Tech_Job/index2571.html"
PTTJ2<-"https://www.ptt.cc/bbs/Tech_Job/index2572.html"
PTTJ3<-"https://www.ptt.cc/bbs/Tech_Job/index2573.html"
PTTJ4<-"https://www.ptt.cc/bbs/Tech_Job/index2574.html"
PTTJ5<-"https://www.ptt.cc/bbs/Tech_Job/index2575.html"

a<-c(PTTJ1, PTTJ2, PTTJ3, PTTJ4, PTTJ5)
PTTJALL<- NULL
for (n in a){
    PTT<-read_html(n)
    PTT_title <- PTT %>% html_nodes(".title") %>% html_text()
    PTT_PushNum <- PTT %>% html_nodes(".nrec") %>% html_text()
    PTT_author <- PTT %>% html_nodes(".author") %>% html_text()
    PTT_post <- data.frame(title = PTT_title, PushNum = PTT_PushNum, author = PTT_author)
    PTTJALL <- rbind(PTTJALL, PTT_post)
    
}
```

爬蟲結果呈現
------------

``` r
#install.packages("knitr")
#這是R Code Chunk
knitr::kable(PTTJALL) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| title                                                 | PushNum | author       |
|:------------------------------------------------------|:--------|:-------------|
| \[請益\] 請問應徵台積OP是否有黑名單                   | 37      | kn0105209    |
| \[新聞\] 郭台銘：陸大學生動手能力差                   | 21      | BBMADE       |
| Re: \[新聞\] 郭台銘：陸大學生動手能力差               |         | schizophrena |
| \[新聞\] 斥資600億 「綠能科學城」落腳台南沙崙         | 26      | hottea88310  |
| 滷肉開獎                                              | 57      | crafttt      |
| \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國          | 51      | popoallan    |
| Re: \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國      | 5       | appledavid   |
| \[新聞\] 台積電成環評箭靶　網友酸農地工廠卻就         | 31      | wahaha23     |
| Fw: \[新聞\] 新世代最崇拜企業家　郭董取代賈柏斯       | X4      | tw689        |
| \[請益\] 工作上想成長,想上點課程~                     | 7       | kevinZJL     |
| Re: \[心得\] 小公司的慎選...                          | 1       | Sex5F        |
| \[請益\] 研替or一般替代役                             | 34      | charisma007  |
| \[請益\] 達運光電(五股)                               |         | smst         |
| \[情報\] 106年03月22日\_竹科\_IC設計產業座談會        | 1       | SuperModel   |
| Re: \[請益\] 點序科技業務職面試請益                   | 2       | hueepf       |
| \[情報\] 整合深度學習的無人駕駛新創公司Drive.ai       | 5       | zxcvxx       |
| \[請益\] 慧盛先進科技？                               | 1       | amethystleaf |
| \[請益\] 3/11長春體檢                                 | 10      | elvisman     |
| \[新聞\] 績效獎金打6折？ 聯詠：不予回應               | 13      | PerfectID    |
| \[新聞\] 台積電 3 奈米赴美？關鍵在量子電腦            | 16      | evil7589     |
| \[請益\] 求職心力憔悴                                 | 66      | rko801024    |
| \[請益\] 代PO 交大半導體碩專班一問                    | 5       | remember246  |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭           | 13      | yolosiku     |
| \[面試\] 關於弘塑科技業務工程師                       | 2       | onlyveritas  |
| \[請益\] 自行保公會勞健保                             | 2       | ann3222      |
| \[面試\] 南科艾爾斯半導體                             | 5       | turtle6188   |
| \[新聞\] 謝金河：台積電打敗Intel！已是全球第一        | 11      | soaping      |
| Re: \[請益\] 水果公司的工廠，工程師好跳嗎？           | 7       | nomilkman    |
| Re: \[新聞\] 台積電 3 奈米赴美？關鍵在量子電腦        |         | pig2014      |
| \[聘書\] offer 機構 vs 半導體CSE                      | 5       | bboycookie   |
| \[請益\] 沒有中生代的公司                             | 9       | randomly     |
| \[請益\] 測試/系統整合/自動化工程師                   | 2       | foreverwhat  |
| Re: \[新聞\] 績效獎金打6折？ 聯詠：不予回應           | 3       | jeromeshih   |
| Re: \[請益\] 水果公司的工廠，工程師好跳嗎？           |         | typewindow   |
| Re: Fw: \[新聞\] 新世代最崇拜企業家　郭董取代賈柏斯   |         | jeromeshih   |
| \[心情\] 連來台灣的外國朋友都會講"台積電"華文         | 8       | terimakasih  |
| \[請益\] 獵人頭 網站 or APP                           | 16      | sustaned     |
| \[新聞\] 台積電赴美設廠？ 科技部轉述：並無此計        | 19      | TrueSpace    |
| \[請益\] 螃蟹OFFER請益(代PO)                          | 6       | birdhackor   |
| \[請益\] 以下加班申請定合理嗎?                        | 9       | zaxck        |
| Re: \[請益\] 獵人頭 網站 or APP                       | 8       | appledavid   |
| \[請益\] 半年的技術員經歷                             | 16      | ak080775     |
| \[請益\] 宏騰光電一些問題...                          | 3       | qqming0721   |
| Fw: \[徵才\] 興豪傳媒科技 誠徵Javascript前端工程師    | 1       | cliffk321    |
| \[請益\] 福爾摩莎紙業股份有限公司高雄業務             |         | edison81630  |
| \[聘書\] 研替offer請益(皮卡)                          | 5       | paulu90      |
| \[新聞\] 吞iPhone緯創資本支出破百億　3年新高          | 11      | qazxc1156892 |
| \[新聞\] 陳良基：與張忠謀溝通過「所有投資以台灣為優先 | 13      | wer11        |
| \[請益\] 竹科聯電製程                                 | 9       | berac16      |
| \[新聞\] 讀軍校免當軍人 中科院上班54K                 | 18      | tw689        |
| \[請益\] 日月光-歐美區(美國)客戶關係管理              | 12      | lim10337     |
| \[請益\] 南科住華科技                                 | 12      | kurtgod      |
| \[請益\] Nvidia的Android Framework/SW Engineer        | 16      | magic704226  |
| \[請益\] 亞德客or鑫陽鋼鐵                             | 6       | eraser90310  |
| \[請益\] 云辰科技                                     |         | Intelgence   |
| \[請益\] NXP Service Engineer                         | 7       | angelpeace   |
| \[情報\] 千竣科技違反勞基法，官司結果                 | 50      | GameHeven    |
| \[新聞\] 台積電試產 7 奈米良率超過七成                | 43      | unrest       |
| \[請益\] offer選擇                                    | 7       | queenghost   |
| \[討論\] 公司要資遣人，需要通報勞工局嗎？             | 12      | JE2K         |
| \[新聞\] 新日光虧損破紀錄 去年財報淨損63.1億          | 17      | moonth66     |
| \[新聞\] 竹科IC產業衰退？ 科管局：研發力道仍強        | 8       | breath35     |
| \[請益\] 走品質的有可能年薪破百嗎?                    | 21      | DUFA         |
| \[討論\] 板上有人遇過這種情況嗎                       | 4       | forgetwhat   |
| \[請益\] 在台灣只剩下一年 該換工作嗎?                 | 9       | kissyourbi   |
| \[情報\] (代po)科技人面試求職講座                     | 6       | yunnnn       |
| Re: \[請益\]信鼎技術 面試前準備?                      | 7       | AlioAlio     |
| Re: \[新聞\] 斥資600億 「綠能科學城」落腳台南沙崙     | 13      | juangpeiyi   |
| \[請益\] offer 選擇                                   | 6       | eclipse911   |
| \[討論\] 系統廠的生命力是否比較強？                   | 8       | join183club  |
| \[請益\] 有人聽過Sogeti這間公司嗎                     | 1       | takeon       |
| \[請益\] offer 選擇                                   | 1       | chrishyper   |
| \[新聞\] 「中國製造2025」美憂威脅國安                 | 12      | AAAB         |
| \[請益\] 菱X科技                                      | 10      | maxgxking    |
| \[新聞\] 環評空污缺電 黃士修：台積電快走吧!           | 31      | wahaha23     |
| \[請益\] htc派遣問題                                  |         | seal44       |
| \[新聞\] 傳蔡力行 跳槽聯發科(已公告)                  | 53      | http405      |
| Re: \[新聞\] 傳蔡力行 跳槽聯發科                      | 10      | jeromeshih   |
| \[新聞\] 聯發科宣布 蔡力行接共同執行長、集團副        | 72      | RTA          |
| Re: \[請益\] Nvidia的Android Framework/SW Engineer    | 5       | nixt         |
| \[請益\] 敏實集團 minth group                         | 1       | urocissa     |
| \[聘書\] 研替offer詢問(QNAP/緯創)                     | 5       | lebron0426   |
| Re: \[新聞\] 傳蔡力行 跳槽聯發科(已公告)              | 15      | TSMCer       |
| \[請益\] 友達 美光 力晶 哪家最推薦去呢?               | 45      | okopp        |
| \[請益\] 面試請益                                     | 3       | lhx63524     |
| 資料探勘及資料分析的基本能力為何                      |         | uasalada     |
| \[請益\] 元隆電子                                     | 2       | zyxcba5      |
| \[請益\] FAE面試請益                                  | 30      | lovelyjojo   |
| Re: \[新聞\] 聯發科宣布 蔡力行接共同執行長、集團副    | 14      | a875979      |
| \[請益\] 晶電 vs 鼎元 (竹南)                          | 9       | kkkmaxtine   |
| \[請益\] gg設備幹到頂天有機會被高薪挖角嗎             | 4       | onlytiger    |
| \[討論\] 新人離職                                     | 75      | forgood      |
| \[請益\]男生做友達OP 適合待到退休嗎?                  | 19      | Silent       |
| \[討論\] 陣亡率高/免洗的職位                          | 25      | NTUlosers    |
| \[討論\] 科技業公司一虧損就開始拆子公司是常態嗎       | 14      | gotptt       |
| \[徵才\] Taylormade Golf company (高雄辦公室)         |         | loddy        |
| \[討論\] 台積電有可能成為百年企業嗎 ?                 | 9       | goodpoint    |
| \[請益\]華新科福利                                    | 4       | ichior       |
| \[請益\] 緯創server部門好嗎?                          | 8       | fantacy0225  |
| \[請益\] 尋求找工作方向建議                           | 2       | YWEC         |

解釋爬蟲結果
------------

``` r
#這是R Code Chunk
dim(PTTJALL)
```

    ## [1] 100   3

共爬出100篇文章標題(這100筆包含標題、推文數、及作者)

``` r
#這是R Code Chunk
table(PTTJALL$author)
```

    ## 
    ## amethystleaf   appledavid       BBMADE  charisma007      crafttt 
    ##            1            2            1            1            1 
    ##     elvisman     evil7589  hottea88310       hueepf     kevinZJL 
    ##            1            1            1            1            1 
    ##    kn0105209    PerfectID    popoallan schizophrena        Sex5F 
    ##            1            1            1            1            1 
    ##         smst   SuperModel        tw689     wahaha23       zxcvxx 
    ##            1            1            2            2            1 
    ##      ann3222   bboycookie   birdhackor  foreverwhat   jeromeshih 
    ##            1            1            1            1            3 
    ##    nomilkman  onlyveritas      pig2014     randomly  remember246 
    ##            1            1            1            1            1 
    ##    rko801024      soaping     sustaned  terimakasih    TrueSpace 
    ##            1            1            1            1            1 
    ##   turtle6188   typewindow     yolosiku        zaxck     ak080775 
    ##            1            1            1            1            1 
    ##   angelpeace      berac16    cliffk321  edison81630  eraser90310 
    ##            1            1            1            1            1 
    ##    GameHeven   Intelgence         JE2K      kurtgod     lim10337 
    ##            1            1            1            1            1 
    ##  magic704226      paulu90 qazxc1156892   qqming0721   queenghost 
    ##            1            1            1            1            1 
    ##       unrest        wer11         AAAB     AlioAlio     breath35 
    ##            1            1            1            1            1 
    ##   chrishyper         DUFA   eclipse911   forgetwhat      http405 
    ##            1            1            1            1            1 
    ##  join183club   juangpeiyi   kissyourbi    maxgxking     moonth66 
    ##            1            1            1            1            1 
    ##         nixt          RTA       seal44       takeon       yunnnn 
    ##            1            1            1            1            1 
    ##      a875979  fantacy0225      forgood    goodpoint       gotptt 
    ##            1            1            1            1            1 
    ##       ichior   kkkmaxtine   lebron0426     lhx63524        loddy 
    ##            1            1            1            1            1 
    ##   lovelyjojo    NTUlosers        okopp    onlytiger       Silent 
    ##            1            1            1            1            1 
    ##       TSMCer     uasalada     urocissa         YWEC      zyxcba5 
    ##            1            1            1            1            1

由table可以看出這100筆PO文的作者以及他們的PO文數， 其中最多的是magic704226，其PO文數為3篇，其他作者幾乎都只有貼一篇文。

抓下來的100筆大多數都是問問題的文章，更多的是回覆他人的貼文，多數的作者 都沒有重複貼文，只有少數的作者會貼到兩篇或三篇文，作者重複貼文的人數不多。
