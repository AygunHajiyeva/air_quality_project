# Lab Work #10 — DELETE / PUT + Search

Full CRUD with Flet desktop UI:
- DataTable with Edit/Delete per row
- PUT to update, DELETE to remove (AlertDialog confirmation)
- Live search with server-side `?search=` filtering

```bash
cd air_quality_project
uvicorn api:app --port 8000 & python main.py
```