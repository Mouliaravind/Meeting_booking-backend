# Calendar Booking Backend Service

This project is a backend calendar booking service built as part of the **Kraftshala hiring assignment**.  
It allows users to schedule meetings while strictly preventing overlapping time slots.

---

## Tech Stack

- Node.js
- JavaScript
- Express.js
- Sequelize ORM
- MySQL (SQL database)

---

##  Features

### User Management
- Create a user
- Get user details by ID

### Meeting Management
- Create a meeting
- List all meetings
- Get meeting by ID
- Update a meeting
- Delete a meeting

### Business Rule (Core Requirement)
- **No overlapping meetings are allowed**
- If a time conflict exists, the API returns:
  - **400 Bad Request**
  - Message: `"Time slot already booked"`

---

##  Project Structure

src/
app.js
server.js

config/
database.js

middlewares/
errorHandler.js

modules/
user/
model/
service/
interface/
routes/
dto/
index.js
meeting/
  model/
  service/
  interface/
  routes/
  dto/
  index.js
utils/
date.utils.js
   
This structure follows a **modular and clean architecture**:
- Routes → Controllers → Services → Models

---

##  Database Design

### Users Table
- id (Primary Key)
- name (required)
- email (required, unique)
- createdAt, updatedAt

### Meetings Table
- id (Primary Key)
- userId (Foreign Key → Users)
- title (required)
- startTime (datetime, required)
- endTime (datetime, required)
- createdAt, updatedAt

**Relationship**
- One User → Many Meetings

---

##  Meeting Conflict Logic

A meeting **cannot be created or updated** if it overlaps with an existing meeting.

### Conflict Condition
API Endpoints
Users
Create User

POST /users

{
  "name": "Aravind",
  "email": "aravind@gmail.com"
}

Get User by ID

GET /users/:id

Meetings
Create Meeting

POST /meetings

{
  "userId": 1,
  "title": "Interview",
  "startTime": "2026-02-10T10:00:00Z",
  "endTime": "2026-02-10T10:30:00Z"
}

Get All Meetings

GET /meetings

Optional filters:

userId

startDate

endDate

Get Meeting by ID

GET /meetings/:id

Update Meeting

PUT /meetings/:id

Delete Meeting

DELETE /meetings/:id

⚙️ Setup & Run Locally
1️1. Clone the repository
git clone <your-github-repo-url>
cd Meeting_booking-backend

2️. Install dependencies
npm install

3️. Setup environment variables

Create a .env file in the root directory:

PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=meeting_db


Make sure MySQL is running and the database exists.

4️. Start the server
node src/server.js


Server will start at:

http://localhost:3000

5️. Health Check

Open in browser:

http://localhost:3000/health


Response:

OK

Testing

APIs can be tested using:

Postman

Thunder Client

cURL

Recommended test flow:

Create a user

Create a meeting

Try creating an overlapping meeting (should fail)

Create a non-overlapping meeting (should succeed)

Demo Video

The demo video covers:

Project structure walkthrough

API testing using Postman

Demonstration of meeting conflict rejection

Explanation of conflict logic

 Evaluation Highlights

Clean modular architecture

Correct REST API design

Proper Sequelize usage

Strict conflict prevention logic

Meaningful validations and error handling

Author

Mouli Aravind Yendru


---

If you want next, I can help you with:
- **Demo video explanation script**
- **Exact Postman test steps**
- **How to explain conflict logic confidently in interview**
- **Deployment steps (Render)**

Just tell me 
