

sudo apt install vim

永久显示行号
需要修改vim配置文件vimrc。
在默认情况下，用户宿主目录（~）中是没有此文件的，需要在当前用户的宿主目录中手工建立，即使用下面的命令：
vim ~/.vimrc ，在打开的vimrc文件中最后一行输入：set number 或者 set nu，然后保存退出。再次用vim打开文件时，就会显示行号了。

