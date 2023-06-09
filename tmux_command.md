tmux 常用命令总结

# 多窗口，防止网络断连，重新连接后不需要一个一个打开会话

tmux
Ctrl + b, c ==> New window
Ctrl + b, n ==> next window
Ctrl + b, p ==> previous window
Ctrl + b, x ==> close window

tmux new -s <session-name>
tmux detach    // Ctrl + b, d ==> detach window
tmux attach -t <session-name>
tmux ls

Ctrl+b %：划分左右两个窗格。
Ctrl+b "：划分上下两个窗格。
Ctrl+b ：光标切换到其他窗格。是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键↓。
Ctrl+b ;：光标切换到上一个窗格。
Ctrl+b o：光标切换到下一个窗格。
Ctrl+b {：当前窗格与上一个窗格交换位置。
Ctrl+b }：当前窗格与下一个窗格交换位置。
Ctrl+b Ctrl+o：所有窗格向前移动一个位置，第一个窗格变成最后一个窗格。
Ctrl+b Alt+o：所有窗格向后移动一个位置，最后一个窗格变成第一个窗格。
Ctrl+b x：关闭当前窗格。
Ctrl+b !：将当前窗格拆分为一个独立窗口。
Ctrl+b z：当前窗格全屏显示，再使用一次会变回原来大小。
Ctrl+b Ctrl+：按箭头方向调整窗格大小。
Ctrl+b q：显示窗格编号。

老版本的Tmux开启鼠标模式的方法：
先按Ctrl + B， 松开以后，输入冒号，输入set mouse-mode on 回车。
新版本取消了这条命令。
在新版本中，开启鼠标模式的方法为：
先按Ctrl + B， 松开以后，输入冒号，输入set -g mouse on 回车。