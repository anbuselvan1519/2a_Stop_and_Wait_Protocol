# 2a-Stop-and-Wait-Protocol.

### Name:Anbuselvan.S
### Register Number:212223240008
### Department:AIML
### Date:

## AIM:
To write a python program to perform stop and wait protocol.

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program.

## PROGRAM:
### Server:
```py
import socket

def server_program():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM) 
    server_socket.bind(('localhost', 12345)) 
    
    print("Server is listening...")

    while True:
        data, addr = server_socket.recvfrom(1024) 
        print(f"Received frame of size: {len(data)} bytes from {addr}")

        server_socket.sendto(b'ACK', addr)
        print("Sent ACK to client.")

if __name__ == '__main__':
    server_program()
```

### Client:
```py
import socket

def client_program():
    frame_size = int(input("Enter the frame size (in bytes): "))
    
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    frame = b'A' * frame_size 
    
    server_address = ('localhost', 12345)
    
    try:
        print("Sending frame to server...")
        client_socket.sendto(frame, server_address)
        
        data, addr = client_socket.recvfrom(1024)  
        print("Received ACK from server:", data.decode())
    
    finally:
        client_socket.close()

if __name__ == '__main__':
    client_program()
```
## OUTPUT:
### Server:
![Screenshot 2024-09-24 083504](https://github.com/user-attachments/assets/b06c9886-7b64-4145-b23a-4035f6686046)

### Client:
![Screenshot 2024-09-24 083441](https://github.com/user-attachments/assets/6be8f338-33b9-49b0-875f-a3ffb25f1721)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
