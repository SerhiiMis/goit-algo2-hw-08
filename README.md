# 🧪 Homework: Rate Limiting Algorithms (Sliding Window & Throttling)

## 📝 Description

In this project, we simulate a messaging system where users are rate-limited to prevent spam.  
Two algorithms are implemented:

1. **Sliding Window Rate Limiter** — precise control over number of messages within a moving time window.
2. **Throttling Rate Limiter** — enforces a fixed waiting time between messages.

---

## 📌 Task 1: Sliding Window Rate Limiter

### ✅ Functional Requirements

- Class: `SlidingWindowRateLimiter`
- Parameters:
  - `window_size = 10` seconds
  - `max_requests = 1` (max 1 message per 10s window)
- Uses `collections.deque` to track message timestamps per user
- Implements:
  - `_cleanup_window(user_id, current_time)`
  - `can_send_message(user_id) -> bool`
  - `record_message(user_id) -> bool`
  - `time_until_next_allowed(user_id) -> float`

### 🧪 Expected Output (example):

```
=== Симуляція потоку повідомлень ===
Повідомлення  1 | Користувач 2 | ✓
Повідомлення  6 | Користувач 2 | × (очікування 7.0с)
...
Очікуємо 4 секунди...

=== Нова серія повідомлень після очікування ===
Повідомлення 11 | Користувач 2 | × (очікування 1.0с)
Повідомлення 16 | Користувач 2 | ✓
```

---

## 📌 Task 2: Throttling Rate Limiter

### ✅ Functional Requirements

- Class: `ThrottlingRateLimiter`
- Parameter:
  - `min_interval = 10.0` seconds
- Tracks timestamp of the last message using `Dict[str, float]`
- Implements:
  - `can_send_message(user_id) -> bool`
  - `record_message(user_id) -> bool`
  - `time_until_next_allowed(user_id) -> float`

### 🧪 Expected Output (example):

```
=== Симуляція потоку повідомлень (Throttling) ===
Повідомлення  1 | Користувач 2 | ✓
Повідомлення  6 | Користувач 2 | × (очікування 7.3с)
...
Очікуємо 10 секунд...

=== Нова серія повідомлень після очікування ===
Повідомлення 11 | Користувач 2 | ✓
```

---

## 📂 Project Structure

```
goit-algo2-hw-08/
├── sliding_window_limiter.py
├── throttling_limiter.py
├── README.md
```

---

## 🚀 How to Run

Install Python (3.8+ recommended), then:

```bash
python sliding_window_limiter.py
python throttling_limiter.py
```

---

## ✅ Submission Instructions

1. Push your work to a public repo named `goit-algo2-hw-08`
2. Zip all files and name it: `ДЗ8_ПІБ.zip`
3. Submit:
   - a link to the GitHub repo
   - the `.zip` archive in LMS
