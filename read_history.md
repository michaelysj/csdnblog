阅读

# 在读的书
* 《C++ Primer 5th》(盼姐推荐，20230606)
  * 20230619 开始
  * 20230619 P32

# 左言推荐的读书方法，抄书，做笔记

# 下一本
* C++ templates 2nd (平神推荐，20230607)
* CSAPP, 深入理解计算机系统 (豆瓣评论推荐, 20230609)
* 《越绝书》
* 《计算机底层的秘密》新书，太贵了，买不起
* 《编程卓越之道》好书，太贵了，买不起
* 《软技能：代码之外的生存指南（第2版）》太贵了，买不起
* 《重构》

# 读过的书
* 20230619 《成长第二曲线》
* 20230617 《程序员的自我修养——链接、装载与库》
* 20230602 《C++标准库第二版》大概过了一遍15章之前的内容
* 20230525 《被讨厌的勇气》
* 20230423 《Effective Modern C++》
* 20230408 《软件架构秘籍》
* 20230401 《人月神话》
* 20230320 《程序员修炼之道》

# C++编程
* 20230625 [跟我学c++中级篇——省略号的巧妙应用](https://mp.weixin.qq.com/s/8x5NRfq6F5yIaHfAf0lGVQ)
* 20230605 [C++模板的特化(specialization)和偏特化(partial specialization)](https://blog.csdn.net/weixin_43744293/article/details/123919688)
* 20230525 [C++11之 std::bind | std::function](https://blog.csdn.net/weixin_36750623/article/details/84841316)

# 软技能
* 20230605 [创业者最核心的特质是韧性](https://mp.weixin.qq.com/s/hz0BqW7bl7myNU5tuBpU-g)
* 20230531 [谈谈如何写好技术文档？](https://mp.weixin.qq.com/s/rwKLgytV8X_ITcjN15rPJQ)
* 20230530 [鹅厂程序员的9个生存法则](https://mp.weixin.qq.com/s/fMRUF6d_9HDntUA9JkuY1g)

## 《程序员的自我修养——链接、装载与库》
* 用到的一些工具
  * readelf
  * nm: List symbols in [file(s)] (a.out by default).
    > nm testFunctional |grep callInsertCb | awk -F [\ ] '{print $3}' | xargs c++filt {}
  * objdump:
    > objdump -t testFunctional | awk '{print $6}' | grep _Z | xargs c++filt {}
  * c++filt
  * file: Determine type of FILEs.
  * ldd:
  * strip: remove debug info from elf file