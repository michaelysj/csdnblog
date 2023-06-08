阅读

# 在读的书
* 《程序员的自我修养——链接、装载与库》
  * 20230602 开始

# 下一本
* 《C++ Primer 5th》(盼姐推荐，20230606)
* C++ templates 2nd (平神推荐，20230607)

# 读过的书
* 20230602 《C++标准库第二版》大概过了一遍15章之前的内容
* 20230525 《被讨厌的勇气》
* 20230423 《Effective Modern C++》
* 20230408 《软件架构秘籍》
* 20230401 《人月神话》
* 20230320 《程序员修炼之道》

# C++编程
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