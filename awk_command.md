awk常用命令总结

# 适合格式化匹配到的文本

# 根据代码里面time()得出的时间差转换成小时数
> awk -F "costMs:" '{print ("hours:")($2)/60/60/1000}
  * 输出结果 hours:48.0006

## 同时使用多个分隔符，用|来区别不同的分隔符
  > cat tmm_auto.log |grep "objTypeId=" | awk -F'tabId=|objId=0-B,|, counterID=' '{print $3}'
  > A-SBC_ORIG_2.2.2.30_ASBCaaaa_3GPP-UTRAN-FDD