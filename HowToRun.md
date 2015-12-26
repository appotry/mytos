# 怎么运行 #

> 一般我们编译一个c文件后生产exe文件，直接生产就行了，那么我们在自己的“内核”上跑的时候应该怎么办呢

> 你可以这么认为，我们编译生产boot.exe,kernel.exe等等文件（当然这里其实后缀无所谓，不要后缀也没关系，因为他不会影响文件里的内容，惯用的是boot.bin,kernel.bin)，然后我们把boot.exe,kernel.exe 放入一个软盘（这里我们使用虚拟软盘,[怎么生产虚拟软盘](http://code.google.com/p/mytos/wiki/MakeVirtualImg),虚拟软盘其实就是用程序对软盘的模拟）

> 我们把boot.exe,kernel.exe放进虚拟软盘之后，就可以使用虚拟软盘在虚拟机上运行了

> 虚拟软盘里的第一扇区是我们的写的汇编代码，通过它可以使boot.exe和kernel.exe放到我们指定的地方，通过汇编命令jump XXX，就可以跳到指定的地方执行我们的boot.exe 和kernel.exe 代码了