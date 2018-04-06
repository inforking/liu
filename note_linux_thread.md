1.  - fork(): create process 
	- exec(): load program into process
2.	- Job is an instance of a task（系统进程？？）
	- 进程：载入到内存并且正被执行的程序
		- 进程在内存中表现为：stack heap text data
## 线程的状态转换图 ##
![](https://i.imgur.com/ik69pC4.jpg)

- waiting：进程等待某个事件发生（比如等待I/O（阻塞情况下））

- ready:等待分配处理器

##
进程调度队列

- 作业队列 ：系统中所有进程（所有状态？）
- 就绪队列 ：处于ready状态，等待cpu调度的队列，一般用链表实现
- 设备队列 ：（处于waiting状态）等待特定I/O设备的队列
- 
## 上下文切换（一般看做额外开销) ##

P0->P1
  - save state into PCB0(process control block)
  - reload PCB1
  - save PCB1
  - reload PCB0
## 进程创建 ##
- 资源共享
	- 共享所有、部分、不共享
- 执行
	- 同步、异步
- 地址
	- 子进程复制父进程
	- 子进程覆盖父进程内存空间（exec，子进程覆盖掉原进程，原进程已经“死掉”，进程号没变但实质上已经是其他程序了）
