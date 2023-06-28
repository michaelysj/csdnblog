grep常用命令总结

# 适合编辑匹配到的文本

## 查找某种类型文件对应的内容，并将其替换
  > find . -name *.la | xargs -i sed -i s#/home/xxx/abcdef/#/home/yyy/abcdef/#g {}
  * 其中#为分隔符，核心规则为  sed -i s###g
  * 如果有空格，需要加上""
  > find . -name Makefile |xargs -i sed -i s#"/home/build/SC-G-R_1_1_24_0/rhel_7_2_vnf/sip/lib/config/missing automake-1.13"#"/home/uagcicd/jenkins_CI/SC-G-R_1_1_24_0/rhel_7_2_vnf/sip/lib/config/missing automake-1.13"#g {}
## 在文件末尾添加一行 内容为 abcdefg
  * 格式: sed -i '行号i\添加的内容' 文件名
  * $: 表示最后一行
  * a: 表示添加
  * \: 表示转义换行符
  > find . -name selected_KPI | xargs -i sed -i '$a\abcdefg' {}
## 删除指定的行
> find . -name Makefile.am | xargs -i sed -i '/HSSUA_PATH/'d {}
> find . -name Makefile.am | xargs -i sed -i '/sip\/sip\/sipstack\/aricent\/sip_uatoolkit_6_0_src/'d {}