grep常用命令总结

# 适合单纯的查找或匹配文本

## 统计每分钟 INVITE的数量
```shell
zgrep "==MessageDump==, ==InitOrTermReqRecv For MO call(1)==:Method:1/INVITE," IMS.log_20230703191*  | grep -oE "<[0-9][0-9]:[0-9][0-9]" | uniq -c
zgrep "==MessageDump==, ==InitOrTermReqRecv For MT call(3)==:Method:1/INVITE," IMS.log_20230703191*  | grep -oE "<[0-9][0-9]:[0-9][0-9]" | uniq -c
优化版本
zgrep "==MessageDump==, ==InitOrTermReqRecv For MT call(3)==:Method:1/INVITE," IMS.log_20230703191*  | grep -oE "[0-9][0-9]:[0-9][0-9]:[0-9][0-9].[0-9][0-9][0-9]" |grep -oE "[0-9][0-9]:[0-9][0-9]" | uniq -c
```

## 通过error or warning log查看 error code是否是 UAG 的问题
>zgrep -n "MessageDump" IMS.log_20230703191* |grep "For MO" |grep RspCode |grep -v "RspCode:302" |grep -v "RspCode:200, Method:5/CANCEL" |grep -v "RspCode:200, Method:15/OPTION" | grep -oE "P-DebugInfo:\".*"

## 通过error or warning log查看 MO Call的RspCode
> zgrep -n "MessageDump" IMS.log_20230703191* |grep "For MO" |grep RspCode |grep -v "RspCode:302" |grep -v "RspCode:487" |grep -v "RspCode:200, Method:5/CANCEL" |grep -v "RspCode:200, Method:15/OPTION" | grep -oE "RspCode:..." | sort | uniq -c

## 统计每个文件中key1的数量
> zgrep -c key1 IMS_v4-sriov-sc-0.log_2023070308*

## 多字匹配
  > grep -e "key1" -e "key2" example.txt
## 只显示匹配到的文件名
  > grep -l "key1" ./*.txt
## 消息统计，用到了新的命令sort，第一个统计数量，第二个统计每分钟的数量
  > zgrep -n "message:0x...." IMS.log_2023061417* |grep -oE "message:0x...." | sort | uniq -c
  > grep -n "message:0x...." IMS.log_2023061417* |grep -E "message:0x...." | grep -oE "<[0-9][0-9]:[0-9][0-9]" | sort | uniq -c
## 通过callid找到对应的压缩log
  > zgrep cdr_test9637000000///1-15706@1.1.1.30 IMS_v4-sriov-sc-0.log_2023062603* |grep Ind | grep -oE ".*.log.gz" | uniq