# 2021/07/01: Simple File Sharing System
---
- 첫 날이었는데, 네트워크나 소켓 개념이 생소했는데 바로 Q1, Q2를 시간 내에 하느라 처음엔 적응하기 힘들었다. 집에 와서 예제를 보면서 공부하니 어렴풋 개념이 잡혀가는 것 같다. 
1. 멀티스레드를 이용한 server-client echo 프로그램
2. Client가 요청한 텍스트 파일의 데이터를 client로 보내주는 프로그램
3. Server의 실행파일에서 Command Line Argument로 port번호와 directory를 입력받고, Client 실행파일의 Argument로 ip:port와 명령어을 받는다.

---
## Thread in C
### Thread?
- 프로세스 안에서의 코드 진행의 흐름, 프로세스와 스레드는 비슷한 특성을 지니고 <u>lightweigh process</u> 라고 불리기도 한다.
- 한 프로세스에서 여러 스레드는 데이타 메모리를 공유하지만 스택, pc 는 공유하지 않는다. 
- 메모리 영역을 공유하기 때문에 context switching마다 새로 로드할 필요 없다; 그래서 프로세스보다 빠르고 가볍다.
- 한 프로세스는 여러 스레드로 구성되어 있고, 스레드들은 context switching하며 동시성을 지닌다. 
### Thread function in C
~~~c
pthread_create( pthread_t *th_id, const pthread_attr_t *attr, void* func, void *arg )
~~~
-th_id: 생성된 Thread ID가 저장될 포인터.  
-attr: Attribute of the Thread. Point ton pthread_attr_t structure. If Null, default.  
-The code sequence of the new thread is executed by invoking func  
-On success, it returns 0;

~~~c
int pthread_join(pthread_t thread, void **retval);
~~~
-thread : The function wait for thread to terminate.   
-retval : If retval is not NULL, the exit status of thread is copied into <u>retval</u>
~~~c
no return void pthread_exit(void *retval);
~~~
-The function terminates the calling thread and returns values to retval 

## Socket 
### Socket?
-네트워크상 통신하는 프로그램의 종착점(endpoint). Socket을 열기 위해서 IP, Port, Protocol이 필요하다. 
데이터가 오고 가는 창구.
~~~c
int socket(int domain, int type, int protocol);
~~~
-domain : It specifies the protocol family which will be used for commucacation.  
-On success, it returns the file descriptor.
~~~c
int listen(int sockfd, int backlog);
~~~
-waiting for any client connection on socket specified by sockfd  
-backlog is the size of waiting queue
~~~c
 int accept(int sockfd, struct sockaddr *restrict addr, socklen_t *restrict addrlen);
 ~~~
-It receives connections on the waiting queue, creates a new socket for that connection 
 and returns a file descriptor reffering to that socket.
 

 
 
 
