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
~~~
CLIENT
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
~~~
~~~
SERVER
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~
## OUPUT - ARP
![Screenshot 2024-10-01 085805](https://github.com/user-attachments/assets/c88442d1-bb51-4c03-98ef-1766d2a5e3b0)

![Screenshot 2024-10-01 085752](https://github.com/user-attachments/assets/f88ad710-06fd-43f1-b9de-0df62742a240)

## PROGRAM - RARP
~~~
CLIENT
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
~~~
~~~
SERVER
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
~~~
## OUPUT -RARP
![Screenshot 2024-10-01 091814](https://github.com/user-attachments/assets/cd7383f1-cbf4-4a4b-a1b7-16fe18e50561)

![Screenshot 2024-10-01 091820](https://github.com/user-attachments/assets/81c9f7da-87fb-4fa9-92f7-830dddfb5348)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
