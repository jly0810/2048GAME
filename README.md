# 项目背景
2048是一个风靡全球的益智类小游戏，通过上下左右控制来合并盘子里的数字，直到盘子里出现2048。

作品效果

![1638260641947](C:\Users\35353\AppData\Roaming\Typora\typora-user-images\1638260641947.png)

# 环境配置
Windows:

- F1：使用MinGW
  
    1. 安装编译器MinGW,https://sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/ 下载mingw-w64-install.exe 5.0.4版本,解压到本地目录，例如 C:\mingw64,然后把C:\mingw64\bin 加入到系统设置的路径里,打开命令行控制台输入g++，确认有这个命令以保证安装是成功
    2. 编译pdcurses库（开源、跨平台）,https://sourceforge.net/projects/pdcurses/files/pdcurses/3.6/pdcurs36.zip/download 下载pdcurses后解压到C:\pdcurs36目录，命令行控制台cd到 C:\pdcurs36\wincon目录，运行 mingw32-make 命令编译pdcurses库，编译成功后目录下有多个demo的exe文件以及一个pdcurses.a文件，这个文件是库文件。
    
- F2：使用VS
  
    ​     1、自行编译生成pdcurses库的.dll和.lib文件或者在https://sourceforge.net/projects/pdcurses/files/pdcurses/3.4/处下载
    
    ​     2、在环境变量中添加pdcurses.dll文件所在的文件夹路径或直接将pdcurses.dll文件放入工程的debug/release文件夹内。
    
    ​          项目配置：（1）在 ”VC++”“包含目录”中新建curses.h文件的路径。（2）“VC++”“库目录”中新建pdcurses.lib文件的路径。（3）“链接器”“输入”“附加依赖项”中输入pdcurses.lb库的名称。
    
      
    

# 编译命令
- Windows: g++ 2048.cpp C:\pdcurs36\wincon\pdcurses.a -I C:\pdcurs36\ -o 2048

# 开发步骤
1. 引入pdcurses库，绘制游戏开始界面
2. 设置游戏状态切换
3. 重启初始化游戏
4. 实现上下左右的移动
5. 游戏胜负判定



# 开发要点

1. 一次只能合并相邻的两个数字，例如 **[2 2 2 2]** ，向右合并以后是 **[空 空 4 4]** ，不是 **[空 空 空 8]**
2. 每次合并的时候，合并方向优先级高，例如 **[空 2 2 2]**，向右合并以后是 **[空 空 2 4]**，不是 **[空 空 4 2]** 
3. 判断游戏胜利或者失败
4. 每次合并以后随机新出4的概率10%

# 进阶

记录最高分

优化界面

