# 🏋️‍♀️ Fitness Studio Booking API

A lightweight FastAPI REST service for managing fitness studio operations — enabling users to browse classes, reserve slots, and track their bookings.

---

## 🚀 Setup Instructions

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/fitness_booking_api.git
   cd fitness_booking_api
    ```
2. Create and activate a virtual environment

   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```

3. Install dependencies

   ```bash
   pip install -r requirements.txt
   ```

4. Run the server

   ```bash
   uvicorn main:app --reload
   ```

👉 API will be available at:

* Homepage: [http://localhost:8000/](http://localhost:8000/)
* Swagger UI: [http://localhost:8000/docs](http://localhost:8000/docs)
* ReDoc: [http://localhost:8000/redoc](http://localhost:8000/redoc)

---

## 📚 API Endpoints

### 🔹 1. API Status

```bash
curl http://localhost:8000/
```

### 🔹 2. Get Classes

```bash
curl http://localhost:8000/classes
curl "http://localhost:8000/classes?tz=utc"
```

### 🔹 3. Get All Bookings

```bash
curl http://localhost:8000/bookings
```

### 🔹 4. Get Bookings by Email

```bash
curl "http://localhost:8000/bookings?email=test@example.com"
```

### 🔹 5. Create a Booking

```bash
curl -X POST http://localhost:8000/book \
  -H "Content-Type: application/json" \
  -d '{"class_name":"Yoga","client_name":"John","client_email":"john@example.com"}'
```

---

## 🧪 Testing

Run the test suite:

```bash
pytest -v
```

---

## 🔮 Future Enhancements

* [ ] User authentication
* [ ] Payments & email notifications
* [ ] Instructor & class management

## Author 👤

**Shivay Bajaj**

- GitHub: https://github.com/IDropCoins
