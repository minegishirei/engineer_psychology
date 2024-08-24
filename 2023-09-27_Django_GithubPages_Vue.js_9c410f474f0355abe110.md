<!--
title:   Github Pagesのおかげで救われた話
tags:    Django,GithubPages,Vue.js,フロントエンド
id:      9c410f474f0355abe110
private: false
-->
AWSの使用料で完全にあきらめていたWebサイト「FlameValue」
Github Pagesのおかげで一度完全につぶれたWebサイトを復活させることができました！

https://minegishirei.github.io/flamevalue_site/code/vue-notus/dist/index.html?name=Scala

このサイトは**プログラミング言語、フレームワークの価値を「実際に掲載されている求人情報を元にスコアリング」し、「今市場価値が最も高いプログラミング言語、フレームワークは何か？」** という問いに答えるべく構築された、**「フレームワーク、プログラミング言語スコアリングサイト」**　。

だったのですが...
AWSの使用量が圧迫してきたので3か月前にAWSアカウントごと削除し、完全に埋没してしまいました。

ところが今回、Github Pagesを使用することにより、**完全につぶれてしまったWebサイトを復活させることが出来ました！**


![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1678228/6f2abd21-40ea-0621-b3c2-06ec688ab5fa.png)



# 以前の構成の問題点：お金がかかる

以前はサーバーにAWSを使用してましたが... 月3000~5000円かかってました。

> 構成：AWS + Django

うまい具合にマネタイズできるかな～と思っていたのですが、収益はほぼ0...。
AWSの積み重なる出費に心が折れて完全にサービス終了となってました。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1678228/b09667a2-ac78-7468-2cad-732b09295747.png)

以前投稿した記事

https://qiita.com/minegishirei_v2/items/dd91d39bad157a927ffb

# 今回の構成のメリット：無料！

**Github Pagesは完全に無料です。**
（サーバーではないのでデータベース、バックエンドは自力で用意しなければなりませんが...）



> 構成：Github Pages + Vue


Vue.jsはSPAフレームワークでStaticなウェブサービスとして動作します。
前作ではEC2上にサービスとしてDjangoを使用してましたがGithub Pagesを利用するためには静的サイトとしてビルドできる必要があります。
そのため、Github Pagesの選択肢としては以下の3つが当てはまると思います。

- React
- Vue.js
- 生のhtml css javascript

今回は初心者にも簡単なVue.jsを活用しました！

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1678228/311013da-fd9d-1655-8356-9f96c21b123c.png)



# 最後に

AWSの利用料に心が折れたらGithub Pagesを利用しましょう！

最後までご視聴ありがとうございました！