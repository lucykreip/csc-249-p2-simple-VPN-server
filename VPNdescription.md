## Overview of Application

In this implementation of a client and VPN, the client takes user input and adds a header to the user's massage that indicate the destination server's IP address and port number. This is implemented in the 'encode_message' function of the client, but concatenating the SERVER_IP, SERVER_PORT, and message together with the delimeter '|'. Using python sockets, the client then establishes a connection with the VPN, using its IP address and port number, and then sends the message. On the VPN side, the VPN server listens for connections on its specific port, and when data is received it parses it. The VPN's parse_message function handles this, using split('|', 2) to split the string on the delimeter '|' at most two times, to ensure the SERVER_IP and SERVER_PORT are extracted from the data, while leaving the rest of the string intact and not splitting too many times, say if another '|' was in the message not as a delimeter. The VPN then can use the SERVER_IP and SERVER_PORT to estabisha  connection with the server and then send the message contents directly to the destination server. The VPN then waits for a response from the server, and forwards the response back to the client.

## Client --> VPN Server message format

Sending a message from the client to the VPN includes the user's message or otherwise data to be recieved by the destination server, the destination server's port number, and the destination server's IP address. The order is IP address - port number - message. Each element is seperated by '|'. An example from this application is: '127.0.0.1|65432|Hello, world'

## VPN Server--> Client mesage format

From the VPN server to the client, the VPN is just sending back the responce from the destination server, in bytes. With the echo server example, the response is just the request repeated back. 

## Example Output

For example, given the client message '127.0.0.1|65432|Hello, world', the VPN forwards it to the correct destination server, and gets the response back: 'Hello, world'. 

## Network Layer Interaction

The application layer deals with the domain name system, if we were given a web adress instead of an IP address, this is helpful in finding the IP address of the destination server and resolving what the destination is. 

This interacts with the transport layer to provide a TCP header that contains information about the data and the destination port of the data. 

The internetwork data handles the IP address and IP protocol to figure out exactly where this message needs to go. 

## Acknowledgements

Jessica and I breifly discussed the project to get a clear understanding of what the end goal is.