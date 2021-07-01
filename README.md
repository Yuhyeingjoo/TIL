# 2021/07/01: Simple File Sharing System
---

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

th_id: 생성된 Thread ID가 저장될 포인터.
-attr: Attribute of the Thread. Point ton pthread_attr_t structure. If Null, default.
-The code sequence of the new thread is executed by invoking <u>func</u>
-On success, it returns 0;


int pthread_join(pthread_t thread, void **retval);
-thread : The function wait for <u>thread</u> to terminate. 
-retval : If <u>retval</u> is not NULL, the exit status of <u>thread</u> is copied into <u>retval</u>

noreturn void pthread_exit(void *retval);
-The function terminates the calling thread and returns values to retval 
~~~
## Socket 
### Socket?
-네트워크상 통신하는 프로그램의 종착점(endpoint). Socket을 열기 위해서 IP, Port, Protocol이 필요하다. 
데이터가 오고 가는 창구.
~~~c
int socket(int domain, int type, int protocol);
-domain : It specifies the protocol family which will be used for commucacation.
-On success, it returns the file descriptor.

int listen(int sockfd, int backlog);
-waiting for any client connection on socket specified by <u>sockfd</u>
-backlog is the size of waiting queue

 int accept(int sockfd, struct sockaddr *restrict addr, socklen_t *restrict addrlen);
 - It receives connections on the waiting queue, creates a new socket for that connection and returns a file descriptor reffering to that socket.
 
 ~~~
 
 
 
