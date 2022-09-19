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
![Screenshot (152)](https://user-images.githubusercontent.com/112462605/191056139-5fb5e619-e23c-4caf-9435-23a2c5f0e4a4.png)
![Screenshot (152)](https://user-images.githubusercontent.com/112462605/191056242-a8150128-1df8-42c4-ba1f-6856a431027f.png)
