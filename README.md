## Use instructions:

Use make to compile. \
commans working, re, clean, fclean, bonus. \

#### Initialize the server you want.
<code>./server</code> \
<code>./server_bonus</code> \

#### Run the client acording to the rules.
<code>./client</code> \
<code>./client_bonus</code> \
-this will give you further instructions for correct use. \

## Explanation

This project will make you learn about bit operations and signals in c. \
My choice was to use sigaction for both the mandatory and bonus. \
Sigaction's structur makes it have a solid comportment in most softwere version and signal would be more prone to errors. \

To use sigaction first initialize it. \
<code>.struct sigaction name; </code> \
After that i set sigactions component sa_sigaction to the &function. \
<code>name.sa_sigaction = &your_function;  </code>  \
This function is declared by me and it handles each character of the message to be sent \
It will send each bit by bit, See how in the BIT PROCESSING part down below. \
To keep the server up i used. \
<code> pause(); </code>  \
Inside a while(true) loop. \
This keeps the program at rest until a signal is received. \
The signal action is turned on once the signal is received. \
<code>Sigaction(SIGUSR1, &name, NULL); </code> \
<code>Sigaction(SIGUSR2, &name, NULL); </code> \
These will run and start processing the incoming signals in the server while the client keeps sending them. \
The variables are set as static conserving value and scope for multiple "executions" of the function <code> &your_function;  </code>  \
One byte is 8 bits so when the bit counter is 8 a condition checkings it and prints the char and resets the variables. \
Make sure you handle errors smoothly. \
The Bonus client will send the null char of the string to the server and that trigers the server to send SIGUSR1 Signal to the client. \
The client receives it, and with the same functionality executes the sigactions.sa_sigaction associated function. \
Printing the aknowledgement message and exiting the program properly. \

## BIT manipulations in minitalk
1 byte == 8 bits \

