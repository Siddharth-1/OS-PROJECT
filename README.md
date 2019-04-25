#include<stdio.h>
#include<semaphore.h>
#include<pthread.h>
void *funcA();
void *funcB();
sem_t s;
main()
  {
    int n,n1;
    pthread_t t1,t2;
    sem_init(&s,0,1);
    printf("Choose a number: ");
    scanf("%d",&n);
    switch(n)
     {
      case 1:
       {
	printf("\nFuncB called");
        pthread_create(&t1,NULL,funcB,NULL);
    	pthread_join(t1,NULL);
	break;
       }
      case 2:
	{
  	 printf("Choose your choice: ");
	 scanf("%d",&n1);
	 switch(n1)
	 {
	 case 1:
		{
                 printf("\nFuncA FuncA called");
                 pthread_create(&t1,NULL,funcA,NULL);
   	         pthread_create(&t2,NULL,funcA,NULL);
   		 pthread_join(t1,NULL);
          	 pthread_join(t2,NULL);
	         break;

         	}	
	 case 2:
		{
		printf("\nFuncA FuncB called");
		pthread_create(&t1,NULL,funcA,NULL);
	    	pthread_create(&t2,NULL,funcB,NULL);
   	 	pthread_join(t1,NULL);
   	 	pthread_join(t2,NULL);
		break;
		}
	 case 3:
		{
		printf("\nFunc B FuncA called");
		pthread_create(&t1,NULL,funcB,NULL);
	    	pthread_create(&t2,NULL,funcA,NULL);
    		pthread_join(t1,NULL);
   	 	pthread_join(t2,NULL);
		break;
		}
 	 case 4:
		{
		printf("\nFuncB FuncB called");
		pthread_create(&t1,NULL,funcB,NULL);
    		pthread_create(&t2,NULL,funcB,NULL);
    		pthread_join(t1,NULL);
    		pthread_join(t2,NULL);
		break;
		}
	 default:
 		{
		printf("\noff");
		break;
		}
	}
	break;
	}
        default:
        {
        printf("\nHi");
        break;
        }
    }
  }
void *funcA()
  {
	printf("\nEntered in 1\n");
    	sleep(1);
    	printf("\nExiting 1\n");
  }
void *funcB()
  {
	sem_wait(&s);
	printf("\nEntered in 2\n");
    	sleep(1);
    	printf("\nExiting 2\n");
	sem_post(&s);
  }
