#include<stdio.h>
#include<pthread.h>
#include<stdlib.h>
#include<unistd.h>
#define MIN_PID 100
#define MAX_PID 1000
int main()
{
    int pid[MAX_PID - MIN_PID];
    int Allocate_Map();
    int Allocate_PID();
    void Release_PID(int pid);
    int Allocate_Map()
   {
    //Sets range for pid range
   //int pid[MAX_PID - MIN_PID]; 
   //returns -1 if pid is unsuccesful
   if(pid == NULL)
    {
       return -1; 
    }
   //sets all pid to 0, which indicates the process if of i is available
   for(int i=0; i<sizeof(pid); i++)
   {
   pid[i] = 0;
   } 
   //return 1 if pid is succesful
   return 1;
   }  
   int Allocate_PID()
   {    
   if(pid == NULL)
   {
   printf("\n PID MANAGER IS NOT INITIALISED ");
   return -1;
   }
   //pidNo is used to determine if the pid was allocate
   int pidNo =-1; 
   //Sets values to 1 to indicate the pid is currently in use.
   for(int i=0; i<sizeof(pid); i++)
   {      
   if(pid[i] == 0)
   {
   pid[i] = 1; 
   //Adds value to pidNo to determine for loop was executed.
   pidNo = i + MIN_PID;
   break;
   }
   }  
   //If for loop was not executed, prints error
   if(pidNo == -1)
   {
   printf("\n UNABLE TO ALLOCATE PID");
   } 
   return pidNo;
   } 
   void Release_PID(int pidNo)
   {     
   if(pid == 0)
   {
   printf("\n PID MANAGER IS NOT INITIALISED ");
   return;
   }  
   if(pidNo < MIN_PID || pidNo > MAX_PID)
   {
   printf("GIVEN PID IS OUT OF RANGE");
   }
   int newPid = pidNo - MIN_PID; 
   if(pid[newPid] == 0)
   {
   printf("\n PID",newPid," IS ALREADY RELEASED ");
   return;
   }   
   pid[newPid]=0;
   } 
   void sleep()
   {
      int x= rand()%10; //here rand function is used to generate a random no between 0 to 9
	  printf("%d \n",x);
	  sleep(x);	
   }    
   void test()
   {
   	 int b=0;
   	 a[b]= alloacate_PID();
   	 sleep();
   	 release_PID(a[b]);
   }
   Allocate_Map();
   printf("ALLOCATE PID : %d \n",Allocate_PID());
   printf("ALLOCATE PID : %d \n",Allocate_PID());
   printf("Releasing PID : %d \n", 100);
   Release_PID(100);
   printf("Allocate PID : %d \n",Allocate_PID());
   int c;
   pthread_t th[100];
   Allocate_Map();
   //Creating 100 threads
   for(c=0;c<100;c++)
   {
   	pthread_create(&th[c],NULL,test,NULL);
   }
   for(c=0;c<100;c++)
   {
   	pthread_join(th[c],NULL);
   	
   }
}
