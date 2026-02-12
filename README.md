# 🚀 LeetCode Clone Backend — Microservices Architecture

<table>
<tr>
<td>

A production-style **LeetCode-like coding platform backend** built using a scalable microservices architecture.

</td>
<td align="right">

### 🔗 Repositories

- [Problem-Service](https://github.com/Sourabh-km13/Problem_service)
- [Submission-Service](https://github.com/Sourabh-km13/Submission-Service)
- [Evaluator-Service](https://github.com/Sourabh-km13/Evaluator-Service)
- [Socket-Service](https://github.com/Sourabh-km13/Socket-Service)

</td>
</tr>
</table>

---

## 🏗️ Architecture Diagram

> High-level system flow and service interaction

![Architecture Diagram](./architecture.png)

> Make sure you add your architecture image file as `architecture.png` in the root of this repository.

---

## 🚀 Architecture Highlights

- **Docker-based execution sandboxing** for running user code safely in isolated JVM, Node, and GNU environments  
- **Asynchronous evaluation pipeline** using Redis Pub/Sub for inter-service messaging  
- **Real-time updates** via WebSockets (Socket.IO)  
- **Distributed state management** with Redis and MongoDB  
- **Clear separation of concerns** across Problem, Submission, Evaluator, and Socket services  
- **Fault isolation** to prevent execution load from impacting core APIs  
- **Modular, extensible architecture** ready for future additions like job queues or API gateways  

---

## 📌 System Overview

The backend consists of four independent services:

| Service | Responsibility |
|----------|---------------|
| **Problem-Service** | Manages coding problems and metadata |
| **Submission-Service** | Tracks and manages submission lifecycle |
| **Evaluator-Service** | Executes and evaluates user code |
| **Socket-Service** | Handles real-time communication |

---

## 🔁 Execution Flow

1. Client fetches problem from **Problem-Service**
2. Client submits solution → **Submission-Service**
3. Submission stored and marked as `Pending`
4. Submission published to Redis queue
5. Evaluator-Service consumes job asynchronously
6. Code executed inside Docker container
7. Results returned to Submission-Service
8. Status updated in database
9. Socket-Service pushes real-time update to client

---

## 🛠 Tech Stack

**Backend**
- Node.js
- Express.js
- TypeScript

**Execution**
- Docker (isolated code sandbox)

**Database & Messaging**
- MongoDB
- Redis (Pub/Sub)

**Real-Time**
- Socket.IO

---

## 🎯 Why This Project Stands Out

- Distributed service architecture  
- Secure sandboxed execution engine  
- Event-driven submission processing  
- Real-time status broadcasting  
- Clean separation of execution and API layers  

---

## 👨‍💻 Author

**Sourabh Kumar**  
GitHub: https://github.com/Sourabh-km13
