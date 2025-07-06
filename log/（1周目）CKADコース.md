## kubectl explain pod
- 仕様を確認することができる。

## kubectl delete rs
- rsでreplicasetを表現することができる。

## kubectl get deploy
- これでdeploymentを確認ができる。

## 試験のコツ
- kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml
- これを使うことでさくっとyamlファイルを出力させることができる。
- --dty-runがないとリソースが作成されてしまうので注意する。

## Podは直接編集できない
- まあ、あまりこのケースはないと思われる。
- Podの多くの仕様は直接編集できませんが、Deployment経由なら柔軟に編集できると。
