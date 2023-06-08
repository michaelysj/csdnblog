awk常用命令总结

# 根据代码里面time()得出的时间差转换成小时数
> awk -F "costMs:" '{print ("hours:")($2)/60/60/1000}
