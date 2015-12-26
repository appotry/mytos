# 概述 Overview #
**Unix高速缓存区就是在内存中用一小部分空间来保存那些经常会被用到的磁盘块这样就不用访问同一个每次都要从硬盘上拷贝数据了，这样效率会比较低.**

**The buffering in unix is that it use a small part of memory for second device(like disk) to buffer.**



# 模拟面试 Interview simulation #

**Let’s have an interview**


**一次面试时间是固定的，我们的目标是在一段时间内怎么让面试的次数更多更好**

**Our purpose is to have interviews as many aspossible,and every interview takes the same time.**

## Picutre One ##


![http://filer.blogbus.com/6085363/6085363_1292226001s.jpg](http://filer.blogbus.com/6085363/6085363_1292226001s.jpg)



**房间C到房间B有一电梯，电梯的容量比较很小（假设为1），从房间C到房间B话费的时间也很长这个假设就像从磁盘拷贝数据到内存会比较花时间，我们要做的事情就是怎么让这种事情别太多但又可以访问到我们所需要访问的数据--Buffering**


**面试官不能叫到编号多少的面试者来面试就来面试，他必须每个人挨着一个一个问，你是不是编号为 XXXX 的面试者，就像在内存查找一个数组里值为5的元素，进程要挨着访问来查看是不是它所需要的。**

**The interviewees must make sure their locations by themselves The interviewee cannot just shout out:”Num. B2”,and the Num.B2 will not know what he is shouting.**



## Picture Two ##



![http://filer.blogbus.com/6085363/6085363_12922260086.jpg](http://filer.blogbus.com/6085363/6085363_12922260086.jpg)



**如果面试者都站在一条线上，那么这个面试官就要每个人挨着问，这样会比较话费时间**

**If the interviewers stand in a line,the interviewees have to ask the interviewers one by one,it will take a long time.**


## Picure Three ##


![http://filer.blogbus.com/6085363/6085363_1292226016x.jpg](http://filer.blogbus.com/6085363/6085363_1292226016x.jpg)



**如果这些面试者按班级站成几排，那么面试官只需要根据资料，查看这个面试官是几班在第几排他只需要去几排询问那一排的人就行了，这样就相当于散列在几排**


**We suppose that the interviewees can get the interviewer's whole infomation.If the interviewers stand in serveral lines order by their class number,and the interviewees will just ask the interviewers in one line,he can know the class number from his information paper.**


## Picture Four ##



![http://filer.blogbus.com/6085363/6085363_1292225994s.jpg](http://filer.blogbus.com/6085363/6085363_1292225994s.jpg)


### 谁应该从房间B下去 ###

**那么面试官需要面试的那个人没在房间B中，那么怎么决定去房间C换来那个需要的人呢，谁该从房间B下去呢假设每个从房间A面试出来的人都得到一张票，那么当他走出房间A的时候会得到一张票，这张票上面有个数字，是从1一直递增的，这样留在房间B中谁手上拿着的号数最小的那个人就是应该下去他就是那个最近最少被面试的人。**

### Who will go out!!!!! ###
**Ofcourse the the student who is being interviewed will not go out.When student go to room C to have interview,they will get a paper which is numbered,as in a bank you are numbered to do the businesses.And the number is increasing So the student left in room B who get the smallest number will go out!**

### 对比 ###
**房间C相当于是第二存储器（比如硬盘），房间B相当于内存，房间A里的面试官相当于进程，面试者就相当于数据。因为某个时候有可能房间B里人某些人正在房间A里就行面试，此时就是进程在访问相应的数据，比如房间B里现在还有10个人，那么有6个人就在房间A里面试，房间B里的10个人就组成一个双向链表--空闲表，空闲表是按他们手里的票的号的大小来排的，号最小的再头，这样我们每次决定谁应该下去的时候就是去双向链表的头结点，这也正如上面所说的那样。房间B里的人按班级站也相当于把这些数据散列在哈希表上，这个哈希值就是班号。**

### Comparation ###
**The Room C is sencond storage device like disk,and the Room B is actually memory and the interviewees are processes,and they call the data in disk(have an interview)Interviewers in room B,let's say that 3 interviewers are in Room A taking an interview and the rest 13 interviewers stay in Room B,taking an number,the number is actually a double link。 list.And the classes is actually a hash table for searching quickly.**