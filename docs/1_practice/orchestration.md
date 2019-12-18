# コンテナオーケストレーションツール
復数のDockerコンテナを協調して動かすためツールです。
主にDockerの管理/自動復旧・ネットワークの管理・オートスケールなど、本番のワークロードに必要な機能を備えています。

## 代表的なオーケストレーションツール
### docker-compose
Docker社がホストするオーケストレーションツール。  
ローカルでdockerを動かす際のデファクトスタンダードとなっているツールです。  
Docker for Mac/Windowsをインストール時に同時にインストールされるので、インストールも簡単です。  

### swarm
同じくDocker社がホストするオーケストレーションツールです。  
docker-composeと相性がよく、 `docker-compose.yaml` を拡張することで本番のワークロードでDockerを使用することができます。  

### ECS (Elastic Container Service)
AWSが開発したオーケストレーションツール。  
AWSが開発したということで、他のAWSサービスと連携が行いやすいです。  
また、他のオーケストレーションツールと比較して責任を持つ範囲が狭いため、比較的学習コストが低いです。

> [Amazon ECS Workshop :: Amazon ECS Workshop](https://ecsworkshop.com/)

### Kubernetes
Google社が開発したOSSのオーケストレーションツール。  
Kubernetesが現在のデファクトスタンダード。  
自由度が高く豊富なエコシステムがあり、コミュニティも非常に活発です。

## 選定
ローカルはdocker-composeを、プロダクションはECS/Fargateを使用すると良いでしょう。

選定理由については [コンテナ化](../../0_introduction/container) を参照してください。
