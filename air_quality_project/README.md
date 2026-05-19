# Air Quality Monitor

IoT Home Air Quality Monitor — a desktop application for managing air quality sensor devices placed in different rooms of a home.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | FastAPI (Python) |
| Frontend | Flet (Python desktop UI) |
| Database | SQLite |
| API Client | Python `requests` |

## Project Structure

```text
air_quality_project/
├── api.py           # FastAPI REST API server
├── main.py          # Flet desktop GUI frontend
├── models.py        # Pydantic request/response models
├── config.py        # Shared configuration constants
├── seed.py          # Database seeder (sample data)
├── air_quality.db   # SQLite database (auto-created)
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/devices` | List all devices (supports `?search=` filter) |
| POST | `/devices` | Add a new device |
| PUT | `/devices/{id}` | Update an existing device |
| DELETE | `/devices/{id}` | Delete a device |

### Example POST body

```json
{
  "device_id": "AQ-011",
  "model": "Air Quality Sensor",
  "status": "online",
  "room_id": 1
}
```

## Current Stage — Lab #10 (Complete)

Full CRUD cycle implemented: POST (create), GET (read), PUT (update), DELETE.

### Features
- **DataTable** displaying all devices with ID, Device ID, Model, Status, Room, and Actions columns
- **Add New** form with client-side validation (no empty fields, valid room ID)
- **Edit** button per row — opens a modal `AlertDialog` pre-filled with device data
- **Delete** button per row — opens a confirmation dialog before deleting
- **Search** field — live server-side filtering across device ID, model, status, and room name
- **SnackBar** notifications — green for success, red for errors
- **NavigationBar** — switch between Records and Add New views
- **SQLite persistence** — data survives application restart

## How to Run

### 1. Start the API server

```bash
cd air_quality_project
.venv\Scripts\python -m uvicorn api:app --host 127.0.0.1 --port 8000
```

API will be available at `http://127.0.0.1:8000/docs` (Swagger UI).

### 2. Start the Flet desktop app

In a separate terminal:

```bash
cd air_quality_project
.venv\Scripts\python main.py
```

A native desktop window will open with the device records table.

### 3. (Optional) Seed the database

```bash
cd air_quality_project
.venv\Scripts\python seed.py
```

This inserts 5 rooms and 10 sample devices.

## Project Plan

The full project plan (4-stage build) is available in `project items/PLAN.pdf`:

- **Stage 1** (Lab #9): DataTable + POST form + NavigationBar ✅
- **Stage 2** (Lab #10): Edit/Delete dialogs + Search filter ✅ *(current)*
- **Stage 3** (Activity #5): Pagination + Column sorting
- **Stage 4** (Lab #19 / Docker): Containerization
