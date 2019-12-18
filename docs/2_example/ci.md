# CI
## テスト

### ユニットテスト
関数単位のテストです。  
DBはスタブやモックが必要になってきます。  
最低限書きましょう。テストの大事さは僕よりあなたの方が知っている。

### 統合テスト
複数システムを統合/結合したテストです。  
データストアのようなミドルウェアや他のマイクロサービスとの疎通などのテストです。

### どこまでやるか
テストは品質担保や継続的な開発に重要です。  
これは昨今の開発事情的にやるのが当たり前という風潮を感じ、僕が語るよりテストに詳しいチームメンバーに教えてもらったほうが良いと思い書きません。  
ただ、「テストをどこまでやるか」はサービスのフェーズによって異なると思います。テストを書くことは中長期的な投資で短期的には無い方がはやく開発できるという人も居ます。  
サービスのフェーズが進むに連れテストの重要度は上がっていき、最終的には3種類とも実施することになるはずです。初期フェーズであれば最低限ユニットテストは書きましょう。

CircleCIは複数コンテナを使用した統合テストが行いやすいです。  
ユニットテストに結合テスト（DBへの接続を発生させる）。を組み合わせてしまっても現代の潤沢なリソースや技術ではテストをスムーズに回すことができるでしょう。

## CircleCI Enterprise
何度も言っていますがCircleCI Enterprise がある/GitHub Enterpriseなのでこれを使いましょう。

以下からお探しの言語が見つかるはずです。  

> [Search · filename:config.yml](https://git.dmm.com/search?l=YAML&q=filename%3Aconfig.yml&type=Code)

### 複数コンテナの活用
```yaml
jobs:
  test:
    docker:
      - image: circleci/php:7.2
      - image: circleci/mysql:5.7
  :
      - run:
          name: dockerize
          command: |
            DOCKERIZE_VERSION=v0.6.1
            wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz
            tar -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz
            rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz
            ./dockerize -wait tcp://localhost:3306 -timeout 1m
```
