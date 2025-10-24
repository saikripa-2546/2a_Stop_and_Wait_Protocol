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
s.connect(("localhost", 9999))
print("Connected to server.")

while True:
    data = s.recv(1024).decode()
    if not data:
        print("Server closed connection.")
        s.close()
        break
    print("Server:", data)
    s.send("Acknowledgement Received".encode())
```
```
import socket

s = socket.socket()
s.bind(("localhost", 9999))
s.listen(1)
print("Server is listening on port 9999...")

c, addr = s.accept()
print("Connected with:", addr)

while True:
    i = input("Enter a data: ")
    if not i:
        print("Closing connection.")
        c.close()
        break
    c.send(i.encode())
    ack = c.recv(1024).decode()
    if ack:
        print("Client:", ack)
    else:
        print("Client disconnected.")
        c.close()
        break
```

## OUTPUT
<img width="1287" height="292" alt="image" src="https://github.com/user-attachments/assets/c9baff7f-b8ad-4a07-89ce-8a20c17b2c59" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
