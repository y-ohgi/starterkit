# コンテナ化
## 入門
拙作の [入門 Docker](https://y-ohgi.github.io/introduction-docker/) を参照してください。

## 導入
新規開発なら最初からDockerで開発していきましょう。  

既存のVMからの移行であればステップを踏んで行くのが良いでしょう。

1. ローカル環境のDocker化
    - まずはローカル環境での導入から行います
    - チームの開発環境をDockerで統一し、Dockerに慣れていくところから始めていきましょう
2. テスト/CIへの導入
    - 次にテスト/CI環境への導入を行います
    - また、CIを導入してないのであればDockerとの相性が良いのでこの機会に導入するのもありでしょう。
3. ステージングへの導入
    - 本番へいきなり導入する前にステージング環境でDockerの動作を確認しましょう
4. 本番への導入
    - 最後に本番環境への導入を行いましょう

## サービスのコンテナ化
### Dockerileで動かす
Dockerfileはの表現力は良い意味で表現力が低いです。  
Dockerfileは慣れるといろんなことをしたくなりたくなりいがちです（環境毎にMulti Stage Buildをしているなど）。複雑化しすぎないようにDockerfileを記載しまししょう。

### The Twelve-Factor App
The Twelve-Factor App はHeroku社が提唱するモダンなアプリケーション構築のための12のプラクティスです。  

> [The Twelve-Factor App （日本語訳）](https://12factor.net/ja/) 。  

コンテナ化に始まり、スケーラビリティ、環境変数の格納、ログの扱い、などなどモダンなアプリケーションの条件が記載されています。  
今後ECS/FargateではなくKubernetesやCloudRunなどに移行する差異にもここでの12factorな設計は将来的にも効いてきます。
