# クラウドスターターキット

## About
![architecture](imgs/aws_architecture.png)

AWSにおける3層アーキテクチャのためのテンプレートになります（以降スターターキットと呼びます）。

## 構成
![repository](imgs/repository.png)  
スターターキットは1つのドキュメントリポジトリと2つのアプリケーション用リポジトリで構成されます。

- [y-ohgi/starterkit](https://github.com/y-ohgi/starterkit)
    - スターターキットのドキュメントです。
    - 当リポジトリ（gitbook）です。
- [y-ohgi/starterkit-inf](https://github.com/y-ohgi/starterkit-inf)
    - TerraformでAWSの共通リソース（VPC, ALB, ECS Cluster, etc...）を記載
- [y-ohgi/starterkit-app](https://github.com/y-ohgi/starterkit-app)
    - アプリケーションコード用リポジトリ
    - ローカル環境ではdocker-composeを、本番環境では"starterkit-inf"で構築した共通リソースの上にECS/Fargateを構築します。
        - サンプルとして別ブランチにgolangでの例を用意しています。
    - "starterkit-app"は"_infra"ディレクトリに配置されているTerraformがメインになります。リポジトリルートに任意のファイル・ディレクトリ（RailsやNextなど）を配置し、"_infra"ディレクトリをコピペして使用することを想定しています。

## 想定する読者層
- サーバーサイドの開発経験がある
- AWSを実務で触ったことがある
- AWSを実務で使いこなしたいモチベーション

## 備考
- GitHub
    - [y-ohgi/starterkit](https://github.com/y-ohgi/starterkit)
- 筆者
    - [@_y_ohgi](https://twitter.com/_y_ohgi)
- [Privacy Policy](privacy-policy.md)
    - Google Analytics によって各章の滞在時間を把握することが目的です。

## 注意
このドキュメントはあくまで [@_y_ohgi](https://twitter.com/_y_ohgi) が発信する1パターンです。
