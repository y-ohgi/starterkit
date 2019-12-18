# AWSの学習

## 学習資料
> [AWS クラウドサービス活用資料集 Top](https://aws.amazon.com/jp/aws-jp-introduction/)    

一番カジュアルに学習できるのがAWS公式で公開されているBlackBeltという資料です。  
初めて触るサービスはまずはBlackBeltから学習を始めると良いでしょう。

## ドキュメント
AWSの各サービスのドキュメントは非常に充実しています。充実しすぎていて読み込むのに苦労するのですが、AWSは集めたを実務に反映しやすいです。  
筆者は土日にお風呂に入りながらゆるゆると各サービスのドキュメントを読み進めました。

> [Amazon VPC とは? - Amazon Virtual Private Cloud](https://docs.aws.amazon.com/ja_jp/vpc/latest/userguide/what-is-amazon-vpc.html)

## ベンダー資格駆動学習
> [AWS 認定 – AWS クラウドコンピューティング認定プログラム | AWS](https://aws.amazon.com/jp/certification/?nc1=h_ls)

AWSによるベンダー資格です。  
古いサービスに問われる問題もありますが、それに目を瞑れば実務的で非常にコスパの良い資格です。  
資格はいくつかありますが「AWS 認定ソリューションアーキテクト – アソシエイト」を目指して勉強すると良いです。

## 主要サービス
「まずどのサービスを勉強すれば良いのか」「最短でAWSを学習するには」まずは以下の主要サービスを学びましょう。  
学習するのに最初から本/技術ブログを読むのではなく、実弾演習アカウントでGetting Started の項をハンズオンしてみましょう。  
当たり前ですが二次情報を参考にするのはリテラシーが求められます。最初は公式ドキュメントから入ると良いでしょう。  
また、公式ドキュメントなのでメンテされており、機能変更に追従していて余計な混乱を招きづらいです。  

1. VPC
    - VPC
    - Subnet
    - SecurityGroup
    - RoutaTable
    - etc, ...
2. EC2
    - EC2インスタンス
    - InstanceProfile
3. IAM
    - User, Role, Group, Policy, InstanceProfile
4. ELB
    - ALB, NLB, CLB
5. RDS
    - Aurora
6. ECS/EC2, ECS/Fargate
    - AWS製コンテナオーケストレーション
8. ACM, Route53
    - TLS証明書、レコードの登録
9. ElastiCache

試験では他にElasticBeanstalkやEBSなどの知識も必要になってくるため受験するタイミングでドキュメントから学びましょう。  
上記の主要なサービスを体系立てて学習することのほうが重要なのです。

## 弊社での学習の仕方
弊社ではAWS社の方から直接、毎週2回のオフィスアワーと毎月AWSの勉強会が行っていただいています。  
また、Slackの [#prj-aws](https://tsuchinoko.slack.com/messages/C4BD5GNQ6) チャンネルにAWSの中の人がいて、カジュアルに話しかけるとカジュアルにレスが返ってきます。  
AWSを使うのにこれらの潤沢なサポートを逃す手はないでしょう。  

また、福利厚生の一環としてQwiklabsというハンズオン形式でクラウドを学ぶサイト（有料）を無料で使うことができます。  

> [Qwiklabs申請 - クラウド推進 - Confluence for DMM.com LLC](https://confl.arms.dmm.com/pages/viewpage.action?pageId=236566720)

また、何度もいいますが、どのフェーズであっても大木がサポートに行くことが可能です。  
2019年内に辞めるのでその範囲内で、タスクコードがあれば、チームの一員としてワークします。  
メンバーの教育・アーキテクティング・壁打ちなどなど、お気軽に分報へおこえがけください。

[#times_y-ohgi](https://app.slack.com/client/T09DRD4PQ/C9PSTPGFN)
