# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
##### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

##### Server:
```
import socket
s=socket.socket()
s.connect(("localhost",8000))
while True:
    ip=input("Enter logical address:")
    s.send(ip.encode())
    print("MAC address :",s.recv(1024).decode())
```
## OUPUT - ARP

client:
<img width="1135" height="157" alt="Screenshot 2025-09-22 105755" src="https://github.com/user-attachments/assets/2a0e9649-a010-4122-b011-3da3e3065e4e" />

server:
<img width="1062" height="143" alt="Screenshot 2025-09-22 105813" src="https://github.com/user-attachments/assets/1dfcf45f-055f-48ad-9154-bafaeb79cb50" />


## PROGRAM - RARP

##### Client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
##### Server:
```
import socket
s=socket.socket()
s.connect(("localhost",9000))
while True:
    ip=input("Enter MAC address:")
    s.send(ip.encode())
    print("Logical Address :",s.recv(1024).decode())
```

## OUPUT -RARP

client:
<img width="1008" height="234" alt="Screenshot 2025-09-22 110214" src="https://github.com/user-attachments/assets/338e9884-41bf-454c-8c64-82f58226c70d" />

Server:
<img width="768" height="192" alt="Screenshot 2025-09-22 110221" src="https://github.com/user-attachments/assets/5caf4987-8b95-4bc6-b575-31b3b7560189" />



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
