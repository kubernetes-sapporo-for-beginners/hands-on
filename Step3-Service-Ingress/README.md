# Service、Ingress

Service,Ingressを学ぶためのデモンストレーション、およびハンズオン用のマニフェストファイルを格納しています。<br>
資料は、

- [ハンズオン：コンテナにアクセスする方法](https://speakerdeck.com/hirokimatsumoto/kubernetes-hands-on-apps-for-k8ssa-number-3)

となります。

# 事前準備

ハンズオンを実施される方は、下記の準備をお願いします。  

## Kubernetes環境
Kubernetes実行環境の用意してください。 (下記は一例です。その他環境でももちろん問題ありません )
- GKE
- AKS
- EKS
- Docker for Desktop (Docker for Mac / Docker for Windows)


## 動作確認用アプリケーションのデプロイ
Service,Ingressの動きを確認するためのアプリケーションのデプロイをしてください。。<br>

```
$ git clone https://github.com/kubernetes-sapporo-for-beginners/hands-on.git
$ kubectl apply -f ./hands-on/Step3-Service-Ingress/prepare
deployment.apps "greet-v1" created
deployment.apps "greet-v2" created
pod "cluster-pod" created
$
```

正常にデプロイが完了すると、下記のように、podが5つ起動します。

```
$ kubectl get pod
NAME                        READY     STATUS    RESTARTS   AGE
cluster-pod                 1/1       Running   0          44s
greet-v1-5ddffdc4d8-mwqx5   1/1       Running   0          44s
greet-v1-5ddffdc4d8-qwk6k   1/1       Running   0          44s
greet-v2-57898bf9b6-f45fp   1/1       Running   0          44s
greet-v2-57898bf9b6-ntmxm   1/1       Running   0          44s
$
```

## Docker for Mac / Docker for Windowsを利用する方

下記を実行しておいてください。Ingressのリソースを制御するための、Ingress Controllerとなります。

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/provider/cloud-generic.yaml
```
