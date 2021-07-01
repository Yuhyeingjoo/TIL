# 2021/07/01: Simple File Sharing System
---
## Thread in C
### Thread?
- 프로세스 안에서의 코드 진행의 흐름, 프로세스와 스레드는 비슷한 특성을 지니고 <u>lightweigh process</u> 라고 불리기도 한다.
- 한 프로세스에서 여러 스레드는 데이타 메모리를 공유하지만 스택, pc 는 공유하지 않는다. 
- 메모리 영역을 공유하기 때문에 context switching마다 새로 로드할 필요 없다; 그래서 프로세스보다 빠르고 가볍다.
- 한 프로세스는 여러 스레드로 구성되어 있고, 스레드들은 context switching하며 동시성을 지닌다. 
### Thread function in C
~~~c
pthread_create( pthread_t *th_id, const pthread_attr_t *attr, void* 함수명, void *arg );



~~~
