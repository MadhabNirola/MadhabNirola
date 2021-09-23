- Demonstrate inter-process communication between two related processes using pipe.

#include<stdio.h> #include<unistd.h> #include<sys/types.h> #define size 100
int main()
{
pid_t pid; int fd[2];
char buff[size]; int n;
pipe(fd); pid=fork(); if(pid==0)
{
close(fd[1]); n=read(fd[0],buff,sizeof(buff)-1); write(1,buff,n);

}
else
{

close(fd[0]);
write(fd[1],"Hello i am sisam\n",20);
}
return 0;
}
