<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
 MathJax.Hub.Config({
 tex2jax: {
 inlineMath: [['$', '$'] ],
 displayMath: [ ['$$','$$'], ["\\[","\\]"] ]
 }
 });
</script>
# nazotoki_ctf_writeup_y0sh1wara
開催URL
https://ctf.nazotoki.tech/

## 今回CTFの感想
 馴染みのある誕生日と対応した黄道12星座を辿っていく冒険感があってとてもエキサイティングでした．(ゾディアック事件を彷彿させる．)
参加人数が多いのか，それともへびつかい座問題でDDOS攻撃をする方がいらしたのかでサーバが落ちて大変そうだなと思いました．
普段なぞ解きをしないので，ヒントを見まくって分かったときの驚きは尋常では無かったです笑．
CTFの基礎も学べてとっても楽しかったです．ありがとうございました！
<br>
CTFとなぞ解きって相性いいのかなっとも思いました．


## Tutorial
`nazotokiCTF{ナゾトキ}` <br>
の `ナゾトキ` をSubmitする．

> フラグは必ず 意味のあるカタカナ4文字の単語 ですが、脈絡があるとは限りません。なぜわざわざフラグが4文字縛りなのか？なぜこの単語なのか？本当の意味はあとで気付くことになるかもしれません。

これは，問題"Last Challenge"で意味が分かる．


## Knowledge - Earth elements
### おうし座 (12)
問題文：
> 2021年に行われた、コンピューターウイルス「emotet」のテイクダウン作戦の名前を日本語で言うと？「○○○○ムシ作戦」

解答：<br>
`テントウ` をSubmitする．<br>
「〇〇〇〇ムシ」といったら天道虫くらいが思い付いたので提出したらクリアした．<br>

Operation LadyBird（てんとう虫作戦）によってウクライナでEmotet を操っていたハッカーの活動拠点に警察が突入捜査を行ったそうだ．
https://www.asahi.com/articles/ASP2S32BDP2QULZU01C.html

補足：
これにより，command＆controlサーバ(C＆Cサーバあるいは，C2サーバ)を壊滅することで，攻撃者がEmotetを操作できないようにした．
https://xtech.nikkei.com/atcl/nxt/column/18/00676/030500073/


Emotet はマルウェアの一種であるボットであり，行政や取引先になりすました不正なメールに添付されたファイル（マクロを実行できるWordやExcelファイル）において「コンテンツの有効化」を行うことで，C2サーバからの命令を実行するようになり，認証情報やネットワーク内の機密情報が外部へ流出し，他の端末に感染した後（自己増殖するワームの性質も持つ．），データが暗号化されること（さらに身代金を要求するランサムウェアに感染させる「トロイの木馬」として機能する．）もあるようです．
https://www.softbank.jp/biz/blog/business/articles/202202/emotet/

対策には，DNSセキュリティやセキュアWebゲートウェイなどがある．
https://www.nttpc.co.jp/column/security/emotet.html


### おとめ座(22)
問題文：
> Webアプリケーションのセキュリティ分野の研究・ガイドラインの作成・脆弱性診断ツールの開発・イベント開催などの活動をしているオープンソースソフトウェアコミュニティの名称の読み方をカタカナ4文字で答えよ。

解答：
分からなかったので「Webアプリケーションのセキュリティ分野の研究・ガイドラインの作成・脆弱性診断ツールの開発・イベント開催などの活動をしているオープンソースソフトウェアコミュニティの名称の読み方をカタカナ4文字で答えよ。」でググった．<br>
OWASPというセキュリティ研究集団は見たことがあったので，`オワスプ`とSubmitした．

補足：
OWASP（Open Web Application Security Project）はOWASP ZAPというWebアプリケーション脆弱性診断ツールや，OWASP Juice ShopとOWASP BWA(The Broken Web Applications)といった脆弱性検査練習用のWebアプリケーションを提供している．
https://www.itmanage.co.jp/column/about-owasp/
OWASP Top 10として，Webアプリケーション向けTop10リスクも公開している．

### やぎ座(32)
問題文：<br>
> ある数 x を数 b のべき乗bᵖとして表した場合のpのこと。logとも呼ばれるこの数を日本語で何というか？カタカナ4文字で答えよ。

解答：
logといえば，`タイスウ`なのでSubmitした．

補足：
「対数」(wikipedia)によれば，
```対数（たいすう、英: logarithm）とは、ある数 x を数 b の冪乗 b^p として表した場合の冪指数 p である。
この p は「底を b とする x の対数（英: logarithm of x to base b; base b logarithm of x）」と呼ばれ、通常は log_b (x)と書き表される。```
つまり，$$x = b^p \iff log_b x = p log_b b = p$$である． 
https://ja.wikipedia.org/wiki/%E5%AF%BE%E6%95%B0




## Riddle - Fire elements
Riddleとは，ゲルマン語源の「なぞなぞ，不可解なもの」という意味．
https://kotobank.jp/word/riddle-1245112<br>
ハリーポッターの"例のあの人"の本名でもある．
https://kotobank.jp/word/%E3%83%B4%E3%82%A9%E3%83%AB%E3%83%87%E3%83%A2%E3%83%BC%E3%83%88-1732832

### おひつじ座(11)
問題文：<br>
> あなたが目指しているものの間を読め

解答：<br>
Hint 1
> プロローグをよく読んでね
目指しているものとは．
セキュリティエンジニア？
採用されたい？
スーパーハッカー？
スーパースター枠？
「「セキュリティ業界の星に、俺はなる！！」」？

Hint 2
> あなたが目指してるものは「セキュリティ業界の星」 つまり…「★」 どこかにマークがなかったでしょうか？テキストとは限りませんよ？
「「★」マークはテキストとは限りません」とのことから，クリックするとai-intro.pngとしてダウンロードできる画像に「★」マークを上下に確認した．
主人公の高橋ピヨ彦くんは「セキュリティ業界の星「★」」を目指しているので，その上下「★」マーク直線上にある文字を読むと`ハン ド          ル`とある．<br>
`ハンドル`をSubmitした．

補足：
これは2番目につまずいた．よくできたナゾトキ問題でした！

### しし座(21)
問題文：
> ルールを守れ
とともに，
https://ctf.nazotoki.tech/files/eda8b00c4d8687aa83985a5c8273592a/leo.png
カタカナが散りばめられた画像が掲載されていた．
leo.pngとしてダウンロードできた．

解答：
hint 1
> ルールを最後までよく読んでね
たしかに，ルール記載の「大切なルール」に「・燃えるゴミは捨ててください，・ペットボトル」とあり，不自然に感じた．

hint 2
> 大切なルールに書かれていることを実行してみよう ・「モエルゴミ」は捨ててください・「ペットボ」とる

「モエルゴミ」と「ペットボ」を取り除くと，`チーター`が残るのでSubmitした．

### いて座(31)
Hint 1<br>
> 身の回りで4つ種類があるものと言えば？

Hint 2<br>
> 地図とかで見かけます

Hint 3
```
方角の読み方をカタカナで当てはめてみると…？
○○○○＝トウ
ウエスト＝ザイ
サウス　＝ナン
ノース　＝ボク
```

ということで，`イースト`をSubmitした．


## Web - Air elements
### ふたご座(13)
問題：<br>
> Webサイトにアクセスしフラグを探せ
https://gemini.ctf.nazotoki.tech/

解答：<br>
```
Gemini
パスワードは dioskouroi って分かってるはずなんだけど…
```
とWebページに書かれていて，
`Dummy Password SUBMIT`
という見た目の入力フォームがあった．

Hint 1<br>
`パスワードは嘘じゃないみたいです。WEBページのソースを見てみましょう。`

Hint 2<br>
```35行目の <input type="hidden" name="realPassword" value="dummyPassword">
でdummyPasswordという文字列が強制的に入力されているようです。これをdioskouroiに書き換えることができれば良さそうです。
やりかたがわからなければ「開発者ツール html 書き換え」とかでぐぐるといいかもしれません。
```

指示通りググって，htmlを上記のように編集して，`nazotokiCTF{ナイーブ}`を確認した．
`ナイーブ`をSubmitした．

補足：<br>
「Google Chromeデベロッパーツールの使い方」
セレクトモードでページ内の編集したい箇所をクリックして，デベロッパーツール内のElementsパネルで編集したいスクリプトを右クリックして，Edit as HTML(HTMLを編集する)をクリックして編集する．
https://willcloud.jp/knowhow/dev-tools-01/

dioskouroiとは「ゼウスの息子」という意味で，ふたご座の名前の由来になった．
https://ja.wikipedia.org/wiki/%E3%83%87%E3%82%A3%E3%82%AA%E3%82%B9%E3%82%AF%E3%83%BC%E3%83%AD%E3%82%A4



### てんびん座(23)
問題：<br>
> Webサイトにアクセスしフラグを探せ
https://libra.ctf.nazotoki.tech/

```
Libra
リクエストヘッダー情報
フラグはstardustChromeという特殊なブラウザでしか閲覧できません。
```
とWebページに書かれていた．

解答：<br>
Hint 1<br>
> stardustChromeという特殊なブラウザで閲覧する必要がありそうです。でもそんなものは持っていないですよね。 使っているブラウザを偽装することはできないでしょうか？

Hint 2<br>
```
使っているブラウザを示すヘッダー情報はuser-agentの中にあります。ここの情報をstardustChromeに変更できれば良さそうです。
やり方は「User-Agent　偽装」とかでググるといいかもしれません。
```

指示通りググって，user-agentをstardustChromeに変更すると，`nazotokiCTF{クローン}`が出てきた．
`クローン`をSubmitした．

補足：<br>
user-agentの変更方法は次のようである．<br>
「ChromeでUA偽装するには？ユーザーエージェント（useragent）変更方法を解説！スマホ/ガラケ/IE」<br>
デベロッパーツールツールを開いて，右側のメニューをクリックして，More toolsを選択し，Network conditionsをクリックする．
User Agentの項目で，Select automaticallyのチェックを外して，Customを選択して，`stardustChrome`を入力して，Webページを更新した．<br>
https://aprico-media.com/posts/1579

### みずがめ座(33)
問題：<br>
> Webサイトにアクセスしフラグを探せ
https://aquarius.ctf.nazotoki.tech/


解答：<br>
リンク先のWebページにはよく見るログインページが表示された．
社員ナンバーとパスワードを入力してくださいとある．

Hint 1<br>
```
passwordを入力することで指定した社員情報を閲覧できます
と書かれています。 スターダストセキュリティの社員の中で、一人だけ社員ナンバーを知っている人がいませんか？ その人の社員ナンバーを使って、「password」と入力すれば検索ができそうです。
```

プロローグに，
`社員ナンバー99．stardust inc. 採用担当AIの「アイ」デス．`
とあるので，社員ナンバーに「99」と入力して，パスワードに「password」と入力する．

すると，アイさんの社員情報が出てきて，attribute メモに以下のメッセージが確認できた．
`フラグのヒントはナンバー9999に載せておいたよ！入社前情報だから普通のパスワードでは見れないかもね。`

Hint 2<br>
```
アイちゃんの情報は検索できましたか？ メモ欄にフラグのヒントが載っていますね。
検索すべき社員ナンバーがわかりましたが、普通のパスワードでは検索できないようです。 どうやらパスワード入力欄に脆弱性がありそうですが…
```

Hint 3<br>
```
パスワード入力フォームにSQLインジェクションの脆弱性があります
社員ナンバー：9999 か 99
パスワード：' or 1=1 ;
と入力してみてください。この人は誰でしょうか？名前がわからなかったらプロローグに戻るといいかもしれません。
```

ということで，社員ナンバーに「9999」，パスワードに「' or 1=1 ;」を入力すると，社員ナンバー9999の社員情報が出てきて，attribute メモに以下のメッセージが確認できた．<br>
`メモ	nazotokiCTF{この候補者の苗字}`

プロローグより，主人公の苗字は高橋なので，`タカハシ`をSubmitした．

補足：<br>
アプリケーションに渡されるパラメータにSQL文を直接指定すると，攻撃者が入力したSQL分が実行されてしまう．
「' or 1=1;」によって，or を使うと，1=1が成り立っているので，「'」より左に書かれているものが何であれ，SQL文が実行されて，全ユーザー情報が漏洩する．
```python:pythonによる比喩
if user == 'taro' or 1==1:
	print("Hello, world!")
```
が実行されるのと同じ．
https://www.shadan-kun.com/waf/sql_injection/


## Misc - Water elements
### かに座(14)
問題：<br>
> 仲間はずれを探せ
cancer.zip がダウンロードできた．

解答：<br>
私ではなくMsYさんが解いたのでざっくり記載する．
```
4de447a391e32baeb5a52c55aa14467b
7c70e2cb2b4a13c4590f6b15c30385fd
44ca0844398b2d010d8cd4a31ddb023d
397cbf6db9d7ae6906ae420aedc5346c
550eadb88a230018bf043d1b6ad15863
635cbc8a5dc1a528c3b5cb9eecdc1086
766cc4dd4d5005652e8514e3513683f8
0961db32a59b8a83c1996498f9d1d80e
7463543d784aa59ca86359a50ef58c8e
a0678bcea04dbd6852c219062ab2bb3c
b9c94e8a87e3647c5a0fa4ff358ecc65
f8a5c386478fa64f118056b82acc31d2
f0525aafa095ed2665d03681537a70ea
```
zipファイルを解凍（展開）すると13個のファイルが確認できた．
なかでも，他はpcapファイルだったが，f0525aafa095ed2665d03681537a70eaだけはUTF-8ファイルだったのでテキストエディタで開くと，
`nazotokiCTF{イイワケ}`
と，最終行に書かれていたので，`イイワケ`とSubmitした．


### さそり座(24)
問題：<br>
`世界一かわいいうちの犬を紹介します`
ミニチュアダックスフンドの画像が掲載されていた．
scorpio.jpgとしてダウンロード出来た．

解答：<br>
私ではなくMsYさんが解いたのでざっくり記載する．
Hint 1
`世界一かわいい犬なのでよく見てください`
拡大してよく見ると，ダックスフンドの両目に反射して映った`カクダイ`という文字が確認できたのでSubmitした．

### うお座(34)
問題：<br>
> みずがめ座からてんびん座に向かうとき、ひみつの鍵が手に入るだろう。水の中に浮かぶ真実を見定めよ。
password.encとencrypt-pisces-new.zipというファイルがダウンロード出来た．
中身は次のようである．
```password.enc
0fb3 8c03 8755 5108 4928 4ce1 447d a628
7116 e23a adce 5108 084d 6feb 9da0 b07c
654c 948b 443d bca2 b3b6 c97e 2b51 275b
450d cec0 31fb 581a 961a f7d6 7de0 d5cc
0027 a9d0 1297 372e 95bd 0f43 0341 eed6
7684 26c8 4e79 c5e4 dcf5 612d 7288 9906
cf9d ef91 4876 c601 a1ce 8b23 7edb 1cc9
37fc 71ba cda5 c96e 7452 65fc 3632 3baa
4e28 af2b 2b8e d1d8 7235 4333 7eb8 6854
8cd6 e05b a3d5 24b8 5fda 3a59 eb16 5b0e
5da4 f9b5 7515 dfdc d654 0ba8 c208 33d4
0519 8881 8cec 1d10 f6fa 7f6c 298d d505
6fb9 e6f2 7700 480a 743d 0469 505e 7ed5
7878 aa47 8762 b382 7dfc 23b4 28cb 65d6
35c4 40db 8972 747a 56dd a9f2 9847 1ed7
4bd8 916a ad24 db8a 368e f74e bd43 ee75
```
encrypt-pisces-new.zipにはpisces.jpgという画像ファイルがあったが，パスワードがないと開けない．

解答：<br>
Hint 1<br>
> みずがめ座からてんびん座に向かうとき…ヘッダー情報に記録されるものはなんでしょうか？

Hint 2<br>
```
どうやらリファラーの情報にaquariusが含まれた状態でてんびん座のサイトにアクセスすると鍵が手に入りそうです。書き換えられないでしょうか？
やり方がわからない人は「リファラー　書き換え」とかでぐぐると良いかもしれません。
```
「リファラー 書き換え」でググると，Chromeでリファラを指定するプラグイン「Referer Control」の説明が出てくるので，ダウンロードして使う．
site filter のenter site にhttps://libra.ctf.nazotoki.tech/ と入力し，Customにhttp://aquarius.libra.ctf.nazotoki.tech/ と入力して，https://libra.ctf.nazotoki.tech/ にアクセスする．
すると，次のようにRSA PRIVATE KEYが表示された．

```
遠いところをよくおいでくださいました。ひみつの鍵を差し上げます。
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAunVG5a8SbXgsayNWhd4f9FYsWb8z57P2Ql8Yq+fQgq0Y2xcH
/HgHO0vZrgSbjFLxnpx4D9arOtvGdn06GLZcL3eU32jPvqVh8QhqmaQ8bdUDlEp8
yt45DMoleYflw8c9q2dDsRjLUoE2qhtMm2xR8B9U+mRq+vVgEJdvNMgmn+XtsmRx
A41n3nHTfTcOznZaNRxyAqZjooDOuUoVBStJVUqbd4a3EzMCBbdAzyQ2VdQEigT0
PVstPiMI0draaO9oKlZkfuGkJJ3Ftn8+A4cjIG8ycihsGqfEMSVUpLmUI+Etb0+C
3iD+B7P25v0CDNdD2odWIRipjdE8TmuTA+AsuQIDAQABAoIBAQCBCSw5Q4EzNNk4
g8oa9m+SvhgPO90F2mrv37PJM7H+3R+4byXduIr4pDNO1G15HOWNaKdF/r+dCf88
fMk51OnTB6SFP5mVTAqNrc9n6FrRf3rsoufd1RASI8rvYfbGGBo7hkk4Q/phbH6S
FjZb0QibbnN2nQvUBP+oO8R/+IuSV3NgxvtQ3CggRnqTiwx99kHO3gEXJVHozq09
mceaWIQeT6jAf5nMsNKl2YlBxomMkeXZ8jEcCJQcAPuHJjZ2SJmLpbADIffg/c95
oaLejnoEWUflnN/QPw7shHE2F50uKyEYAh5uNCjVHRQE15jUOQZBr5aLMtpyCkfJ
3bPrzFcBAoGBAOyEMyBBwAh2Kuk+QS9OCsFcxjTQPV/jkHnk2nU8I7xrO0MqONOL
/ily+GcbTrY4bx8zkIKuYwEAp/5Mybd+C/kRsjeSGZVrNxNDNG32JYTn49Z1miKv
jNMGUJsfOoKI6G1gKnI3j5WlP2E+xXtQkJUMwqj5vdafCTVJhWrucFyxAoGBAMnR
ave7rOChNxVEoS7YmwMUSEk/PlM4MLkv7WkOPdNATxZ2u5fj8RrHfI4pGt//QXUX
pI0dE6Y8ndM24YhynvqGYr8cyygBj+BpMZFXSFmf2ozRTawFbo2IgqqsZ6AszQVb
EUuq5k5mx5Mg+ilMMzTmxjL4AD5GRy/2ofYK5DKJAoGACdhW6HjULYX9s0fMHtP4
zqO1/GzOoTcvxGMqVMb0FdvA08LmKqghJEiM3n3cgOlIdtwGn+nyZRBJ7eP0YZb1
mKCL8pQ6TGXyHPMnM4yTczzT1xF+IQN9sSsKH+rk3JomUqc2HRsC9w+x27JpNgDc
g9fMIoyCwnRMRdORoinas4ECgYAausnYFdtHxRJulrBia/3b4ovQZ7fxfbe2T0q6
Z1B48kOHTiJ6c44zZchxa7BLips4zvDUX82CbvTYTKSCVewIclQRy9Z8bfiIWGZg
QZcrh6iCjhYjenSx+iqUQFFZPZXJ583an7/xElvMeMmpPpZpo0cM6RvfI5+6EohQ
9hBTQQKBgQCBiu+qiElJXJUTrwr3XESHUEsCPz27VWViYlj/n6GsY80QSf4Y1F0d
ynDDCJ4zE0FL1WfFFGMqaE86wvQZwvv9NCqSkpxhfbYhf/lKUmyNIyqoQYkV7kAK
NjQ0gdNlw4NLioSXny6/0k5G4OIzwh8QNf38sZGKhm7FMVQ4G8r1Yw==
-----END RSA PRIVATE KEY-----
```

これで，秘密鍵と公開鍵（password.encより）が揃ったので，
http://ctf.publog.jp/tag/Crypto
を参考にパスワードを復元する．

encrypt-pisces-new.zipファイルを解凍して，画像pisces.jpgを確認した．

Hint 4<br>
```
そろそろ目が疲れてきたころかと思って涼し気な画像をご用意しました。ちょっと休憩してぼんやり眺めてみてはいかがでしょうか。
もしあなたが若者なら、年上の人に見せてみるとピンとくる人がいるかもしれません。
```

プールの水面を撮影したようなpisces.jpgだが．．．両目立体視，立体写真とも呼ばれ，「交差法」（2枚並べて寄り目で見る）または「並行法」（2枚並べて見る）という見方で見ると文字が浮かび上がる．
https://www.stereoeye.jp/howto/cross.html
https://www.stereoeye.jp/howto/parallel.html


しかし，難しいので，ステガノグラフィーツールによって文字を復元出来るようだ．
```
wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar
java -jar stegsolve.jar
```

すると，`ケッパク`と見える画像をずらすポイントがあるので，Submitした．



## 2nd Challenge
### へびつかい座(100)
問題文：
```
最終問題に進むためのフラグを導く魔法の解答用紙をご用意しました（謎解きによくあるやつ）
※使い方のヒント
PDF版とPNG版を用意してますが内容は一緒です
印刷できる環境がある方は印刷するといいかも
PDF版は文字入力ができるようになってます
お使いのIMEによるかもしれませんがカタカナ入力よりひらがな入力のほうがやりやすいかも（どっちでも大丈夫です）
tabキーで次の入力欄に移動できるようになってます
あとで提出が必要になったりするとかではないので最悪使わなくても大丈夫です
ただし、用紙の様式はよくみておいたほうが良さそうです
```

answersheet.pdf がダウンロード出来た．
1 ~ 12 の数字が書かれており，その隣に4文字文の空欄が書かれていた．
1文字目が囲まれていた．

解答：
この問題は私ではなくMsYさんが解いたのでざっくりとした解答です．
プロローグに黄道１２星座が数字とセットで記載されていたので，これまで解いてきた問題のFlag(解答)をanswersheet.pdfの数字の横に入力していった．
```
1, おひつじ座：	ハンドル
2,  おうし座：	テントウ
3, ふたご座：	ナイーブ
4, かに座：		イイワケ
5, しし座：		チーター
6, おとめ座：	オワスプ
7, てんびん座：	クローン
8, さそり座：	カクダイ
9, いて座：		イースト
10, やぎ座：	タイスウ
11, みずがめ座：	タカハシ
12, うお座：	ケッパク
```
強調されている1文字目を取り出すと，「ハテナイチオクカイタタケ」とある．<br>
よって，DDOS攻撃のようにWebページ左上の?アイコンを1億回クリック（アクセス）する方法を取ろうとした方もいらっしゃるでしょうが，1億回は競技時間以内にアクセスできないことや，サーバーダウンの原因になるので違う方法を考える．
答えとしてはcache（キャッシュ）を書き換えて1億回以上アクセスしたことにするらしいです．
すると，`nazotokiCTF{ポラリス}`と出て，`ポラリス`をSubmitした．

## Last Challenge
### 最終問題(200)
問題文：<br>
> パスワードを解け
https://polaris.ctf.nazotoki.tech/

Webページには，
```
Last Challenge
パスワードのヒントは愛の星座の中
流れに従い
太陽と月に背いて心の示す方を読め
```
と記載があり，
Password入力欄があった．

解答：<br>
「パスワードのヒントは愛の星座の中」とあるので，問題みずがめ座でアイさんは7月18日生まれでかに座と分かるので，問題かに座のファイルたちを確認した．
かに座のファイルたちはpcapファイルだったのでWiresharkで中身を見た．どうやらFTP通信しているようで，Protocolカラムを見るとFTP-DATAのやり取りをしているところがあるので，FTP Data(1009 bytes data)を右クリックしてShow Packet Bytesを選択すると画像を確認した．
すると，pcapファイルごとにさそり座やおひつじ座．．．などが見られる．
さらに，Next sequence numberとAcknowledgment numberによってファイルの順序が分かるので，12個の星座画像をFTP-DATAで取得しているpcapファイルたちを並べて，1つのファイルに統合しました．
その統合された星座の順番は次のようになり，これまでのFlag達も並べた．

```
うお座: 		ケッパク
やぎ座:		タイスウ
かに座:		イイワケ
てんびん座:	クローン
おひつじ座:	ハンドル
みずがめ座:	タカハシ
おとめ座:		オワスプ
しし座:		チーター
ふたご座:		ナイーブ
さそり座:		カクダイ
いて座:		イースト
おうし座:		テントウ
```
最初は頭文字を読んでさっぱり意味が分からなかったが，「太陽と月に背いて」ということと，へびつかい座のanswersheet.pdfの上に太陽，下に月のアイコンを結ぶ直線上にはない，つまり頭文字以外の文字を縦に読むと，「パスワードハスターダスト」と「心の示す方」に叶うような読み方が見つかった．
だから，これら4文字だったのね～っと意味が通る．
よって，`stardust`とパスワード欄に入力すると，クリア画面が表示された．
そこには，`nazotokiCTF{オールト}`と書かれていた．
`オールト`をSubmitした．

補足：
この問題はCTFもナゾトキもうまく組み合わさって一番難しい問題だったのではないでしょうか．面白い問題です！

RETR FTP commandとは，接続先サーバからファイルを取得するcommandです．
https://www.serv-u.com/resource/tutorial/appe-stor-stou-retr-list-mlsd-mlst-ftp-command

pcapファイルの分割・結合<br>
commandでもhttps://giugno.hatenadiary.org/entry/20110914/1315983399<br>
ドラッグ＆ドロップでも出来る．
https://sugarsugar.conf.jp/wireshark%E3%81%A7%E3%81%AE%E3%82%AD%E3%83%A3%E3%83%97%E3%83%81%E3%83%A3%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%AE%E3%83%9E%E3%83%BC%E3%82%B8%E6%96%B9%E6%B3%95<br>

## Congratulations!!
### Thank you(201)
アンケートを答えたらFlagが表示された．
`nazotokiCTF{アリガト}`<br>
`アリガト`をSubmitした．

因みに，
```
curl https://docs.google.com/forms/d/e/1FAIpQLSfRQck97eWMf3YFLLzhAF14kpyLODVZC2eGCIvhr2xero2dgA/viewform | grep CTF
```
でも確かめられる．
































