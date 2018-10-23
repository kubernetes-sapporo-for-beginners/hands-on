# Google Kubernetes Engine 事前準備

## クラスタの作成

下記のコマンドを実行して、GKEのクラスタを作成してください。
${project}には、利用するGCPプロジェクトのIDを指定してください。

```
$ gcloud beta container --project "${project}" clusters create "k8ssa-cluster" --zone "us-central1-a" --cluster-version "1.10.7-gke.6" --machine-type "g1-small" --image-type "COS" --disk-type "pd-standard" --disk-size "100" --scopes "https://www.googleapis.com/auth/devstorage.read_only","https://www.googleapis.com/auth/logging.write","https://www.googleapis.com/auth/monitoring","https://www.googleapis.com/auth/servicecontrol","https://www.googleapis.com/auth/service.management.readonly","https://www.googleapis.com/auth/trace.append" --num-nodes "2"
WARNING: Currently node auto repairs are disabled by default. In the future this will change and they will be enabled by default. Use `--[no-]enable-autorepair` flag  to suppress this warning.
Creating cluster k8ssa-cluster...done.
Created [https://container.googleapis.com/v1beta1/projects/nth-pad-151011/zones/us-central1-a/clusters/k8ssa-cluster].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/us-central1-a/k8ssa-cluster?project=nth-pad-151011
kubeconfig entry generated for k8ssa-cluster.
NAME           LOCATION       MASTER_VERSION  MASTER_IP      MACHINE_TYPE  NODE_VERSION  NUM_NODES  STATUS
k8ssa-cluster  us-central1-a  1.10.7-gke.6    35.184.247.36  g1-small      1.10.7-gke.6  2          RUNNING

$
```

### 補足
ノードを2台起動しています。
これでは、 `g1-small` インスタンス2台分のお金がかかってしまいます。

使っていない時は、下記コマンドでnode数を0にしておくことで、お金がかかりません。
```
gcloud container  --project "${project}"  clusters --zone "us-central1-a"  resize k8ssa-cluster --node-pool default-pool --size 0
```

必要に応じて下記コマンドで、またノード数を1以上に設定します。

```
gcloud container  --project "${project}"  clusters --zone "us-central1-a"  resize k8ssa-cluster --node-pool default-pool --size 2
```

## ハンズオンのための事前準備

### ハンズオン資料のClone
まず、本リポジトリをcloneしてください。gitコマンドが使えない場合は、下記画面のようにzipでダウンロード、展開を行って下さい。

![image](../images/git-zip-download.png)
