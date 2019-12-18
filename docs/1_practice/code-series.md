# CD
CircleCI Enterpriseでもカジュアルなデプロイはシェルスクによって可能ですがサービスの責務（CI）を大きく超えたタスクになってしまいます。  
また、そもそもCircleCI自身にCDは機能として備わっていません

2019年8月時点プロダクト自体過渡期だと考じます。  
OSSではSpinnaker, Argo CD, Fluxがイケているといわれますがそれぞれまだ安定を得られなさそうな点はあります。  
CDツールはあとから変更可能なので、まずはスモールスタートでCode兄弟を使うと良いと思います

## Code兄弟
![code pipeline](../imgs/codepipeline.png)

CDにはAWSのマネージドサービス郡であるCode兄弟（CodePipeline, CodeBuild, CodeDeploy）を使用します。  
Code兄弟はBuildやDeployなどサービスがそれぞれの機能を持ち、CodePipelineで定義したワークフローの上で動かします。

雑に分けると以下のようなかたちになり、これが1つのデプロイになります。

- CodePipeline
    - デプロイに関する1連のワークフロー
- CodeBuild
    - 任意の処理の実行
        - DB migrationやアセットコンパイルなど
- CodeDeploy
    - デプロイの実行

このパイプラインをイベント毎（Gitへのpushやtag付け）に回し、デプロイを行います。

## その他CDプロダクト
### CircleCI Enterprise
CircleCIはCIツールという前提がありますが、CircleCI Enterpriseからデプロイすることも可能です。  
最初はCI/CDともにCircleCI Enterpriseを使用してスモールスタートするのもありでしょう。

### GitHub Action
GitHub Enterprise に来ることを座して待て。

### Argo
多機能なジョブ実行プロダクト。  
CDの実行もツールのスコープ内。自前ホストする必要あり。

### Spinnaker
GCPがマネージド（addon）なSpinnakerを出してきた。  
個人的な肌感としてはまだバギーなツールだと思っている。
