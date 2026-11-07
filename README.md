# minitalk


## 📖 Description

**minitalk** is a small data exchange program that allows two processes to communicate with each other using UNIX signals.

The project consists of two programs:
- **Server** – Receives and decodes messages sent by the client.
- **Client** – Sends a string message to the server, one bit at a time.

Communication is handled using two UNIX signals:
- `SIGUSR1` – Represents the bit `0`.
- `SIGUSR2` – Represents the bit `1`.

Each character is transmitted bit by bit, allowing the client to send a complete string to the server.

The main goal of this project is to understand UNIX signals, process communication, and bitwise operations.

## 🛠️ Technologies

- C
- UNIX Signals (`SIGUSR1`, `SIGUSR2`)
- Bitwise Operations
- Process IDs (PID)
- Makefile
- Linux / UNIX

## ⚙️ Compilation

Clone the repository:

```bash
git clone <repository-url>
cd minitalk
```

Compile the project:

```bash
make
```

This generates two executables:

- `server`
- `client`

## 🚀 Usage

### 1. Start the server

Run the server:

```bash
./server
```

The server displays its PID:

```text
Server PID: 12345
```

### 2. Send a message

Open another terminal and execute the client with the server PID and your message:

```bash
./client 12345 "Hello from minitalk!"
```

The server receives and displays:

```text
Hello from minitalk!
```

## 🧠 How It Works

The communication process works as follows:

1. The server starts and waits for incoming signals.
2. The client receives the server's PID and the message as arguments.
3. Each character is converted into its binary representation.
4. The client sends each bit using `SIGUSR1` or `SIGUSR2`.
5. The server catches the signals and reconstructs the original character.
6. Once a null character (`\0`) is received, the server knows that the message is complete.

### Example

The character `A` has the following ASCII binary representation:

```text
A = 01000001
```

It is transmitted as eight signals:

```text
SIGUSR1 SIGUSR2 SIGUSR1 SIGUSR1
SIGUSR1 SIGUSR1 SIGUSR1 SIGUSR2
```

The server reconstructs the bits and displays the character.

## 📋 Makefile Commands

| Command | Description |
|---|---|
| `make` | Compiles the project |
| `make clean` | Removes object files |
| `make fclean` | Removes object files and executables |
| `make re` | Recompiles everything |

## 🎯 Project Objectives

- Understand UNIX signals and signal handling.
- Learn inter-process communication (IPC).
- Work with bitwise operators.
- Manipulate binary representations of characters.
- Understand process IDs and communication between processes.
- Improve memory management and error handling in C.

## 👨‍💻 Author

gvasylie
