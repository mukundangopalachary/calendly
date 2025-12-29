# Documentation

## Introduction

- The project that will be built is **Event Booking System**.

- The main goal is to learn *System Design*.

## Requirements

### Phase 1 (Core – MUST)

- Browse events
- Seat booking
- Prevent double booking
- Booking generation
- Auth (email/password)

### Phase 2 (Extension – OPTIONAL)

- OAuth
- Payments
- Archival cleanup jobs

## Data Models (PostgreSQL)

 **Users**

```
user_id(Primary Key, auto generated)
user_name(Not null)
email(Not Null)
password_hashed(Not Null)
joinedAt
```

**Event**

```
event_id(Primary Key)
event_title
start_time
end_time
ticket_fare
```

**Seat**
```
seat_id (PK)
event_id (FK)
seat_number
status (AVAILABLE / BOOKED)
UNIQUE(event_id, seat_number)

```

**Booking**

```
booking_id(Primary Key)
user_id(Foreign Key)
event_id(Foreign Key)
seat_id(Foreign key)
status(CONFIRMED/CANCELLED)
created_at
```

## Cache


### Login/Sign Up

- OTP
- Rate Limit
- User BlackList
- JWT ID, Refresh Tokens will be in the HttpOnly Cookie and the CSRF Token in each response
- Cache the JTI for logging out.

## Booking Workflow

-Begin
- User selects an Event
- User selects a Seat
- The seat is locked(cached) or queued.
- Begin DB Transaction
- Validate Seat availability
- Insert Booking
- Mark seat as booked 
- commit 
- release lock


## Tools

### Languages & Frameworks
- Java / SpringBoot
- JavaScript / React.js 

### Open Source Tools:

Docker
RabbitMQ(Message Queues)
PostgreSQL(Database Engine)
Redis(Caching)
HAProxy(Load Balancer)
Nginx(Reverse Proxy)
Coraza(WAF)
