grep常用命令总结

# 适合单纯的查找或匹配文本

## 多字匹配
  > grep -e "key1" -e "key2" example.txt
## 只显示匹配到的文件名
  > grep -l "key1" ./*.txt
## 消息统计，用到了新的命令sort，第一个统计数量，第二个统计每分钟的数量
  > zgrep -n "message:0x...." IMS.log_2023061417* |grep -oE "message:0x...." | sort | uniq -c
  > grep -n "message:0x...." IMS.log_2023061417* |grep -E "message:0x...." | grep -oE "<[0-9][0-9]:[0-9][0-9]" | sort | uniq -c
## 通过callid找到对应的压缩log
  > zgrep cdr_test9637000000///1-15706@1.1.1.30 IMS_v4-sriov-sc-0.log_2023062603* |grep Ind | grep -oE ".*.log.gz" | uniq