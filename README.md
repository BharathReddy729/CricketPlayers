🏏 Cricketers And Players

A full-stack web application built using Java (Spring Boot), Angular, and MySQL, designed to manage cricket teams, players, and user roles.
This project was developed as a personal project to strengthen full-stack development skills, focusing on REST APIs, data persistence, and UI interaction.


---

🚀 Features

Role-Based Authentication

Implemented using JWT (JSON Web Token).

Supports two user roles:

Admin: Can add, update, or delete teams and players.

Team Admin/User: Can only release or buy players.



CRUD Operations

Create, Read, Update, and Delete functionalities for Teams and Players.

Data is managed through Spring Data JPA with MySQL integration.


Team Management

Players can be assigned to teams.

Restrictions enforced:

A player cannot belong to multiple teams.

A team’s budget cannot be exceeded.



Email Notifications

Automated email triggered when a player is successfully selected or released.


RESTful API Design

Clean and modular REST APIs for all operations.

Built using Spring Boot’s Controller-Service-Repository pattern.


Angular Frontend

Interactive UI for admins and team admins.

Seamless integration with backend REST APIs.




---

🧠 Tech Stack

Frontend: Angular
Backend: Spring Boot (Java)
Database: MySQL
Security: JWT Authentication
Build Tools: Maven
IDE: IntelliJ IDEA / VS Code


---

⚙️ Setup Instructions

Backend Setup (Spring Boot)

1. Clone the repository:

git clone https://github.com/CharanTerugu/CricketPlayers.git

cd CricketPlayers


2. Open the project in your IDE (IntelliJ/Eclipse).


3. Update application.properties with your MySQL configuration:

spring.datasource.url=jdbc:mysql://localhost:3306/cricket_db
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update


4. Run the application:

mvn spring-boot:run


5. The backend will start on: http://localhost:8080



Frontend Setup (Angular)

1. Navigate to the Angular project folder (if separate).


2. Install dependencies:

npm install


3. Run the application:

ng serve


4. The frontend will start on: http://localhost:4200




---

📬 API Highlights

Method	Endpoint	Description

POST	/any/user/authentcate
Authenticate user and generate JWT

POST	/admin/team	Create new team (Admin only)

GET	/common/teams	Fetch all teams (user &Admin)

POST	admin/addplayer	Add new player (Admin only)

PUT	/players/release	Release player from team

POST	/players/select	Assign player to a team and send email



---

🧩 Architecture Overview

Angular (Frontend)

      ↓ REST API calls
Spring Boot (Backend)

      ↓
Spring Data JPA

      ↓
MySQL Database
