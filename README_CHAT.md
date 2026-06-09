# 💬 TCP Chat Application in C

A lightweight multi-client chat application built in **C** using **TCP sockets**, **POSIX threads (pthreads)**, and **epoll** for efficient I/O handling.

This project demonstrates client-server communication, concurrent connection handling, message broadcasting, and event-driven programming in Linux.

---

## 🚀 Features

### 🖥️ Server

* Supports multiple simultaneous clients
* Uses **POSIX threads** to handle each client independently
* Broadcasts messages to all connected clients
* Thread-safe client management using mutexes
* Automatic client disconnection handling

### 💻 Client

* Connects to the chat server via TCP
* Uses **epoll** for efficient event monitoring
* Simultaneously:

  * Reads user input from the terminal
  * Receives incoming messages from the server
* Real-time communication

---

## 🏗️ System Overview

```text
              +------------------+
              |   Chat Server    |
              |------------------|
              | Message Routing  |
              | Client Manager   |
              +--------+---------+
                       |
        +--------------+--------------+
        |              |              |
        v              v              v
   +---------+    +---------+    +---------+
   | Client  |    | Client  |    | Client  |
   |    1    |    |    2    |    |    N    |
   +---------+    +---------+    +---------+
```

The server acts as a central communication hub. Messages received from one client are broadcast to all other connected clients in real time.

---

## 📂 Project Structure

```text
.
├── server.c    # Multi-threaded chat server
├── client.c    # Epoll-based chat client
└── README.md
```

---

## 💬 Example Chat Session

### Client 1

```text
Hello everyone!
```

### Client 2

```text
-> Hello everyone!
```

### Client 2

```text
Hi there!
```

### Client 1

```text
-> Hi there!
```

---

## 🔒 Thread Safety

The server uses:

```c
pthread_mutex_t clients_mutex;
```

to safely manage shared client resources and prevent race conditions when multiple threads access the client list simultaneously.

---

## 📝 Notes

* Messages are broadcast to all connected clients except the sender.
* The server supports multiple concurrent connections.
* Client input and incoming messages are handled simultaneously using epoll.
* Default communication port: **8080**.
* Designed for Linux environments.
