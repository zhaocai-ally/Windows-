# Windows-
使用PE系统盘进入系统，打开命令行界面，如果EFI分区还在的话，直接使用如下命令即可，其中‘C’是系统所在的盘符，在PE系统中系统盘符可能发生变化，请点开目录自行查看。

bcdboot C:\Windows
如果EFI分区已经删除，则需要重新建立一个EFI分区。首先需要在磁盘上存在一部分未分配空间（一般大于100M即可），使用PE系统中的diskgenius工具或傲梅分区助手即可。然后，使用如下命令建立EFI分区并建立引导。

diskpart 
list disk 
select disk * // 选择你要重建EFI分区的盘的编号，以数字代替*
list partition 
create partition efi size = 260 // 260M，分配给EFI分区的容量
format quick fs = fat32 
exit 
 
bcdboot C:\Windows // 注意盘符
