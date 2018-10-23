# Azure Kubernetes Service 事前準備

## クラスタの作成

下記の手順に従い、クラスタを作成してください。

https://docs.microsoft.com/ja-jp/azure/aks/kubernetes-walkthrough

下記3つが完了していれば問題ありません。
- リソース グループの作成
- AKS クラスターの作成
- クラスターへの接続

## ハンズオンのための事前準備

### ハンズオン資料のClone
まず、本リポジトリをcloneしてください。gitコマンドが使えない場合は、下記画面のようにzipでダウンロード、展開を行って下さい。

![image](../images/git-zip-download.png)

### StorageClassの作成

下記コマンドを行い、`standard` のStorageClassを作成してください。

```
$ cd docs\#1-ApplicationDeployment\kubernetes-prepared 
$ kubectl apply -f azure-storageclass.yaml
storageclass.storage.k8s.io "standard" created

$ kubectl get storageclass
NAME                 PROVISIONER                AGE
default (default)    kubernetes.io/azure-disk   51m
managed-premium      kubernetes.io/azure-disk   51m
standard (default)   kubernetes.io/azure-disk   20m
$
```

正常に作成されると、 `kubectl get storageclass` で、 `standard` が表示されます。
