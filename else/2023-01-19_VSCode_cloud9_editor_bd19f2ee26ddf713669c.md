<!--
title:   Cloud9 vs VScode Online
tags:    VSCode,cloud9,editor
id:      bd19f2ee26ddf713669c
private: false
-->
## Cloud9とは何か？

*AWS Cloud9 には、**事前認証された AWS コマンドラインインターフェイスと一緒に開発環境をホストしている**、マネージド Amazon EC2 インスタンスに対する sudo 権限を含むターミナルが付属しています。これにより、すばやくコマンドを実行して AWS のサービスに直接アクセスすることが簡単になります。*

要は:Cloud9とは**EC2に対して、vscodeのようなエンジニアにとって快適なインターフェースを追加したもの**

<img src="https://d1.awsstatic.com/product-marketing/Tulip/Terminal%20New.67b39d8fa735fcd10b997e2767a4302d3e388263.png">

from https://aws.amazon.com/jp/cloud9/


## 料金:無料

AWS Cloud9自体には費用はかかりませんが、これに合わせて利用するサービスには料金がかかってくるため注意が必要です。

from https://www.yume-tec.co.jp/column/awsengineer/4595#9Lambda


*AWS Cloud9 には追加料金はかかりません。AWS Cloud9 開発環境に Amazon EC2 インスタンスを使用する場合は、コードの実行と保存に使用された コンピューティング とストレージのリソース分 (例: EC2 インスタンス、 EBS ボリューム) のみのお支払いとなります。また、AWS Cloud9 開発環境を、SSH 経由で、追加料金なしで、既存の Linux サーバー (オンプレミスサーバーなど) に接続できます。*

from https://aws.amazon.com/jp/cloud9/pricing/






# Vscodeに勝る点

## リアルタイムでのメンバー間の連携

共同作業中にチームメンバーは互いのタイピングをリアルタイムで確認でき、IDE 内から即座にチャットを開始できます。

**ペアプログラミングに適した IDE**

<img src="https://d1.awsstatic.com/product-marketing/Tulip/C9-Collab-Image%403x.e03a65d9488633c154358430540ab363dd1e8f45.png">


## lambdaをサポートしてくれる

*Cloud9 では、**AWS Lambda** 関数をローカルでテストおよびデバッグするための環境を利用できます。これにより、コードを直接反復処理して時間を節約し、コードの品質を向上させることができます。*

<img src="https://d1.awsstatic.com/product-marketing/Tulip/AWS_Cloud9_Asset03_R3P.f4760f91e9108120992d31a8ab0014022595a43e.png">


## terraformのレジストリ登録済み

次の名前でterraformレジストリに登録されていた。
Iacの恩恵を受けることができる。

レジストリ名:Resource: aws_cloud9_environment_ec2

サンプルコード

```tf
resource "aws_cloud9_environment_ec2" "example" {
  instance_type = "t2.micro"
}

data "aws_instance" "cloud9_instance" {
  filter {
    name = "tag:aws:cloud9:environment"
    values = [
    aws_cloud9_environment_ec2.example.id]
  }
}

resource "aws_eip" "cloud9_eip" {
  instance = data.aws_instance.cloud9_instance.id
  vpc      = true
}

output "cloud9_public_ip" {
  value = aws_eip.cloud9_eip.public_ip
}
```

from https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloud9_environment_ec2


*一方、AzureのVscode Onlineをサポートするレジストリは存在しなかった。*


# Vscodeに劣る点

## AWSへのログインが必要

```
これはCloud9とう特性上仕方ない作業です。AWSのログインってなぜかメールアドレスとパスワードの画面遷移があって、しかも毎回ロボットか疑われるので地味に面倒ですよね...。
VS CodeなどからSSHで接続すれば公開鍵認証なのでパスワードを打つ必要はなくなります。
```

要するに:**awsのログインはかなり面倒**

from https://note.com/mtkn1/n/nbc33e765558b#9de1ebf9-a67e-4993-91a0-1d40e52c399b

## syntaxハイライト

```
Cloud9は内蔵エディターを搭載しておりWebアプリとしては高性能ですが、ネイティブなエディターには劣ります。VS Codeに乗り換えるとPythonのシンタックスハイライトやコード補完、型推定などが大幅に強化されます。
コーディングはVS Codeを使ってCloud9にコピペする使い方もありますが、手動でファイル操作するよりもVS Codeまたはコンソール上で操作したほうがファイル管理が煩雑になりません。
```

現在は改善されている可能性があるが、シンタックスハイライトはVscodeに軍配が上がる。

from https://note.com/mtkn1/n/nbc33e765558b#9de1ebf9-a67e-4993-91a0-1d40e52c399b