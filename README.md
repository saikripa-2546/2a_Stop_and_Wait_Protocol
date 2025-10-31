# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT:
```
import socket

s = socket.socket()
s.connect(("localhost", 8000))
while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print("Client received:", data)
    s.send("Acknowledgement Received".encode())
```
sever
```
import socket

s = socket.socket()
s.bind(("localhost", 8000))
s.listen(5)
c, addr = s.accept()
print("Connected with", addr)

while True:
    i = input("Enter data: ")
    c.send(i.encode())
    ack = c.recv(1024).decode()
    if ack:
        print("Server received:", ack)
    else:
        c.close()
        break
```

## OUTPUT
<img width="915" height="290" alt="image" src="https://github.com/user-attachments/assets/816e7b16-5aeb-41d1-9d9b-5e6e25cda999" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
