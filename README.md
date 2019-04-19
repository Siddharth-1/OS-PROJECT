#include<stdio.h>
#include<semaphore.h>
#include<pthread.h>
void *fun1();
void *fun2();
sem_t s;
main()
  {
    int n,n1;
    pthread_t t1,t2;
    pthread_create(&t1,NULL,fun1,NULL);
    pthread_create(&t2,NULL,fun2,NULL);
    pthread_join(t1,NULL);
    pthread_join(t2,NULL);
    printf("Choose a number: ");
    scanf("%d",&n);
    }

void *fun1()
  {
    printf("\nhi");
  }
void *fun2()
  {
   printf("\nhii");
  }
