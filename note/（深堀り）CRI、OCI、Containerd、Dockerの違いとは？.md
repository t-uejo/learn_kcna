---
tags:
  - Docker
  - ContainerD
  - CRI
  - OCI
Created: 2025-06-21
---
## なぜDockerは非推奨となったのか？
- DockerはCRIをサポートしていないから。

## CRIランタイム
- KubernatesのkubeletがCRIを用いてコンテナランタイムに対して命令を実行する。
- ランタイムには、ContainerdとCRI-Oがある。

## OCIランタイム
- OCIランタイムはLinuxのシステムコールであるnamesapceとcgroupを用いて実際のコンテナ(ホスト上で隔離されたプロセス)を作成、削除する役割
- runCやgVisor

## 全体像
![[Pasted image 20250621140126.png]]

## 参考記事
- https://blog.inductor.me/entry/2020/12/03/061329
- https://jaco.udcp.info/entry/2020/12/03/172843

