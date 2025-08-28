# 🏋️‍♂️ Fitness Booking API

A simple **fitness studio booking system** built with **FastAPI**.  
This project was built as part of a Python Developer Assignment to demonstrate skills in backend development, API design, validation, and testing.

---

## ✨ Features
- **View available fitness classes** (`GET /classes`) with timezone support
- **Book a spot in a class** (`POST /book`)
- **View bookings** (`GET /bookings`)
- **Filter bookings by client email** (`GET /bookings?email=...`)
- Automatic **slot management** (reduces available slots when booked)
- Clean, modular code (separate `main.py`, `models.py`, `database.py`)
- **Pydantic validation** including email format check
- Interactive API documentation with **Swagger UI** (`/docs`) and **ReDoc** (`/redoc`)
- Basic **unit tests** with pytest

---

## 🛠️ Tech Stack
- **FastAPI** – API framework  
- **Pydantic** – Data validation  
- **JSON files** – Lightweight persistence (no DB setup needed)  
- **Python 3.11+**  
- **Pytest** – Unit testing framework  

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/<your-username>/fitness-booking-api.git
cd fitness-booking-api
````

### 2. Create virtual environment

```bash
python -m venv venv
# On Linux/Mac
source venv/bin/activate
# On Windows
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the server

```bash
uvicorn main:app --reload
```

### 5. Open in browser

* Swagger docs → [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
* ReDoc → [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

## 📦 Sample Seed Data

### `data/classes.json`

```json
[
  {
    "name": "Yoga",
    "datetime": "2025-08-28T07:00:00+05:30",
    "instructor": "Priya Sharma",
    "available_slots": 10
  },
  {
    "name": "Zumba",
    "datetime": "2025-08-28T18:00:00+05:30",
    "instructor": "Rahul Verma",
    "available_slots": 15
  },
  {
    "name": "HIIT",
    "datetime": "2025-08-29T06:30:00+05:30",
    "instructor": "Neha Singh",
    "available_slots": 12
  }
]
```

### `data/bookings.json`

```json
[]
```

---

## 📌 API Endpoints

### 1. Root

**GET /**
Returns HTML instructions and links to `/docs` and `/redoc`.

---

### 2. Classes

**GET /classes?tz=Asia/Kolkata**

* Returns a list of available classes in the requested timezone.
* Query parameter `tz` is optional, with dropdown options:

  * `Asia/Kolkata`
  * `UTC`
  * `America/New_York`
  * `Europe/London`

✅ Example Response:

```json
[
  {
    "name": "Yoga",
    "datetime": "2025-08-28T01:30:00+00:00",
    "instructor": "Priya Sharma",
    "available_slots": 10
  }
]
```

---

### 3. Bookings

**GET /bookings**
Returns all bookings.

**GET /bookings?email=[user@example.com](mailto:user@example.com)**
Filters bookings by email.

✅ Example Response:

```json
[
  {
    "booking_id": 1,
    "class_name": "Yoga",
    "client_name": "Alice",
    "client_email": "alice@example.com"
  }
]
```

---

### 4. Book a Class

**POST /book**
Request body:

```json
{
  "class_name": "Yoga",
  "client_name": "Alice",
  "client_email": "alice@example.com"
}
```

✅ Example Response:

```json
{
  "booking_id": 1,
  "class_name": "Yoga",
  "client_name": "Alice",
  "client_email": "alice@example.com"
}
```

Handles errors:

* ❌ `404` if class not found
* ❌ `400` if no slots available
* ❌ `422` if email format is invalid

---

## 🧪 Running Tests

Tests are written with **pytest**.

Run:

```bash
pytest -v
```

### Included Tests

* ✅ `/` root loads successfully
* ✅ `/classes` returns list of dictionaries with correct keys
* ✅ `/book` creates a booking successfully
* ✅ `/bookings?email=...` returns correct booking

---

## 🎯 Future Improvements

* Replace JSON storage with SQLite or PostgreSQL
* Add authentication for clients
* Class scheduling with recurrence
* Admin dashboard for managing instructors and slots

---

## 📄 License

MIT License – free to use and modify.

```

## Author 👤

**Shivay Bajaj**

- GitHub: https://github.com/IDropCoins
