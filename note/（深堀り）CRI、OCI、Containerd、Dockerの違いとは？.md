---
tags:
  - Docker
  - ContainerD
  - CRI
  - OCI
Created: 2025-06-21
---
## Dockerが非推奨となった理由
- DockerはCRIをサポートしていないから。
	![[Pasted image 20250621140810.png]]
- 以下となっただけ。ContainerdがCRIランタイムだったのでこれで良いと。
	![[Pasted image 20250621140832.png]]

## 階層構造での理解

### 上位層: Kubernetes API
- kubectl → kubelet

### 中間層: CRI (Container Runtime Interface)
- KubernatesのkubeletがCRIを用いてコンテナランタイムに対して命令を実行する。
- ランタイムには、ContainerdとCRI-Oがある。

### 下位層: OCI (Open Container Initiative)
- OCIランタイムはLinuxのシステムコールであるnamesapceとcgroupを用いて実際のコンテナ(ホスト上で隔離されたプロセス)を作成、削除する役割があると。
- runCやgVisorが実装である。

## 全体像はこんな感じ
![[Pasted image 20250621140126.png]]

## 参考記事
- https://blog.inductor.me/entry/2020/12/03/061329
- https://jaco.udcp.info/entry/2020/12/03/172843

