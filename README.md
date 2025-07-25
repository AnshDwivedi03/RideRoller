﻿# RideRoller
# 🚗 Ride Booking Microservices System

A scalable and modular microservices-based ride booking platform built using **Node.js**, designed for interaction between **User**, **Ride**, and **Captain** services. It features secure **authentication**, **RabbitMQ** for inter-service messaging, and follows a clean architecture for maintainability and scalability.

---

## 🧱 Microservices Structure

This system includes the following independent services:

### 1. **User Service**
- Register/Login users
- JWT-based Authentication
- Book ride requests

### 2. **Captain Service**
- Register/Login captains
- Accept/reject ride requests

### 3. **Ride Service**
- Handles ride creation, assignment, and status updates
- Coordinates ride flow between users and captains

### 4. **Message Broker**
- **RabbitMQ** is used for asynchronous, decoupled communication between services.

---

## 🔐 Authentication

- Implemented using **JWT** tokens.
- Services securely verify tokens via middleware.
- Tokens are stored in HTTP-only cookies or headers.

---

## 🔁 Communication Flow (via RabbitMQ)

- When a user books a ride, the **User Service** emits a message: `ride-requested`.
- The **Ride Service** consumes this message and notifies the **Captain Service**.
- When a captain accepts a ride, it emits `ride-accepted`.
- **Ride Service** listens to `ride-accepted`, updates ride status, and notifies the **User Service**.
- Long polling or WebSocket mechanisms are used to notify users in real time.

---

## 📦 Tech Stack

| Layer              | Technology       |
|-------------------|------------------|
| Backend            | Node.js + Express |
| Messaging Queue    | RabbitMQ         |
| Authentication     | JWT              |
| Communication      | REST APIs, EventEmitter (intra-service) |
| Data Formats       | JSON             |

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/ride-booking-microservices.git
cd ride-booking-microservices
