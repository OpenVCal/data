# CONTRIBUTING

## Twitterの数値IDを探す方法

以下JavaScriptを開発者ツールやブックマークレットから実行。なお、このスニペットはWTFPLとして放棄可能な権利を不可逆的に放棄し、利用によっては各国によって定められる法律が要求する制約以外は何ら課さない。

```javascript
alert(JSON.parse(document.evaluate(`/html/head/script[@type="application/ld+json"]`, document, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null).singleNodeValue.innerText).author.identifier)
```

### 解説
なぜかTwitterはLD-JSONのデータを動的に生成して`<head>`タグ以下にぶら下げるため、ページが完全にロードされた頃合いで適当に叩いてやるとうまいこと取れる。
