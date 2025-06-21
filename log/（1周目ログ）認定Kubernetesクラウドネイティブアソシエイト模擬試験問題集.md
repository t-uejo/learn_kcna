# 演習テスト５
## クラウドネイティブセキュリティの4C
![[Pasted image 20250621081948.png]]

## kubectl edit (RESOURCE/NAME | -f FILENAME)
- 指定したリソースを編集するためのテキストエディタが開きます。このコマンドを使用すると、リソースのYAML定義を直接編集することができます。
- これは、リソースを動的に変更する場合に便利です。

## statefulsetとHeadless Service
- statefulsetでは、Podの識別にHeadless Serviceが使用されます。
- Headless Serviceは、個々のPodに固有のDNSエントリーを提供し、Podを一意に識別します。
- https://kubernetes.io/ja/docs/concepts/workloads/controllers/statefulset/

## Kubernetes ダッシュボードのユースケース
- 新しいKubernetesクラスターのインストールはダッシュボードのユースケースではありません。

## kube-scheduler
- 新しいポッドをどのノードにスケジュールするかを決定するためのコントロールプレーンコンポーネントです。
- Kubernetesにおけるデフォルトのスケジューラーで、コントロールプレーンの一部分として稼働します。
- ポッドの要件とノードの状態を考慮して、最適なノードを選択してくれるので、クラスター内のリソースが効率的に使用され、ポッドが適切に配置されます。

## kube-proxy
- kube-proxyはノードコンポーネントの一部です。コントローププレーンのコンポーネントではありません。
- [Kubernetesのコンポーネント](https://kubernetes.io/ja/docs/concepts/overview/components/#%E3%82%B3%E3%83%B3%E3%83%88%E3%83%AD%E3%83%BC%E3%83%AB%E3%83%97%E3%83%AC%E3%83%BC%E3%83%B3%E3%82%B3%E3%83%B3%E3%83%9D%E3%83%BC%E3%83%8D%E3%83%B3%E3%83%88)

## CustomResourceDefinitions（CRD）
- Kubernetesクラスターに独自のリソースタイプを追加できます。
- これにより、ユーザーは独自のカスタムリソースを定義して使用することができます。CRDを使用することで、Kubernetesの柔軟性と拡張性が向上
- https://qiita.com/shmurata/items/86f3a0c2a2431cec410e#customresourcedefinitionscrd-%E3%81%A8%E3%81%AF

## 必須のフィールド
- metadata
- kind
- apiversion
- spec
- cotnainerは違う
- https://kubernetes.io/ja/docs/concepts/overview/working-with-objects/kubernetes-objects/#%E5%BF%85%E9%A0%88%E3%83%95%E3%82%A3%E3%83%BC%E3%83%AB%E3%83%89

## NodeSelector
- Podがどのノードにスケジュールされるかを制御
- PodのspecにnodeSelectorフィールドを追加することで、ターゲットNodeが持つべきNodeラベルを指定できます。 Kubernetesは指定された各ラベルを持つNodeにのみ、Podをスケジューリングします。
- DeploymentはPodの管理を行いますが、スケジューリングに直接関与しません。
- https://kubernetes.io/ja/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector

## kubectl describe nodes
- kubectl inspect nodesおよびkubectl check nodesは存在しないコマンド

## 暗号化
- KubernetesのSecretsを暗号化して保存するための方法
- RSAが採用される。
- これはSealed Secretのことを言っているのか？

## OPA Gatekeeper
- OPA GatekeeperはKubernetesクラスター内で実行できる内容を制御するカスタム ポリシーを作成できるツールの一つです

## runC
- Open Container Initiative (OCI) ランタイム仕様に完全に準拠した軽量のコンテナー ランタイム
- https://medium.com/nttlabs/runc-overview-263b83164c98

## kubectl api-resources
- Kubernetesクラスター内の使用可能なすべてのオブジェクトを一覧表示します。

## kubectl create deployment app-dep --image=nginx --replicas=5
- 名前が "app-dep" でレプリカ数が 5 で、Nginxイメージを使用したデプロイメントが作成されます。

## kubectl explain RESOURCE
- Kubernetesのリソースタイプに関する詳細な情報が取得
- kubectl explain pods

## init container（イニシャライズ コンテナ）
- Pods内のコンテナが起動する前に実行されるタスクを実行する
- この機能を使用すると、コンテナの起動前に特定のタスクを実行して、正常な起動を確認できます。

## Kubernetes フェデレーション
- 複数の Kubernetes クラスターを統合し、統一された管理を可能にするツールです。
- これにより、異なるクラウドプロバイダー間でのクラスターの管理が容易になります。
- マルチクラウド環境でのアプリケーションのデプロイメントを簡素化し、運用を簡素化します。
- これにより、開発者や運用チームはより効率的にリソースを管理し、アプリケーションを展開できます。
- https://tech-blog.abeja.asia/entry/Kubernetes-federation#:~:text=Federation%E3%81%AF%E8%A4%87%E6%95%B0%E3%81%AE%E3%83%AA%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3,%E3%81%A7%E5%AE%9F%E7%8F%BE%E3%81%95%E3%82%8C%E3%81%A6%E3%81%84%E3%81%BE%E3%81%99%E3%80%82

## kubectl logs hello -c green
- -pがついてもOKなのか？

## CRI
- kubeletとコンテナランタイム間のインターフェースを定義します。

## オープンコンテナイニシアチブ（OCI）
- コンテナの実行、構築、および配布に関する標準を設定します。
- これにより、異なる環境でのコンテナの互換性が向上し、ポータビリティが確保されます。

## コンテナランタイムのcontainerdやCRI-Oの違いとは？
- Kubernetesがコンテナを管理し、実行するためのインターフェースを提供
- これらは同じでインターフェースを提供するのみか



---
# 演習テスト４
## なぜContainered？
- なぜDockerからContainerdになったのか。

## kubelet
- kubeletは各ノード上でポッドを管理し、ポッドのライフサイクルを制御し、各コンテナがPodで実行されていることを保証します。
- 各コンポーネントの役割についてちゃんと復習すること。

## SRE
- SLA、SLO、および SLI を作成して、アプリケーションとインフラストラクチャの信頼性に関する標準を定義および実装。
- システムリライアビリティエンジニア

## kubectl logs [-f] [-p] (POD | TYPE/NAME) [-c CONTAINER]
- kubectl logs deployment/nginx -c nginx-1

## Kubernetesのポッド内で実行されているプロセスを確認するためのコマンド
- kubectl describe pods

## kubectl top nodes
- リソース (CPU/メモリ) の使用状況を表示します。

## Kubernetesのポッドのスケジューリング戦略
- ラウンドロビン戦略が採用されている。おそらくデフォルトで。

# 演習テスト３
## ラベルの例
-  labels:
    app: nginx

## ランタイムクラス（RuntimeClass）
- Podごとに異なるコンテナランタイムを使用するために使用。
- 使用するコンテナランタイムによって特性があるので最適化するために利用すると。

## Notary
- コンテナイメージに暗号化署名を付与するプロジェクトで、配布されているコンテナイメージが、途中で改ざんされていないことを署名によって確認できます。
- Notaryは"公証人"という意味です。

## Flux
- GitOpsとして知られるツールキットを使用して構成

## kubectl logs -p -c nginx web
- -p（previous）は、ポッド内のコンテナの以前のインスタンスのログを出力するオプションです。
- -c（container）は、コンテナのログを出力させるのに使用するオプションです。-c の直後にコンテナ名を指定します。

## 支配的なCNCFプロジェクト
- **業界標準として広く使われている**
- **他プロジェクトに依存されている（基盤技術）**
- **成熟度が高く、CNCFで「Graduated（卒業）」している**
- **クラウドネイティブの中核的な役割を担っている**

## Trail MapとLandscape
- Cloud Native Trail Map
    - クラウドネイティブ化までのステップを示したもの
- Cloud Native Landscape
    - Cloud Nativeなサービス一覧

## RBAC
- 特定のユーザー、グループ、またはサービスアカウントに対して、クラスター内のリソースへのアクセス権を制御

## kubectl expose rc nginx --port=80 --target-port=8000
- typeがclusterIPなサービスができると。
- rc nginx
	- ReplicationController の `nginx` を指定
	- これは古い指定方法であると。
- ところどころに古いものがあるのが気になるな。テストでこける可能性がある。

## kubectl logs --tail=10 nginx-pod
- Podnginx-podのログを直近の10行だけ表示

## kubectl rollout undo deployment sample-pod --to-revision 2
- sample-podをRevision.2にロールバックする。

## kubectl rollout history deployments nginx-deployment
- デプロイメントnginx-deploymentのロールアウト履歴
- `nginx-deployment` に何らかの変更（イメージのバージョン変更、レプリカ数の変更など）を加えるたびに、その状態が「履歴（リビジョン）」として保存されます。
- 以下のコマンドで確認ができる。
	- kubectl set image deployment/nginx-deployment nginx=nginx:1.19
	- kubectl rollout history deployment nginx-deployment

## kubectl get pod nginx-pod -o yaml
- Pod: nginx-podの詳細情報を表示し、YAML形式で出力する
- `kubectl get pod nginx-pod -o yaml > pod.yaml` のようにファイル出力可能

## kubectl delete pods --selector=app=nginx
- app=nginxというラベルが付いているものを削除
- **`--selector` と `-l` は同義で、好みや文脈で使い分けるだけ**です。

## kubectl logs -f -l app=nginx-pod
- -f（**f**ollow）オプションは、ログをリアルタイム表示したいときに指定します。
- -l （se**l**ector）オプションは、ラベルセレクターを指定しています。
- ラベルが「app」というキーで「nginx-pod」**という値を持つPodを選択**

## kubectl get services --show-ips
- クラスター内のすべてのサービスとそれぞれのサービスのIPアドレスを表示

## kubectl set env
- "set env"は、1 つ以上のポッド、ポッド テンプレートの環境変数を更新するコマンドです。

## kubectl logs -f nginx-pod
- 指定したPodのログをリアルタイムで表示

## kubectl scale deployment x-pod --replicas=y
- 指定されたデプロイメントのレプリカ数を変更

## kubectl getとkubectl describe
- リスト表示させるか、詳細表示するかの違い

## kubectl set image
- "set image"はリソースの既存のコンテナイメージを更新するコマンド

## kubelet
- ポッドの再起動や代替ポッドの作成を担当するのはkubeletです。
- kubeletはノード上で実行され、そのノード上のポッドの生存状態を監視し、必要に応じて再起動や再作成を行います。

## データ収集、可観測性、および監視はなぜ重要か
- アプリケーションの可用性を向上させるために重要。
- これにより、問題が発生した際に早期に検出し、迅速に対処することができる。

## Datadog
- クラスタ監視のためのツール。

## OpenTelemetry
- 可観測性のための仕組み全体のこと。ツール群＋仕様の集合体（SDK＋Collector＋Protocol）
- Promethusと統合できる。

## リザーブドインスタンス
- クラウド環境でコスト最適を実現するためには、リザーブドインスタンスを使用します。リザーブドインスタンスは長期間の利用を前提に事前に予約することで割引を受けられる仕組みです。

## セマンティック バージョニング（SemVer）
- major.minor.patch の3つのドットで区切られる。

## 論理グループ化
- ラベルで分類し、それをセレクターで**意味のあるグループ（論理的なまとまり）として扱う**ことができます。
- Kubernetesでは、ラベルを使ってリソースにタグ付けし、セレクターを使ってそのラベルを持つリソースを探し出すことで、リソースを論理的にグループ化・操作することができます。

## FluxCD や ArgoCDのトリガー方式
- ArgoもFluxもpullベース
- FluxCD や ArgoCD は Pull 型の GitOps ツールと呼ばれています。

## OpenPolicyAgent
- OPAは「どこにでもポリシーを組み込める」柔軟なエンジンです。セキュリティ、ガバナンス、監査、整合性といった企業のあらゆる課題に対応でき、**Regoによる宣言的なルール管理が特徴**です。
- OPAはポリシー管理のためのオープンソースプロジェクトであり、Kubernetesなどのクラウドネイティブ環境でのアクセス制御やポリシー管理を実現します。

---
# 演習テスト２
## ローリングデプロイメント
- ローリングデプロイメントは、新しいバージョンを段階的に展開して、システム全体の可用性を維持します。
- https://www.splunk.com/ja_jp/blog/devops/ci-cd-devops-pipeline.html
- 新しいバージョンのアプリケーションが徐々にデプロイされ、過渡的な停止やサービスの中断を最小限に抑えながら、アプリケーションのアップグレードが可能になります。

## サーキットブレーカーパターン
- 依存している外部サービスやコンポーネントが障害を起こした際に、**連鎖的な障害（カスケード障害）**や、無駄なリトライによる**リソースの消耗**を防ぐためのデザインパターン
- サーキットブレーカーパターンは、依存するサービスの障害によってシステム全体が影響を受けるのを防ぐために使用されます。

## ブルーグリーンデプロイの説明
- 「新しいバージョンのアプリケーションがリリースされる前に、一時的にトラフィックを新しいバージョンにルーティングします」は誤り。
- 上記の説明では、すべてのトラフィックが時間体の一部で新しいところへ行く。
- ブルーグリーンは時間に限らず、半分ずつ流すなどになる。

## PrometheusのAlertmanagerにおける `for`とは
- `for` は「条件を○分間継続して満たしているか？」を見てから **「firing状態に昇格」させる**ためのもの。
- firingとなったらAlertmanagerへ通知させる。

## リカバリ通知
- Alertmanagerが発行したアラートが解消された（正常状態に戻った）ことを通知する機能のこと。
- 監視対象の状態が正常範囲に戻ると、「問題が解決された」旨を知らせる通知が送信されます。

## ダウンサンプリング
- 株価など、解像度が高い1秒などのデータを、代表値を決めて、1日などの長期トレンドを把握できる値に変換すること。
