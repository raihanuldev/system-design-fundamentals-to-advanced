# 📘 Class – 4 | Fundamentals of Database & Introduction of SQL

## 1. **DDL (Data Definition Language)**

👉 ডাটাবেসের **স্ট্রাকচার (structure)** তৈরি বা পরিবর্তন করতে ব্যবহার হয়।

**Keywords:** `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.

- `CREATE` → নতুন টেবিল বা ডাটাবেস বানানো
- `ALTER` → টেবিলের কলাম যোগ/বাদ/পরিবর্তন করা
- `DROP` → টেবিল বা ডাটাবেস মুছে ফেলা
- `TRUNCATE` → টেবিলের সব ডাটা মুছে ফেলা, কিন্তু টেবিল থাকে

✍️ Example:

```sql
CREATE TABLE students (
   id INT PRIMARY KEY,
   name VARCHAR(50),
   age INT
);

ALTER TABLE students ADD email VARCHAR(100);
DROP TABLE students;

```

---

## 2. **DML (Data Manipulation Language)**

👉 টেবিলের ভেতরে ডাটা ইনসার্ট, আপডেট, ডিলিট করতে ব্যবহার হয়।

**Keywords:** `INSERT`, `UPDATE`, `DELETE`.

✍️ Example:

```sql
INSERT INTO students (id, name, age) VALUES (1, 'Raihan', 22);
UPDATE students SET age = 23 WHERE id = 1;
DELETE FROM students WHERE id = 1;

```

---

## 3. **GROUP BY**

👉 এক বা একাধিক কলামের ভিত্তিতে ডাটা গ্রুপ করতে ব্যবহার হয়।

👉 সাধারনত `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` এর সাথে ব্যবহার হয়।

✍️ Example:

```sql
SELECT age, COUNT(*)
FROM students
GROUP BY age;

```

📌 এখানে প্রতিটি বয়স অনুযায়ী কয়জন স্টুডেন্ট আছে তা দেখাবে।

---

## 4. **JOIN (Joining Queries)**

👉 একাধিক টেবিল থেকে ডাটা একসাথে আনার জন্য ব্যবহার হয়।

### Types of JOIN:

- **INNER JOIN** → মিল পাওয়া রেকর্ডগুলো আনে
- **LEFT JOIN** → বাম টেবিলের সব ডাটা আনে, ডান টেবিলে না থাকলে NULL দেখায়
- **RIGHT JOIN** → ডান টেবিলের সব ডাটা আনে
- **FULL OUTER JOIN** → দুই টেবিলের সব ডাটা আনে

✍️ Example:

```sql
SELECT students.name, departments.dept_name
FROM students
INNER JOIN departments
ON students.dept_id = departments.id;

```

---

## 5. **ORDER BY**

👉 রেজাল্টকে সাজানোর জন্য ব্যবহার হয়।

- `ASC` = ascending (ছোট → বড়)
- `DESC` = descending (বড় → ছোট)

✍️ Example:

```sql
SELECT * FROM students ORDER BY age ASC;

```

---

## 6. **LIMIT & OFFSET**

👉 **LIMIT** = কতগুলো রেকর্ড চাই তা নির্ধারণ করে।

👉 **OFFSET** = শুরু থেকে কয়টা বাদ দিয়ে দেখাবে।

✍️ Example:

```sql
SELECT * FROM students LIMIT 5;   -- প্রথম ৫টা ডাটা
SELECT * FROM students LIMIT 5 OFFSET 10; -- ১১ নম্বর থেকে ৫টা ডাটা

```

---

## 7. **COUNT()**

👉 টেবিলে কতগুলো রেকর্ড আছে তা গণনা করে।

✍️ Example:

```sql
SELECT COUNT(*) FROM students;

```

---

## 8. **HAVING**

👉 `WHERE` এর মতো কাজ করে, কিন্তু এটি **GROUP BY** এর পরে ব্যবহার হয়।

✍️ Example:

```sql
SELECT age, COUNT(*)
FROM students
GROUP BY age
HAVING COUNT(*) > 2;

```

📌 এখানে শুধু সেই বয়স দেখাবে, যেখানে ২ জনের বেশি স্টুডেন্ট আছে।