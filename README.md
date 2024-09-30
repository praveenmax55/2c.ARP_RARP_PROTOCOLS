# EX.NO:2c                SIMULATING ARP /RARP PROTOCOLS

## AIM
To write a python program for simulating ARP protocols using TCP.
## NAME: Praveen D
## REG.NO:212222240076

## ALGORITHM:
### Client:
1. Start the program</br>
2. Using socket connection is established between client and server.</br>
3. Get the IP address to be converted into MAC address.</br>
4. Send this IP address to server.</br>
5. Server returns the MAC address to client.</br>
### Server:
1. Start the program</br>
2. Accept the socket which is created by the client.</br>
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.</br>
4. Read the IP address which is send by the client.</br>
5. Map the IP address with its MAC address and return the MAC address to client.</br>

## PROGRAM - ARP
### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## PROGRAM - RARP
### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
```
### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT - ARP
![CN output 2 c1](https://github.com/user-attachments/assets/dee70649-6ab7-432e-9df0-f89cb3161922)


## OUPUT -RARP
![CN output 2 c2](https://github.com/user-attachments/assets/dbbc30ca-c440-4da8-aed2-a97d5cefcd86)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
