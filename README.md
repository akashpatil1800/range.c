#include<stdio.h>
 
#include<unistd.h>
 
#include<stdlib.h>
 
#include<sys/types.h>
 
#include<sys/wait.h>
 
int main()
 
{
 
pid_t childpid;
 
int num1,num2,x;
 
int fd[2];
 
int val =0;
 
childpid = fork();
 
if(childpid = 0)
 
{
 
close(fd[1]);
 
read(fd[0],&val,sizeof(val));
 
printf("parent recieved value: %d\n", val);
 
close(fd[0]);
 
}
 
else
 
{
 
close(fd[0]);
 
printf("enter the value of x ");
 
scanf("%d",&x);
 
if(num1<1000 || num1>9999 || num2<1000 || num2>9999)

for(int i =num1; i<=num2;i++)
{
int sum =0;
for(int num =i;num>0;num/=10)
{
sum+=(num%10);
}
if(sum==8)
{

write(fd[1],&x,sizeof(x));
 
printf("child send value: %d\n", i);
 
close(fd[1]);
}
}
 
}
 
}
