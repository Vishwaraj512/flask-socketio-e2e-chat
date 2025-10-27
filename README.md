# flask-socketio-e2e-chat

# Secure Chat App with End-to-End Encryption (E2EE)

## Project 10: Cyber Security Internship Project

This project implements a real-time chat application where all messages are secured using **End-to-End Encryption (E2EE)**. The server facilitates communication and public key exchange but cannot read the message content, ensuring maximum user privacy.

### Key Technologies Used

* **Backend:** Python, Flask, Flask-SocketIO
* **Cryptography (Server):** Python's `cryptography` library (for RSA key generation and object management)
* **Cryptography (Client):** JavaScript Forge library (for client-side AES encryption/decryption)
* **Protocol:** WebSocket (via SocketIO)

### Cryptography Model

1.  **Key Generation:** Upon registration, the server generates a unique **RSA Key Pair** for the user. The Public Key is stored and shared, while the Private Key is kept secret.
2.  **Session Key:** When a user joins a room, a temporary **AES Session Key** is generated locally on the client.
3.  **E2EE Principle:**
    * **Sender:** Encrypts the plain text message using the local AES Session Key.
    * **Server:** Relays the encrypted cipher-text payload to the room *without* attempting decryption.
    * **Recipient:** Uses their identical local AES Session Key to decrypt the cipher-text and display the original message.

### Setup and Installation

1.  **Clone the Repository:**
    ```bash
    git clone
    cd secure-chat-app
    ```

2.  **Create and Activate Virtual Environment:**
    ```bash
    python -m venv venv
    # On Windows (Git Bash/MINGW64):
    source venv/Scripts/activate
    # On Linux/macOS:
    # source venv/bin/activate
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### How to Run the Application

1.  **Start the Server:** Ensure your virtual environment (`(venv)`) is active, and run:
    ```bash
    python app.py
    ```
    *(Note: If you encounter a `ModuleNotFoundError` on Windows, try running `./venv/Scripts/python.exe app.py`)*

2.  **Access the App:** Open your web browser and navigate to:
    ```
    [http://127.0.0.1:5000/](http://127.0.0.1:5000/)
    ```

3.  **Test E2EE:**
    * Open **two separate browser windows/tabs**.
    * **Window 1 (Alice):** Register "Alice", Join Room "General".
    * **Window 2 (Bob):** Register "Bob", Join Room "General".
    * Send messages between Alice and Bob to confirm successful E2EE communication.
