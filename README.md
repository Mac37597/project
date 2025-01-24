

import socket

def start_server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    server_socket.bind(('localhost', 8080))
    print("Server started and listening for incoming pings.")

  while True:
        message, client_address = server_socket.recvfrom(1024)
        if message.decode() == "ping":
            print(f"Ping received from {client_address}")
            server_socket.sendto("pong".encode(), client_address)

if __name__ == "__main__":
    start_server()
