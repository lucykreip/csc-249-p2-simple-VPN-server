## Client trace

lucy@LucyK-MacBook-Air csc-249-p2-simple-VPN-server % python3 client.py --message 'Hi there!'  

client starting - connecting to VPN at IP 127.0.0.1 and port 55554
connection established, sending message '127.0.0.1|65432|Hi there!'
message sent, waiting for reply
Received response: 'Hi there!' [9 bytes]
client is done!

## VPN trace

lucy@LucyK-MacBook-Air csc-249-p2-simple-VPN-server % python3 VPN.py

VPN starting - listening for connections at IP 127.0.0.1 and port 55554
Connected established with ('127.0.0.1', 64404)
Received client message: 'b'127.0.0.1|65432|Hi there!'' [25 bytes]

VPN starting - connecting to server at IP 127.0.0.1 and port 65432
connection established, sending message 'Hi there!'
message sent, waiting for reply
Received response: 'b'Hi there!'' [9 bytes]
sending 'b'Hi there!'' back to client
VPN is done!