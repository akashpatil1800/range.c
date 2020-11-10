#include<stdio.h>
 
#include<unistd.h>
 
#include<stdlib.h>
 
#include<sys/types.h>
 
#include<sys/wait.h>
 
int main()
 
{
 
pid_t childpid;
 
int x;
 
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
 
if (x >1 && x <8000)
 
{
 
printf( "8");
 
}
 
else
 
{
 
printf(" not 8");
 
}
 
write(fd[1],&x,sizeof(x));
 
printf("child send value: %d\n", x);
 
close(fd[1]);
 
}
 
}
