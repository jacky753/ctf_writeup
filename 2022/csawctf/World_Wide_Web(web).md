# World Wide Web
CTFリンク：https://ctf.csaw.io/
writeup参照リンク：https://yocchin.hatenablog.com/

http://web.chal.csaw.io:5010/stuff
にアクセスして，たくさん並んでいる単語のうちいくつかの単語にのみ<a href="/XXXXX">XXXXX</a>タグでハイパーリンクがつけられていることを開発者ツールで確認することまではできた．
手動で次々にハイパーリンクを踏んでいくものの，最終的に行きつく先は「Boooooooo!!」と表示されるページのみであった．

後日writeupをチェックすると，pythonスクリプトによって自動的に次々リンクを踏む方式を取っていた．

そのwriteupで使われているスクリプトを今後使えるようにしたいので，こちらに掲載しておく．

```
#!/usr/bin/env python3
import requests
import re

s = requests.Session()

url = 'http://web.chal.csaw.io:5010'
path = ''

while True:
    r = s.get(url + path)
    body = r.text

    pattern = '\<a href="(\/.+)"\>'
    m = re.search(pattern, body)
    if m is None:
        print(body)
        break
    path = m.group(1)
```

瞬時にアクセスしないと別のページに飛ばされるカラクリがあったのだろうか．．．

以上です．