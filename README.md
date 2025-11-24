This is  **README section** summarizing Roboshop project with Docker + AWS + 11 microservices.

# 🚀 RoboShop – Microservices Project (Fully Dockerized)

This project is a complete **end-to-end microservices-based e-commerce application** built and deployed using modern DevOps practices.
RoboShop consists of **11 independent microservices**, each containerized with Docker and connected through custom Docker networks on an AWS EC2 instance.

## 🧱 **Tech Stack**

**DevOps & Cloud:**
Docker • Docker Networks • AWS EC2 (RHEL 9) • Shell Scripting • GitHub

**Backend Microservices:**
Node.js • Java (Maven) • Python • Go

**Databases & Queues:**
MongoDB • MySQL • Redis • RabbitMQ

**Frontend:**
Nginx (Reverse Proxy)

## 🛒 **Microservices Included**

| Service       | Technology   | Description                  |
| ------------- | ------------ | ---------------------------- |
| **Frontend**  | Nginx        | Static UI + Reverse Proxy    |
| **Catalogue** | Node.js      | Product catalogue service    |
| **User**      | Node.js      | User authentication          |
| **Cart**      | Node.js      | Manages shopping cart        |
| **Shipping**  | Java (Maven) | Shipping cost + logistics    |
| **Payment**   | Python       | Payment API                  |
| **Dispatch**  | Go           | Dispatch & notifications     |
| **MongoDB**   | Database     | Stores catalogue data        |
| **MySQL**     | Database     | Stores user & app data       |
| **Redis**     | Cache        | Stores cart sessions         |
| **RabbitMQ**  | Queue        | Payment → Dispatch messaging |

All services are **fully containerized** using Docker images and run on an **AWS EC2 t3.micro instance**.

## 🐳 **Docker Implementation**

* Created **custom Docker network** `roboshop` for internal service communication
* Built **individual Docker images** for all 11 microservices
* Used **Docker volumes** for MongoDB, MySQL, and RabbitMQ persistent storage
* Configured **health checks** and environment variables for service dependencies
* Tested communication between services (Redis, RabbitMQ, MySQL, MongoDB, etc.)

## ☁️ **AWS Setup**

* EC2 (t3.micro – RHEL 9)
* Increased volume using `growpart` + `lvextend`
* Installed Docker CE and Docker Compose
* Deployed all containers on the VM
* Configured security groups and networking

## 🔗 **Service Communication Example**

* Cart uses Redis & Catalogue
* User uses MySQL
* Payment uses RabbitMQ
* Dispatch consumes RabbitMQ messages

All services communicate using **Docker DNS** (service name = hostname).

## 📦 **Project Features**

✔ Fully containerized architecture
✔ Production-like microservice deployment
✔ Zero dependency conflicts
✔ Network-isolated microservices
✔ Persistent DB storage
✔ Clean and maintainable Dockerfiles
✔ AWS cloud deployment

## 🙌 **About This Project**

This project demonstrates:

* Docker containerization skill
* Microservice architecture understanding
* Handling service dependencies (DB, Cache, Queue)
* Cloud deployment on AWS
* Linux administration
* Troubleshooting distributed systems
