# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
# SERVER
## PROGRAM
```
import socket

def chat_server(host='127.0.0.1', port=65432):
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)
    print(f"Chat Server started on {host}:{port}")

    conn, addr = server_socket.accept()
    print("Connected with:", addr)

    while True:
        data = conn.recv(1024).decode()
        if not data or data.lower() == "exit":
            print("Client disconnected.")
            break
        print("Client:", data)
        message = input("You: ")
        conn.sendall(message.encode())
        if message.lower() == "exit":
            break

    conn.close()
    server_socket.close()

if __name__ == "__main__":
    chat_server()
```
## OUPUT
<img width="521" height="184" alt="Screenshot 2025-09-24 115053" src="https://github.com/user-attachments/assets/41a05e68-fc4c-4069-8dda-617ae7aae78d" />

# CLIENT
## PROGRAM
```
import socket

def chat_client(host='127.0.0.1', port=65432):
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))
    print("Connected to Chat Server. Type 'exit' to quit.")

    while True:
        message = input("You: ")
        client_socket.sendall(message.encode())
        if message.lower() == "exit":
            break
        data = client_socket.recv(1024).decode()
        if not data or data.lower() == "exit":
            print("Server disconnected.")
            break
        print("Server:", data)

    client_socket.close()

if __name__ == "__main__":
    chat_client()
```
## OUTPUT
<img width="643" height="167" alt="Screenshot 2025-09-24 115047" src="https://github.com/user-attachments/assets/c92b2a46-693e-4507-be37-3a31b573ce43" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
