# School Management API

This is a **Node.js & Express API** that allows users to manage school data. It supports adding new schools and retrieving schools sorted by their proximity to a user-specified location.

## Features
- Add new schools to the database.
- Retrieve a list of schools sorted by distance.
- Hosted backend using **Render**.
- MySQL database hosted on **Clever Cloud**.
- API tested using **Postman**.

## Technologies Used
- **Backend**: Node.js, Express.js
- **Database**: MySQL (Clever Cloud)
- **Hosting**:
  - **Backend**: Render
  - **Database**: Clever Cloud
- **Testing**: Postman

## Project Structure
```
/school-management-api
├── db.js             # Database connection setup
├── index.js         # Main entry point
│── .gitignore
│── package.json
│── README.md
```

## Database Schema

**Table Name: `schools`**
| Column     | Type        | Description                        |
|------------|------------|------------------------------------|
| id         | INT (PK)    | Auto-increment primary key       |
| name       | VARCHAR(255) | Name of the school              |
| address    | VARCHAR(255) | Full address of the school      |
| latitude   | FLOAT       | Latitude coordinate             |
| longitude  | FLOAT       | Longitude coordinate            |

## Setup & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/Ajay-oraon/school_management_api.git
cd school-management-api
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the root directory and add:
```
DB_HOST=your-mysql-host
DB_USER=your-mysql-user
DB_PASSWORD=your-mysql-password
DB_NAME=your-database-name
PORT=5000
```

### 4. Start the Server
```bash
node index.js
```
Server will run on: **`http://localhost:3000`**

## API Endpoints

### 1. Add a New School
- **Endpoint:** `POST /addSchool`
- **Description:** Adds a new school to the database.
- **Payload Example:**
```json
{
  "name": "Green Valley High School",
  "address": "123 Main Street, Springfield",
  "latitude": 37.7749,
  "longitude": -122.4194
}
```
- **Response Example:**
```json
{
  "message": "School added successfully",
  "school": {
    "id": 1,
    "name": "Green Valley High School",
    "address": "123 Main Street, Springfield",
    "latitude": 37.7749,
    "longitude": -122.4194
  }
}
```

### 2. Retrieve Schools Sorted by Distance
- **Endpoint:** `GET /listSchools`
- **Query Parameters:**
  - `latitude` (User's latitude)
  - `longitude` (User's longitude)
- **Example Request:**
```
GET http://localhost:5000/listSchools?latitude=40.7128&longitude=-74.0060
```
- **Response Example:**
```json
[
  {
    "id": 2,
    "name": "Sunrise Public School",
    "address": "456 Elm Street, New York",
    "latitude": 40.7128,
    "longitude": -74.0060,
    "distance": 0
  },
  {
    "id": 1,
    "name": "Green Valley High School",
    "address": "123 Main Street, Springfield",
    "latitude": 37.7749,
    "longitude": -122.4194,
    "distance": 4138.5
  }
]
```

## Hosted API (For Testing)
- **Backend Hosted on Render:** `[https://school-management-api-rgrz.onrender.com]`
- **Database Hosted on Clever Cloud:** MySQL

📌 **Postman Collection:** [Insert Postman Collection Link]

## Error Handling
| Status Code | Description |
|-------------|------------|
| `400` | Missing or invalid parameters |
| `500` | Database connection issues |
| `404` | Resource not found |

## Future Improvements
- Implement authentication (JWT).
- Add endpoints for updating and deleting schools.
- Integrate Google Maps API for real-time geolocation.

## Contact & Support
For any issues or suggestions, feel free to reach out via **[Your Email]**.

---

