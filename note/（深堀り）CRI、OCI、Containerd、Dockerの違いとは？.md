---
tags:
  - Docker
  - ContainerD
  - CRI
  - OCI
Created: 2025-06-21
---
# CRI と OCI の違い
## CRI (Container Runtime Interface)
- **定義**: kubeletとコンテナランタイム間のインターフェースを定義します
- **役割**: KubernetesのkubeletがコンテナランタイムとやりとりするためのAPIプロトコル
- **目的**: Kubernetesが様々なコンテナランタイム（Docker、containerd、CRI-Oなど）を統一的に扱えるようにする
- **レベル**: **Kubernetesレベル**のインターフェース
- **使用場面**: Kubernetesクラスター内でのPod管理、コンテナ実行制御
- **実装**: gRPCプロトコルを使用してkubeletとやりとり

## OCI (Open Container Initiative)
- **定義**: コンテナの実行、構築、および配布に関する標準を設定します
- **役割**: コンテナの実行可能な形式やランタイムの仕様を定義
- **目的**: 異なる環境でのコンテナの互換性が向上し、ポータビリティが確保される
- **レベル**: **業界標準レベル**の仕様
- **実装例**: runC（OCI Runtime Specification準拠の軽量コンテナランタイム）

## 主な違い

| 観点       | CRI                        | OCI          |
| -------- | -------------------------- | ------------ |
| **スコープ** | Kubernetes特化               | 業界全体の標準      |
| **目的**   | KubernetesとコンテナランタイムのAPI統一 | コンテナ技術全体の標準化 |
| **関係者**  | kubelet ↔ コンテナランタイム        | コンテナエコシステム全体 |
| **実装**   | gRPCプロトコル                  | 仕様書・標準       |
| **対象**   | Kubernetes環境               | あらゆるコンテナ環境   |

## 関係性
### 階層的関係
- **CRI**: 上位層（Kubernetes）- Kubernetesとコンテナランタイム間の通信
- **OCI**: 下位層（コンテナ実行）- コンテナの実際の実行標準

### 協調関係
CRI準拠のコンテナランタイムは、内部的にOCI準拠のランタイム（例：runC）を使用することが多い
```
kubectl → kubelet → CRI → containerd → OCI Runtime (runC)
```

## 具体例
### CRIの実装
- containerd
- CRI-O
- Docker（dockershim経由、現在は非推奨）

### OCIの実装
- runC
- crun
- Kata Containers

## なぜ重要か
- **CRI**: Kubernetesの拡張性とコンテナランタイムの選択肢を広げる
- **OCI**: コンテナ業界全体での互換性とポータビリティを保証

この理解により、Kubernetesのコンテナ実行アーキテクチャがより明確になります。
