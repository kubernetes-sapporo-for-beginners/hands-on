<style>
.tablelines table, .tablelines td, .tablelines th {
  border: 2px solid black;
  padding: 3px; 
}
</style>

# ApplicationDeployment
Kubernetesにアプリケーションをデプロイしてみましょう。

そして、
 - Podとはどんなもの？
 - ReplicaSet (Deployments,StatefulSets)は何をしてくれる？
を学んでいきたいと思います。

今回は、下記のようなアプリケーションを動かします。

![image](../images/No1-app-overview.png)


# 事前準備

Kubernetesを使える環境を用意してください。

## 環境毎の事前準備

お好きな環境を使ってください。
登壇者は、EKS、AKSはあまり詳しくありません。GKEを使っています。

**[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/)**<br>
 事前準備は[prepared-gke.md](./prepared-gke.md)。
<br>
<br>
**[Amazon EKS](https://aws.amazon.com/jp/eks/)**<br>
 事前準備は[prepared-eks.md](./prepared-eks.md)。
<br>
<br>
**[Azure Kubernetes Service](https://azure.microsoft.com/ja-jp/services/kubernetes-service/)**<br>
事前準備は[prepared-aks.md](./prepared-aks.md)。
<br>
<br>
**[Docker for Windows](https://docs.docker.com/docker-for-windows/)**<br>
事前準備は[prepared-win.md](./prepared-win.md)。
<br>
<br>
**[Docker for Mac](https://docs.docker.com/docker-for-mac/)**<br>
事前準備は[prepared-mac.md](./prepared-mac.md) 



# ハンズオン

ハンズ資料は、

- [https://speakerdeck.com/hirokimatsumoto/kubernetes-hands-on-apps-for-k8ssa](https://speakerdeck.com/hirokimatsumoto/kubernetes-hands-on-apps-for-k8ssa)

となります。当日公開予定となっております。
