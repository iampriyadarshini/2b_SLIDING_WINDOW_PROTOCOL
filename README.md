# EX.NO: 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## NAME - PRIYADARSHINI K
## REG NO - 212224100046
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## SERVER 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```

## CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```

## OUPUT
## Server.py
<img width="431" height="198" alt="image" src="https://github.com/user-attachments/assets/f3e0eb29-d94d-402d-bd88-c487eacc1efc" />

## Client.py
<img width="841" height="322" alt="image" src="https://github.com/user-attachments/assets/a5e9c36f-dabb-4a79-ab61-678dee735a9f" />




## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
