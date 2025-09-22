
## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
[Uploading City Fitness Club Management (1).pdf…]()


### Entities and Attributes

| **Entity**     | **Attributes (PK, FK)**                                                                       | **Notes**                     |
| -------------- | --------------------------------------------------------------------------------------------- | ----------------------------- |
| **Member**     | MemberID (PK), Name, MembershipType, StartDate, Contact, Email                                | Stores member details.        |
| **Program**    | ProgramID (PK), ProgramName, Schedule, Duration                                               | Stores fitness programs.      |
| **Trainer**    | TrainerID (PK), Name, Specialization, Contact, Email                                          | Stores trainer details.       |
| **Session**    | SessionID (PK), SessionDate, Time, MemberID (FK), TrainerID (FK), ProgramID (FK), SessionType | Represents training sessions. |
| **Attendance** | AttendanceID (PK), SessionID (FK), MemberID (FK), Status                                      | Tracks member attendance.     |
| **Payment**    | PaymentID (PK), MemberID (FK), Amount, PaymentDate, PaymentType, ReferenceNo                  | Stores payments by members.   |

### Relationships and Constraints

| **Relationship**                 | **Cardinality**           | **Participation** | **Notes**                                                                    |
| -------------------------------- | ------------------------- | ----------------- | ---------------------------------------------------------------------------- |
| **Member–Program**               | M\:N                      | Partial           | A member can join multiple programs; a program has many members.             |
| **Program–Trainer**              | M\:N                      | Total             | A program can have multiple trainers; trainers can handle multiple programs. |
| **Member–Trainer (Personal PT)** | M\:N (via Session entity) | Partial           | Members may book multiple trainers for personal sessions.                    |
| **Member–Session**               | 1\:M                      | Partial           | A member can attend multiple sessions.                                       |
| **Trainer–Session**              | 1\:M                      | Total             | Each session is led by a trainer.                                            |
| **Program–Session**              | 1\:M (optional)           | Partial           | Sessions may belong to a program (e.g., group Yoga class).                   |
| **Session–Attendance**           | 1\:M                      | Total             | Each session has attendance records for members.                             |
| **Member–Payment**               | 1\:M                      | Total             | A member can make multiple payments (membership fees, personal sessions).    |


### Assumptions
Membership type defines validity (e.g., Monthly, Quarterly, Yearly).

Programs run on fixed schedules; members enroll beforehand.

A trainer can conduct multiple sessions in a day but not two at the exact same time.

Personal training sessions are booked separately from program classes.

Payments are recorded per member; refunds are not considered in this model.

Attendance is recorded only for sessions actually scheduled.

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
