<style>
.tablelines table, .tablelines td, .tablelines th {
  border: 2px solid black;
  padding: 3px; 
}
</style>

# CronJob
KubernetesでCronJobを動かしてみましょう。
Jobの実行動作や一時停止制御などを行っていきます。

# 事前準備

Step1の準備ができていれば実行環境は問題ありません。
仕組みとして、CronJobで作成されたコンテナからStep1で作成されたコンテナのAPIを呼び出しているため、Step1のAPIをあらかじめ起動しておく必要があります。

# ハンズオン

ハンズ資料は、

- https://speakerdeck.com/hirose39/kubernetes-getting-started-number-2-cronjob

となります。
