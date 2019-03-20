# はじめに
本リポジトリは、
 [Kubernetes Sapporo for Beginners](https://sapporo-beginner-kubernetes.connpass.com/)
が実施しているハンズオン用の各種ソース、マニフェストファイル保管場所です。

# ハンズオン内容

## #1 アプリケーションを動かすぞ！
Kubernetesで実際にアプリケーションを動かしてみましょう。
主にDeployments,StatefulSetsを中心に、Pod,Service,Volumeの定義についても知識と実践を深めていきます。

[資料](./Step1-ApplicationDeployment/README.md)

## #2 こんなのもあるよ！CronJobを動かしてみよう！
Kubernetesに存在するJobスケジュールによるJob実行のCronJobを実際に動かしてみたいと思います。

[資料](./Step2-CronJob/README.md)

## #3 Podが冗長化されていても意味がない！ロードバランシングだ！

Service,Ingressについて学びましょう。
それぞれどのようなロードバランシングを行なっているのかを理解し、実運用イメージの理解を深めます。

[資料](./Step3-Service-Ingress/README.md)

## #4 設定をConfigMap／Secretとして登録しよう

設定系をKubernetesリソースに登録するConfigMap／Secretについて学びましょう。
実行環境ごとに異なる設定ファイル類を外出しすることでコンテナイメージを効率よく運用することができます。

[資料](./Step4-ConfigMap-Secret/README.md)
