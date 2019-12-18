# CI（CircleCI Enterprise）
継続的インテグレーション（Continuous Integration）です。  
リポジトリにpushされたコードを自動的にビルド&テストを実行し、開発物の品質担保を行います。  

## Circle CI Enterprise
![circleci](../imgs/cci-logo.png)

CIサービスであるCircleCIのEnterprise版、CircleCI Enterprise が社内でホストされています。  
CircleCIと比べると一分機能（OrbsやiOS対応）が欠けているのが惜しいですが、基本的にEnterprise版でも遜色なく使用することが可能です。  
また、GitHub EntepriseからCircleCI Enterpriseへはが連携しやすいです。  

今後GitHub ActionがGitHub Enterpriseでサポートされたり新しいCIプロダクトがホストされない限りはCircleCI Enterpriseを選択すれば問題ないでしょう。

![circleci workflow](../imgs/cci-workflow.png)

## 注意点
CircleCI EnterpriseはAWSでホストされています。  
リソース不足になれば全体の挙動が不安定になります（経験談）。  
無邪気にCircleCIのリソースプールを使用しすぎない/長時間フックしすぎないよう、真摯な利用を心がけましょう。  

最初は以下の項目に気をつけましょう。

1. 共有リソースであることを意識する
    - CircleCI Enterprise は自社でAWS上に構築されています。
    - Nomadを使用してクラスターを構築しており、時間によってEC2の台数が変わるようにコントロールされています。
2. 長時間かかるジョブを実行しない
    - ジョブは共有リソースの一部を一時的に使用して実行するため長時間かかると他のユーザーが使うリソースが無いといった状態になる可能性があります。
    - CircleCI Enterprise 自体が不安定な面もあり長時間かかるジョブは落ちる可能性が時間とともに上がっていきます。
    - CircleCI EnterpriseはCIを目的にされたプロダクトです。予め長時間かかることが想定されるワークロードはRundeck・Digdag・Jenkins・Argo・CronJob(k8s)などジョブ実行をスコープとされたプロダクトを使いましょう。CircleCIにバックオフリトライは
4. 最適なリソースクラスを選択する
    - 実行するジョブの [リソース](https://circleci.com/docs/2.0/configuration-reference/#resource_class) を選択することができます。
    - 基本的にデフォルト（medium）のままで問題ないですが、必要に応じて最適なリソースを選択しましょう。
        - 一般的にCPU/Memoryより人件費のほうが高く付きます。本当にリソースが必要になったらCircleCI Enterpriseの管理者へ連絡し、増強してもらいましょう。
