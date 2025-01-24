import socket
import time

def start_client():
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    server_address = ('localhost', 8080)

    while True:
        client_socket.sendto("ping".encode(), server_address)
        print("Ping sent.")
        response, _ = client_socket.recvfrom(1024)
        print(f"Received {response.decode()}")
        time.sleep(1)

if __name__ == "__main__":
    start_client()
