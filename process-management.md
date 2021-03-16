# Linux processes, init, fork/exec, ps, kill, fg, bg, jobs

Kernel Space - User Space  
Process number 0 is the kernel which lives in the kernel space and from there it launches the process 1 which is systemd and from there systemd gets in charge of the user space and responsible to start all processes needed  

Parent processes start child processes  
Bash => ls /home/user  
Bash process in this situation, forks itself (creates a copy) and from that copy runs exec ls /home/user  
if you run exec something, you will exit bash  

Processes can run in the foreground of background, fg or bg, to send it to the background you can execute or run your command with & at the end and it will return you the pid, when you write ``` jobs ``` you get  list of processes running in the background.  
