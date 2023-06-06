# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM
## DATE : 11-05-2023
## AIM :
To write a python program for creating File Transfer using TCP Sockets Links.
## ALGORITHM :
1.Start the program.
2.Get the frame size from the user.
3.To create the frame based on the user request.
4.To send frames to server from the client side.
5.If your frames reach the server, it will send ACK signal to client otherwise it will sendNACK signal to client.
6.Stop the program
## CLIENT PROGRAM :
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
## SERVER PROGRAM :
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    f = open('received_file','rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## SERVER OUTPUT :
![241628280-41bad91a-fc9a-47e9-b928-6cac4b7da7e4](https://github.com/Amruthavarshnibs/EX-10/assets/119103704/4d4962ae-cffc-41e0-a630-6093c37b9997)

## CLIENT OUTPUT :
![241628178-fd346807-1906-41ce-b5a7-86591b80d664](https://github.com/Amruthavarshnibs/EX-10/assets/119103704/c4db2e6c-a0e8-430d-b6dc-16f273468d3c)

## RECEIVED FILE :
![241628226-bbd95574-7a4b-45bc-bf33-cb1486fa9209](https://github.com/Amruthavarshnibs/EX-10/assets/119103704/e897ae82-72bf-4e0e-89f5-6b403c49dcc3)

## RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
