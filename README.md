#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
 
int main(void) {
  pid_t pid = fork();
 
  if(pid == 0) {
    printf("Child => PPID: %d PID: %d\n", getppid(), getpid());
    exit(EXIT_SUCCESS);
  }
  else if(pid > 0) {
    printf("Parent => PID: %d\n", getpid());
    printf("Waiting for child process to finish.\n");
    wait(NULL);
    printf("Child process finished.\n");
  }
  else {
    printf("Unable to create child process.\n");
  }
 
  return EXIT_SUCCESS;
}
![Screenshot (152)](https://user-images.githubusercontent.com/112462605/191056060-1eac98f8-b6f6-4291-89d0-b7e3a57a622f.png)
