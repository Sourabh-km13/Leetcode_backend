# 🚀 LeetCode Clone Backend — Microservices Architecture

A production-style **LeetCode-like coding platform backend** built using a scalable **microservices architecture**.

This project demonstrates real-world backend engineering principles including:

- **Docker-based execution sandboxing** for running user code safely in isolated JVM, Node, and GNU environments  
- **Asynchronous evaluation pipeline** using Redis Pub/Sub for inter-service messaging  
- **Real-time updates** via WebSockets (Socket.IO)  
- **Distributed state management** with Redis and MongoDB  
- **Clear separation of concerns** across Problem, Submission, Evaluator, and Socket services  
- **Fault isolation** to prevent execution load from impacting core APIs  
- **Modular, extensible architecture** ready for future additions like job queues or API gateways  

---

# 📌 System Overview

The backend consists of **four independent microservices**, each handling a specific domain responsibility.

| Service | Responsibility |
|----------|---------------|
| **Problem-Service** | Manages coding problems and metadata |
| **Submission-Service** | Tracks and manages submission lifecycle |
| **Evaluator-Service** | Executes and evaluates user code |
| **Socket-Service** | Enables real-time communication |

Each service:
- Has its own isolated repository
- Can be deployed independently
- Can scale independently
- Communicates using HTTP & asynchronous Redis Pub/Sub

---

# 🏗️ High-Level Architecture

## 🔁 Execution Flow

1. Client requests problem from **Problem-Service**
2. User submits code → **Submission-Service**
3. Submission-Service forwards job → **Evaluator-Service**
4. Evaluator executes code safely against test cases
5. Results returned to Submission-Service
6. **Socket-Service** pushes real-time status updates to client

## 📦 Shared Infrastructure

- **MongoDB** → Persistent storage
- **Redis** → Caching, Pub/Sub messaging, Socket scaling

This architecture enables:
- Non-blocking evaluation pipeline
- Event-driven communication
- Fault isolation between services

---

# 🔧 Microservices Breakdown

---

## 📚 Problem-Service

🔗 Repository:  
https://github.com/Sourabh-km13/Problem_service  

### Responsibilities
- Create, update, delete coding problems
- Store problem statements, constraints, examples
- Manage tags, categories, difficulty
- Provide search and filtering
- Serve structured problem data

---

## 📤 Submission-Service

🔗 Repository:  
https://github.com/Sourabh-km13/Submission-Service  

### Responsibilities
- Store submission metadata
- Maintain submission states:
  - Pending
  - Running
  - Accepted
  - Wrong Answer
  - Runtime Error
- Track user submission history
- Coordinate with Evaluator-Service
- Provide analytics

Acts as the orchestration layer between user requests and code execution.

---

## ⚡ Evaluator-Service

🔗 Repository:  
https://github.com/Sourabh-km13/Evaluator-Service  

### Responsibilities
- Execute user-submitted code
- Validate against test cases
- Enforce time and memory constraints
- Return detailed execution metrics:
  - Execution time
  - Memory usage
  - Test case results
  - Error messages

### Built With
- Node.js
- TypeScript (for type-safe execution flow)

Designed to scale horizontally under heavy submission load.

---

## 🔌 Socket-Service

🔗 Repository:  
https://github.com/Sourabh-km13/Socket-Service  

### Responsibilities
- Manage WebSocket connections
- Push real-time submission updates
- Broadcast evaluation results
- Handle concurrent users
- Scale using Redis adapter

### Technologies
- Express.js
- Socket.IO
- Redis
- IORedis

---

# 🛠 Technology Stack

## Backend
- Node.js
- Express.js
- TypeScript (Evaluator-Service)

## Database & Caching
- MongoDB
- Redis

## Real-Time Communication
- Socket.IO
- socket.io-redis adapter

## Tooling
- ESLint
- Prettier
- npm

---

# 🎯 Key Engineering Highlights

- ✅ Microservices architecture
- ✅ Event-driven evaluation pipeline
- ✅ Real-time submission tracking
- ✅ Independent service scaling
- ✅ Redis-based inter-service communication
- ✅ Type-safe evaluator service
- ✅ Fault isolation between execution and storage

---

# 🚀 Running the Services

## Prerequisites
- Node.js (v14+)
- MongoDB
- Redis

## Installation (For Each Service)

```bash
check respective repository
