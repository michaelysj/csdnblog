grep常用命令总结

# 适合编辑匹配到的文本

## 查找某种类型文件对应的内容，并将其替换
  > find . -name *.la | xargs -i sed -i s#/home/xxx/abcdef/#/home/yyy/abcdef/#g {}
  * 其中#为分隔符，核心规则为  sed -i s###g