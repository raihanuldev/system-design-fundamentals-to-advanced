# 💻What is Database Transaction. class 2

---

## 🧾 **Database Transaction (ডেটাবেস লেনদেন) কী?**

একটি **Transaction** হল এমন একটি ক্রিয়াকলাপের সেট যা ডেটাবেসে একসাথে সম্পন্ন হয় — সম্পূর্ণ না হলে কিছুই হয় না।

📌 উদাহরণ:

একটি ব্যাংক একাউন্ট থেকে টাকা কেটে অন্য একাউন্টে পাঠানো —

- টাকা কাটাও ✅
- টাকা জমাও ✅
- এই দুইটা একসাথে না হলে ডেটা **corrupt** হতে পারে।

---

## 🔄 **Transaction Steps (লেনদেনের ধাপসমূহ)**

```
[BEGIN] ➜ [EXECUTE] ➜ [COMMIT or ROLLBACK]

```

| ধাপ | বর্ণনা |
| --- | --- |
| `BEGIN` | লেনদেন শুরু |
| `EXECUTE` | এক বা একাধিক অপারেশন (ডেটাবেসে পড়া/লেখা) |
| `COMMIT` | সব সফল হলে স্থায়ীভাবে সংরক্ষণ |
| `ROLLBACK` | কোনো সমস্যা হলে আগের অবস্থায় ফেরত |

---

## ✅ **ACID Properties of Transaction**

Transaction যেন নির্ভরযোগ্য হয়, সেজন্য নিচের ৪টি নিয়ম মানা হয়:

| Property | বাংলা ব্যাখ্যা |
| --- | --- |
| **A - Atomicity** | সব কাজ একসাথে হবে, না হলে কিছুই হবে না |
| **C - Consistency** | ডেটাবেসের নিয়ম ভাঙবে না |
| **I - Isolation** | একাধিক লেনদেন একে অপরকে প্রভাবিত করবে না |
| **D - Durability** | একবার কমিট হলে কোনোভাবেই মুছে যাবে না |

---

## 💰 **Bank Example Diagram:**

```
User A: Account Balance = 500
User B: Account Balance = 300

Transaction:
1. A → B = 100 টাকা ট্রান্সফার

[BEGIN]
→ A থেকে 100 টাকা কাটল
→ B তে 100 টাকা যোগ করল
[COMMIT]

Final:
User A = 400
User B = 400

```

---

## 🔍 **Transaction States:**

```
[Active] ➜ [Partially Committed] ➜ [Committed]
             ⬋
          [Failed] ➜ [Aborted]

```

| State | ব্যাখ্যা |
| --- | --- |
| **Active** | ট্রান্স্যাকশন চলছে |
| **Partially Committed** | সব কাজ শেষ, কিন্তু এখনও কমিট হয়নি |
| **Committed** | সফলভাবে সংরক্ষিত |
| **Failed/Aborted** | সমস্যা হয়েছে, তাই রোলব্যাক হয়েছে |

---

## ⚙️ **System Design Context এ কেন গুরুত্বপূর্ণ?**

- Large scale system এ consistency রক্ষা করতে দরকার
- Replication বা distributed system এ একাধিক ডেটাবেসে ACID মানা চ্যালেঞ্জিং
- Transaction fail হলে fallback strategy থাকতে হয় (যেমন: retry queue, event sourcing)

---

## 📦 **Bonus: Replication ও High Traffic Management**

- **Replication:** একাধিক সার্ভারে ডেটা কপি করে রাখা হয় → Load balancing ও Fault tolerance
- **Eventual Consistency:** সব ডেটা একসাথে update হবে না, তবে শেষ পর্যন্ত consistent হবে