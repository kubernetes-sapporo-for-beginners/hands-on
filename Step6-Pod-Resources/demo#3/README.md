# PODに入る
kubectl exec -it centos-noresource-deployment-※可変 /bin/bash

# メモリ消費スクリプトを作成
参考：https://note.com/ujisakura/n/n78c76059ff29
 vi test-memory.sh

 ```
#! /bin/bash
# "--bytest 200000000" is 500MB.
echo PID=$$
echo -n "[ Enter : powerup! ] , [ Ctrl+d : stop ]"
c=0
while read byte; do
   eval a$c'=$(head --bytes 200000000 /dev/zero |cat -v)'
   c=$(($c+1))
   echo -n ">"
done
echo
 ```

 # 実行
 bash ./test-memory.sh