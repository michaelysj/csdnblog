开始学习Python

# 安装PyCharm 2023.1.1 (Commnunity Edition)
## 下载IDE: pycharm-community-2023.1.1.exe
## 下载解释器(interpreter): python-3.9.13-amd64.exe
# 学习python turtle 库
```python
import turtle
for i in range(5):
    turtle.penup()
    turtle.goto(0, -20*(i+1))
    turtle.pendown()
    turtle.circle(20*(i+1))
turtle.done()
```
## 如下图所示
![同心圆](images/tongxinyuan.png)