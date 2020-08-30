# Podライフサイクル

Podライフサイクルを学ぶためのデモンストレーション、およびハンズオン用のマニフェストファイルを格納しています。

資料は後日アップされます。

# 事前準備

ハンズオンを実施される方は、下記の準備をお願いします。  

## Kubernetes環境
Kubernetes実行環境の用意してください。 (下記は一例です。その他環境でももちろん問題ありません )
- GKE
- AKS
- EKS
- Docker for Desktop (Docker for Mac / Docker for Windows)

# 実践 - 状態を知る。

## 通常の状態 (Running)

### 準備
下記コマンドを実行しておきましょう。これによりpodリソース状態変化を確認する事ができます。

```bash
kubectl get pod -w
```

### 実行

podinfoのdeploymentsを要求します。
```bash
$ kubectl apply -f simple.yaml 
deployment.apps/podinfo created
$
```

## Pending状態

```bash
$ kubectl apply -f pending1.yaml
deployment.apps/podinfo configured
$
```

```bash
$ kubectl apply -f pending2.yaml
deployment.apps/podinfo configured
$
```

```bash
$ kubectl apply -f pending3.yaml
deployment.apps/podinfo configured
$
```

## Succeeded/Failedの状態

```bash
$ kubectl apply -f succeeded.yaml
pod/pod-name created
$ kubectl delete -f succeeded.yaml
pod "pod-name" deleted
$ kubectl apply -f failed.yaml    
pod/pod-name created
$ 
```

# Probeの動きを知る。

いったんお掃除。
```bash
$ kubectl delete -f ./        
pod "pod-failed" deleted
deployment.apps "podinfo" deleted
pod "pod-succeeded" deleted
Error from server (NotFound): error when deleting "pending2.yaml": deployments.apps "podinfo" not found
Error from server (NotFound): error when deleting "pending3.yaml": deployments.apps "podinfo" not found
Error from server (NotFound): error when deleting "service.yaml": services "podinfo" not found
Error from server (NotFound): error when deleting "sidecar.yaml": deployments.apps "podinfo" not found
Error from server (NotFound): error when deleting "simple.yaml": deployments.apps "podinfo" not found
$ 
```

もう一回simple.yamlのapply。そしてより動きを理解しやすくするために、サービスも作成。
```bash
$ kubectl apply -f simple.yaml
deployment.apps/podinfo created
$ kubectl apply -f service.yaml
service/podinfo created
$ 
```

**podinfoの操作**

|目的|コマンド|
|:---|:---|
|バージョン取得|kubectl exec -it *{podname}* -- curl http://{service or pod ipaddress}:9898/version|
|readnessProbe無効化|kubectl exec -it *{podname}* --  curl -X POST localhost:9898/readyz/disable|
|readnessProbe有効化|kubectl exec -it *{podname}* --  curl -X POST localhost:9898/readyz/enable|
|livenessProbe無効化|kubectl exec -it *{podname}* --  curl -X POST localhost:9898/healthz/disable|
|livenessProbe有効化|kubectl exec -it *{podname}* --  curl -X POST localhost:9898/healthz/enable|
|OOMの発生|kubectl exec -it *{podname}* --  curl localhost:9898/oom|

### livenessProbeの確認

livenessProbeでエラーを返す。
```bash
kubectl exec -it *{podname}* --  curl -X POST localhost:9898/healthz/disable
```

livenessProbeを元に戻す。
```bash
kubectl exec -it *{podname}* --  curl -X POST localhost:9898/healthz/enable
```


### readnessProbeの確認

readnessProbeでエラーを返す。
```bash
kubectl exec -it *{podname}* --  curl -X POST localhost:9898/readyz/disable
```

readnessProbeを元に戻す。
```bash
kubectl exec -it *{podname}* --  curl -X POST localhost:9898/readyz/enable
```

### OOM発生時の動作確認

最初にprobeのエラーとする間隔を長くします。
```bash
$ kubectl apply -f oom.yaml   
deployment.apps/podinfo configured
$
```

下記の実行でOut Of Memoryが発生します。

```bash
kubectl exec -it *{podname}* --  curl localhost:9898/oom
```

### CrashLoopBackOffの動作確認

下記の実行でCrashLoopBackOffが発生します。

```bash
$ kubectl apply -f crash.yaml
deployment.apps/podinfo configured
$ 
```
