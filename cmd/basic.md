简要说明：对于变量%0~%9及for里使用的%i这样的变量，可以有以下的语法：
     %~I         - 删除任何引号(")，扩充 %I
     %~fI        - 将 %I 扩充到一个完全合格的路径名
     %~dI        - 仅将 %I 扩充到一个驱动器号
     %~pI        - 仅将 %I 扩充到一个路径
     %~nI        - 仅将 %I 扩充到一个文件名
     %~xI        - 仅将 %I 扩充到一个文件扩展名
     %~sI        - 扩充的路径只含有短名
     %~aI        - 将 %I 扩充到文件的文件属性
     %~tI        - 将 %I 扩充到文件的日期/时间
     %~zI        - 将 %I 扩充到文件的大小

递归删除某类型文件
     del *.txt/s
删除当前目录下所有的txt文件, 加 /s 即可递归删除

复制文件夹
     xcopy abc bcd /i
复制文件夹abc到文件夹bcd, /i 用于忽略是文件还是目录, 如果abc为文件, 则bcd则为文件; 如果abc为目录, 则bcd为目录

打开网页
     start http://www.baidu.com