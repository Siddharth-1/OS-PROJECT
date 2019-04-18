#include<stdio.h>
#include<semaphore.h>
#include<pthread.h>
void *fun1();
void *fun2();
sem_t s;

void *fun1()
  {
    printf("\nhi");
  }
void *fun2()
  {
   printf("\nhii");
  }
