# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

## AIM
To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.

## PROGRAM
## client:
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
print('Successfully got the file')
s.close()
print('connection closed')
```
## server:
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
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
```
## OUPUT
## client:
![Screenshot 2024-04-29 141835](https://github.com/23013743/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/161271714/697e6fd8-2ea5-4d19-a22f-cea9e7e4fd2d)


## server:

![Screenshot 2024-04-29 141841](https://github.com/23013743/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/161271714/17d33249-84d5-499d-ab01-7e8f30903fa0)


## RESULT

Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
