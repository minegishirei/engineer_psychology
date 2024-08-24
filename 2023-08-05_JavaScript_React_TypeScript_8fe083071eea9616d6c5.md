<!--
title:   🍛🍛🍛🍛🍛APIはカレーでラッピングするが吉🍛🍛🍛🍛🍛
tags:    JavaScript,React,TypeScript,カリー化,関数型プログラミング
id:      8fe083071eea9616d6c5
private: false
-->
例えばAPIを呼び出す関数を書くとき。
以下のように感じに書くこともできます。

```js
const base_url = "https://example.com"
const async callAPI = (endpoint="normal",count=10, q="Excel") => {
  const url = `${base_url}/${endpoint}?q=${q}&count=${count}`
  const response = await fetch(url)
  return response.json()
}
```

ですが、urlを切り替えたいときに`base_url`を変更するのはなんだか癪ですよね。
そこで別の選択肢として**カレー化**を使ってみましょう。


```js
// カリー化
const async curreyCallAPI = (base_url = "https://example.com") => {
  return (endpoint="normal",count=10, q="Excel") => {
    const url = `${base_url}/${endpoint}?q=${q}&count=${count}`
    const response = await fetch(url)
    return response.json()
  }
}

// 適応
if is_dev === true:
    const callAPIDokomo  = curreyCallAPI("https://dokomo.com")
else:
    const callAPI        = curreyCallAPI()

```

このようにカレー化を使用することで以下の二つのメリットがあります。

- **中身の処理が似ているが微妙に内容が異なる処理の重複を防ぐ**
- **関数の中身の決定を遅らせる**