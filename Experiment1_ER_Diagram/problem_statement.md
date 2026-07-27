# ER Diagram Workshop – Submission Template

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

<img width="979" height="860" alt="image" src="https://github.com/user-attachments/assets/0d1301bd-fe64-4682-8602-8ca3d6dafd15" />


### Entities and Attributes

| Entity  | Attributes (PK, FK)                                   | Notes                           |
| ------- | ----------------------------------------------------- | ------------------------------- |
| Member  | **member_id (PK)**, name, membership_type, start_date | Stores member information       |
| Program | **program_id (PK)**, program_name                     | Fitness programs offered        |
| Trainer | **trainer_id (PK)**, name                             | Trainer details                 |
| Session | **session_id (PK)**, session_date, attendance_status  | Personal training sessions      |
| Payment | **payment_id (PK)**, amount, payment_type             | Membership and session payments |


### Relationships and Constraints

| Relationship                  | Cardinality | Participation | Notes                                         |
| ----------------------------- | ----------- | ------------- | --------------------------------------------- |
| Enrolls In (Member–Program)   | M : 1       | Total         | Members enroll in one program.                |
| Assigned To (Trainer–Program) | 1 : N       | Total         | One trainer is assigned to multiple programs. |
| Books (Member–Session)        | 1 : N       | Partial       | Members can book multiple sessions.           |
| Conducts (Trainer–Session)    | 1 : N       | Total         | One trainer conducts multiple sessions.       |
| Makes (Session–Payment)       | 1 : 1       | Total         | Each session generates one payment.           |



### Assumptions

-Every member has a unique Member ID.

-One member is enrolled in one program.

-Trainers can conduct multiple sessions.

-Attendance is recorded for every session.

-Every session has one payment record.

---

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

<img width="979" height="723" alt="image" src="https://github.com/user-attachments/assets/8313c58e-ca8b-4c17-99fa-e37a09aa7cab" />


### Entities and Attributes

| Entity  | Attributes (PK, FK)                       | Notes                  |
| ------- | ----------------------------------------- | ---------------------- |
| Member  | **member_id (PK)**, name, phone           | Library member details |
| Book    | **book_id (PK)**, title, author, category | Book details           |
| Loan    | **loan_id (PK)**, loan_date, return_date  | Loan records           |
| Room    | **room_id (PK)**, room_name, capacity     | Library rooms          |
| Event   | **event_id (PK)**, event_name, event_date | Library events         |
| Speaker | **speaker_id (PK)**, name, expertise      | Event speakers         |


### Relationships and Constraints

| Relationship                | Cardinality | Participation | Notes                                 |
| --------------------------- | ----------- | ------------- | ------------------------------------- |
| Borrows (Member–Loan)       | 1 : N       | Total         | One member can borrow multiple books. |
| Of Book (Loan–Book)         | N : 1       | Total         | Each loan belongs to one book.        |
| Reserves (Member–Room)      | 1 : N       | Partial       | Members reserve study rooms.          |
| Register For (Member–Event) | M : N       | Partial       | Members register for events.          |
| Held In (Event–Room)        | N : 1       | Total         | Events are conducted in one room.     |
| Features (Event–Speaker)    | 1 : N       | Total         | One event features multiple speakers. |


### Assumptions

-Every member has a unique Member ID.

-Books can be borrowed multiple times.

-One loan record is created per borrowed book.

-A room can host multiple events.

-Overdue fines are managed separately.

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


<img width="937" height="617" alt="image" src="https://github.com/user-attachments/assets/04e3b2d6-576c-4c68-84c2-806186cbd9fe" />




### Entities and Attributes

| Entity      | Attributes (PK, FK)                                         | Notes                   |
| ----------- | ----------------------------------------------------------- | ----------------------- |
| Customer    | **customer_id (PK)**, name, phone                           | Customer details        |
| Reservation | **reservation_id (PK)**, date, time, guests                 | Reservation information |
| Table       | **table_id (PK)**, table_number, capacity                   | Restaurant tables       |
| Waiter      | **waiter_id (PK)**, name, phone                             | Waiter details          |
| Order       | **order_id (PK)**, order_time, status                       | Food orders             |
| Dish        | **dish_id (PK)**, starter, main_course, dessert             | Menu dishes             |
| Bill        | **bill_id (PK)**, food_charge, service_charge, total_amount | Billing information     |



### Relationships and Constraints

| Relationship                     | Cardinality | Participation | Notes                                               |
| -------------------------------- | ----------- | ------------- | --------------------------------------------------- |
| Reserves (Customer–Reservation)  | 1 : N       | Total         | One customer can make multiple reservations.        |
| Assigned To (Reservation–Waiter) | N : 1       | Total         | One waiter serves multiple reservations.            |
| For (Reservation–Table)          | N : 1       | Total         | One table can have multiple reservations over time. |
| Places (Reservation–Order)       | 1 : N       | Total         | A reservation can contain multiple orders.          |
| Contains (Order–Dish)            | M : N       | Total         | An order contains multiple dishes.                  |
| Generates (Reservation–Bill)     | 1 : 1       | Total         | One reservation generates one bill.                 |


### Assumptions

-Walk-in customers are also stored as customers.

-Every reservation is assigned to one table.

-Each reservation is served by one waiter.

-Dishes are classified as Starter, Main Course, and Dessert.

-One bill is generated for each reservation.

---

