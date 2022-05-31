> * 线程微观上可以看成是进程的“子任务”。
> * 线程是CPU调度的最小单位。



```C
/*在用户空间实现线程，《现代操作系统（第四版）》*/
#include<pthread>
#include<stdio.h>
#include<stdlib.h>

#define NUMBER_OF_THREADS 10

void *print_hello_world(void *tid)
{
    printf("Hello World.Greeting from thread%d\n",tid);
    pthread_exit(NULL);
}

int main(int argc,char *argv[])
{
    /*主程序创建10个线程，然后退出*/
    pthread_t threads[NUMBRR_OF_THREADS];
    int status,i;

    for(i = 0; i < NUMBER_OF_THREADS; i++)
    {
        printf("Main here.Creating thread%d\n",i);
        status = pthread_create(&thread[i],NULL,print_hello_world,(void*)i);

        if(status != 0)
        {
            printf("Oops.pthread_create returned error code%d\n",status);
            exit(-1);
        }
    }
    exit(-1);
}
```





