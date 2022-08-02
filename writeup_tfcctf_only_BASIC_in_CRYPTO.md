# writeup for tfcctf about BASIC in CRYPTO

## BASIC in CRYPTO
「CTF 暗号」とググって，

https://rightcode.co.jp/blog/information-technology/becoming-security-engineer-solving-ctf-q6-q14

にはよく出る暗号方式として次の3つを上げている．

```
1. シーザー暗号
2. 進数の変換
3. base64
```

今回の暗号文は
```
"/Rn/X7n#bUc.rjzh,|eEsg,?&QI;@^ARm}UKOkICi#X.ixEmN]D"
```
このように記号が入り乱れているため，シーザー暗号ではないと判断した．

base64の場合は数字とアルファベットだけなので，文字の並びの雰囲気は同じだが違うと判断した．

「CTF 暗号 見分け方」でググると，

https://raintrees.net/projects/a-painter-and-a-black-cat/wiki/CTF_Crypto

このサイトに様々な暗号がまとめられており，「Base N encoding」というようにBase64以外にも様々なBaseN系の暗号があることが分かる．

そして，Base85, 91, 94, 95は数字とアルファベットに加えて記号(!#$%&()\*+....)も使うので，今回の暗号化に使われていそうだと判断した．

まず，Base85を次のリンクのように試したが，Base85が対応していない文字列が暗号文に入っているようで複合できずにエラーメッセージが出る．

https://hi120ki.github.io/blog/posts/20190129/

次に，Base91を「Base91 python」とググって，

https://github.com/aberaud/base91-python

のプログラムをgit cloneしてダウンロードした．

ダウンロードした同じディレクトリにpythonファイルを作成して次のコードを実行した．

filename='decode_base91.py'
```
import base91
base91.decode("/Rn/X7n#bUc.rjzh,|eEsg,?&QI;@^ARm}UKOkICi#X.ixEmN]D") 
```
```
python decode_base91.py
```

これで何故かgit cloneしたプログラム内に起因するerrorが出てきたので，

https://pypi.org/project/base91/

ここにあるように，

```
pip install base91
```
こっちのbase91モジュールもインストールした．

その上で再実行したところflagが出た．

```
TFCCTF{sh3's_4_10..._but_0n_th3_ph_sc4l3}
```

以上となります．
