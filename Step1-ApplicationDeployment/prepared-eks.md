# Amazon EKS 事前準備

## クラスタの作成

下記の手順に従い、クラスタを作成してください。
STEP.3まで完了していれば十分です。

https://docs.aws.amazon.com/ja_jp/eks/latest/userguide/getting-started.html#eks-create-cluster

**注意事項**<br>
クラスタは、AWS CLIで作成した方が良いと思います。
下記にもありますが、 `kubectl` コマンドで接続しようとすると、

```
error: You must be logged in to the server (Unauthorized)
```

のエラーが出てうまく接続できませんでした。

https://qiita.com/taishin/items/a32b4ac2c3f73cd02abb

## ハンズオンのための事前準備

### ハンズオン資料のClone
まず、本リポジトリをcloneしてください。gitコマンドが使えない場合は、下記画面のようにzipでダウンロード、展開を行って下さい。

![image](../images/git-zip-download.png)

### StorageClassの作成

下記コマンドを行い、`standard` のStorageClassを作成してください。

```
$ cd docs\#1-ApplicationDeployment\kubernetes-prepared 
$ kubectl apply -f aws-storageclass.yaml
storageclass.storage.k8s.io "standard" created

$ kubectl get storageclass
NAME                 PROVISIONER             AGE
standard (default)   kubernetes.io/aws-ebs   54m
$
```

正常に作成されると、 `kubectl get storageclass` で、 `standard` が表示されます。
