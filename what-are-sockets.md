# Sockets in Linux

In the simplest terms, a socket is a pseudo-file that represents a network connection. Once a socket has been created (using the proper primitives, and the proper parameters to identify the other host), writes to the socket are turned into network packets that get sent out, and data received from the network can be read from the socket.

In one regard, sockets are very similar to pipes: they look just like files to the programs using them, but do not result in read or writes to a disk; rather, they allow communicating with another program (local in the case of pipes, and possibly remote in the case of sockets). They also offer, as you mention, bidirectional communication (much like a pair of properly connected pipes could).

Finally, it is common for programs on a single machine to communicate using standard network protocols, such as TCP; it would be wasteful to go all the way to the network hardware (if any!), computing checksums, etc., just to go back to the same host: that's where Unix domains sockets come in. Those are much like regular sockets, except they connect processes on the same host rather than remote processes, and do not attempt to use any network resources at all. In this way, they are a medium of inter-process communication.
