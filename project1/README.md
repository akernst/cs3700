### High-Level Approach
After parsing the arguments, we began by creating a TCP/IP client socket. If the `-s` flag was specified, we then wrap the TCP/IP socket in an SSL wrapper, specifying to use TLSv1. After this, we set the timeout on the socket so that if the server fails we will not be stuck forever waiting. Then we connect to the server and send the initial HELLO message. At this point, we enter an event loop which reads successive messages from the server. If the message is a FIND message, we perform the count in a separae function and then reply with the necessary COUNT message. If the message is a BYE message, we print the secret flag and then exit the program.

### Challenges Faced
Overall, this assignment went quite smoothly. The only significant challenge faced was in the integration with SSL. We knew only a couple lines would have to be changed and that the important part was to wrap the socket using pythons `ssl` library, but figuring out which options we needed to specify (or not specify) took a few tries.

### Testing
Due to the straightforward and small scope of this project, testing was done entirely by hand with the help of print statements, verifying that each subcomponent of the program worked as expected initially, and then finally running the entire integration. It was easy to find failures this way for this project, but we acknowledge that more expansive unit testing may prove fruitful in future assignments. 
