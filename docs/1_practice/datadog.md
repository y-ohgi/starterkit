# Datadog
![dd logo](../imgs/dd-logo.png)

強い理由がなければDatadogを選びましょう。  
機能や料金面ですぐれているだけでなく、社として最も使用事例が多く、利用申請フローも整っています。

## 監視の導入
3 pillars of observability（可観測性の3つの柱）、ログ ・ メトリクス ・ トレース の3つの柱を意識して監視しましょう。

## 3 pillars of observability
### ログ
ECS/Fargateであれば標準出力からCloudWatch Logsへ出力し、CloudWatch Logsを [Lambda](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#set-up-the-datadog-lambda-function) を使用してDatadogへ転送へ転送すると良いでしょう。  
この際ログを標準出力にし、フォーマットを1イベント1行（のJSON）にしましょう。

### メトリクス
DatadogとAWSを連携させましょう。  
数分で完了できるレベルです、サクッとやってしまいましょう。

> [AWS | Datadog](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions)

この際気をつけることとして、Tagをつけることです。  
弊社では本番と本番以外でアカウントを分けています。それらを区別し（本番アカウントのメトリクスがわかりやすくなるよう）にしましょう。

### トレース
DatadogのAPMはメジャーなフレームワークに対応しています。  
それぞれのフレームワーク（もしくは言語）のインストール方法を確認し、導入しましょう。

> [APM & Distributed Tracing](https://docs.datadoghq.com/tracing/)

## SLI/SLO
### SLI
Service Level Indicatorの略で、システムの安定稼働に必要な指標です。  
例えば「エラー率」・「リクエストのレイテンシ」・「稼働率」などです。

特にこだわりが無かったり特殊な挙動が入っていたりするわけではなければ「エラー率」と「リクエストのレイテンシ」の2つをSLIとして定義すると良いでしょう。  

### SLO
SLIをもとにシステム提供の可用率を定義します。  

SLOを定義することはエンジニアのために行うものだと筆者は思っています。  
一般的になにもしないとビズサイドから「SLAは100％」と意味不明なWordが飛んできてもおかしくないです。ビジネス層へシステムは100%ではないことを説明し、その合意をするタイミングを含めてSLOの定義を行ってしまいましょう。  
SLOの定義はエンジニアが管理者からの定量的な評価を受けることができるようになり、SLOを取り入れたことによりエラーバジェットという考え方で生産的な挑戦をすることができるようになります。

## アラートの設定
Datadogでできます。  

> [監視#アラート - 入門クラウド](../0_introduction/monitoring/#_13)

## ダッシュボードの作成
Datadogでできます。

> [監視#ダッシュボード - 入門クラウド](../0_introduction/monitoring/#_14)

## その他
### さらに先へ
- 行動ログの解析
- SLAの定義
- 分散トレース

### Organizationの分け方
マイクロサービス化されてくるとDatadog Organizationの分け方が気になってきます。  
将来的にマイクロサービスへの対応は拡張されるであろう箇所ですが、現時点のプラクティスとしてマイクロサービスは全環境1つのOrganizationに所属させるとよいと考えます。  
機能面では分散トレースをしづらいことがあり、組織面では知見の共有をしやすいことがあります。  
Datadogの操作で誤って障害を引き起こすことは基本的に起こらず、ログのマスクを行っていれば誰でも見れて良いはずです。
