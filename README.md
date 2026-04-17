# 🔐 Secure File Management System

A multi-user file management backend built with **Java (Spring Boot)** and **MySQL** — designed to be fully AWS-compatible while running at **zero cost** locally using Docker.

---

## 🛠 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Backend** | Java 17, Spring Boot |
| **Database** | MySQL (via Docker) |
| **Object Storage** | LocalStack S3 emulator (via Docker) |
| **Cloud SDK** | AWS SDK v2 (drop-in ready for real AWS) |
| **Build Tool** | Maven |

---

## ⚙️ Prerequisites

- Java 17
- Maven
- Docker Desktop

---

## 🚀 Local Setup

### 1. Start dependencies (MySQL + LocalStack)

```bash
docker compose up -d
```

### 2. Run the application

```bash
./mvnw spring-boot:run
```

---

## 🏗 Architecture

```
Client Request
      │
      ▼
Spring Boot API
      │
      ├──► MySQL (user data, file metadata)
      │
      └──► LocalStack S3 (file storage)
               │
               └──► AWS S3 (swap in for production — no code changes)
```

> **Zero-cost design:** LocalStack emulates the AWS S3 API locally, so the same AWS SDK v2 code works in both development and production. Switching to real AWS only requires updating environment variables.

---

## 🔑 Key Features

- **Multi-user support** — isolated file access per authenticated user
- **Secure storage** — files stored in S3-compatible object storage, metadata in MySQL
- **AWS-ready** — built on AWS SDK v2; deploy to real S3/RDS with no code changes
- **Fully containerized** — MySQL and LocalStack spin up with a single command
