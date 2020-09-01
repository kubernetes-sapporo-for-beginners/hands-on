# apply後、各PodのQoS Classを確認する
* Windows
```
kubectl get pod -o yaml | findstr "qos generateName"
```

* Linux
```
kubectl get pod -o yaml | grep -e "qos" -e "generateName"
```

# その後、centosのPodを用いてStep3と同様の手順でメモリ負荷増量して他Podへの影響を確認。  
ただし、このデモは失敗。