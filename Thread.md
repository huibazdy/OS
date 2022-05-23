> * 线程微观上可以看成是进程的“子任务”。
> * 线程是CPU调度的最小单位。



```C
int pthread_create(pthread_t *_restricted_newthread,
                  _constpthread_attr_t *_restrict_attr,
                  void *(*_start_routine)(void*),
                  void *_restrict_arg)
```



```C
#include<stdio.h>
#include<pthread.h>

void * thread_func(void* _arg)
{
    unsigned int *arg = _arg;
    printf("new thread:my tid is %u\n",*arg);
}

void main()
{
    pthread_t new_thread_id;
    pthread_create(&new_thread_id,NULL,thread_func,&new_thread_id);
    printf("main thread:my tid is %u\n",pthread_self());
    usleep(100);
}
```



