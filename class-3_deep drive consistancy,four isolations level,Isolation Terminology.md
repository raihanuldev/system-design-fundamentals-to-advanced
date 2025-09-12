# class-3 | deep drive consistancy,four isolations level,Isolation Terminology

1. Immediate Consistency (Strong Consistency)
2. Eventual Consistency
3. Four Isolation Levels: Read Uncommitted, Read Committed, Repeatable Read, Serializable.
4. Isolation Terminology: Dirty Reads, Non-Repeatable Reads, Phantom Reads.
5. Types of Databases


## 1. Immediate Consistency (Strong Consistency)

- ডাটাবেসে যখনই কোনো পরিবর্তন (update/insert/delete) করা হয়, তখনই সেটা সব ইউজার/সার্ভারে সাথে সাথে দেখা যায়।
- একে **Strong Consistency** বলা হয়।
- উদাহরণ: ব্যাংক অ্যাকাউন্টে টাকা ট্রান্সফার করলে সাথে সাথেই ব্যালেন্স আপডেট হয়ে যায়।

---

## 2. Eventual Consistency

- ডাটা আপডেট করার পরপরই সব ইউজার সেই পরিবর্তন নাও দেখতে পেতে পারে।
- কিছু সময় পরে (eventually) সব জায়গায় ডাটা এক হয়ে যায়।
- এটি সাধারণত distributed systems এ ব্যবহার হয়।
- উদাহরণ: সোশ্যাল মিডিয়ার লাইক সংখ্যা সাথে সাথে সবার কাছে আপডেট নাও হতে পারে, কিন্তু কিছুক্ষণ পরে সবাই একই সংখ্যা দেখতে পায়।

---

## 3. Four Isolation Levels (SQL Transaction Isolation Levels)

👉 ট্রানজেকশন চলাকালীন ডাটার consistency ঠিক রাখার জন্য SQL চার ধরণের isolation level দেয়।

1. **Read Uncommitted**
    - অন্য ট্রানজেকশনের **uncommitted data** (যা এখনও final হয়নি) পড়তে পারে।
    - এর ফলে **Dirty Read** হতে পারে।
2. **Read Committed**
    - কেবল committed data পড়তে দেয়।
    - **Dirty Read রোধ করে**, কিন্তু **Non-Repeatable Read** হতে পারে।
3. **Repeatable Read**
    - একই ডাটাকে বারবার পড়লে একই রেজাল্ট পাওয়া যাবে।
    - **Non-Repeatable Read রোধ করে**, কিন্তু **Phantom Read** হতে পারে।
4. **Serializable**
    - সবচেয়ে strict isolation level।
    - একেবারে serial execution এর মতো কাজ করে।
    - **Dirty, Non-Repeatable, Phantom—সবকিছু প্রতিরোধ করে।**
    - কিন্তু performance ধীর হয়ে যায়।

---

## 4. Isolation Terminology

- **Dirty Read**: অন্য ট্রানজেকশনের uncommitted data পড়ে ফেলা।
- **Non-Repeatable Read**: একই query দু’বার চালালে ভিন্ন রেজাল্ট আসা (কারণ অন্য ট্রানজেকশন data পরিবর্তন করেছে)।
- **Phantom Read**: একই query চালালে নতুন row যুক্ত হয়ে যাওয়া (কারণ অন্য ট্রানজেকশন নতুন row insert করেছে)।

---

## 5. Types of Databases

1. **Relational Databases (RDBMS)** – SQL ভিত্তিক (MySQL, PostgreSQL, Oracle)।
2. **NoSQL Databases** – Schema-less, flexible (MongoDB, Cassandra, DynamoDB)।
3. **NewSQL Databases** – SQL এর সুবিধা + NoSQL এর scalability (CockroachDB, Google Spanner)।
4. **Graph Databases** – node এবং edge দিয়ে ডাটা সম্পর্ক সংরক্ষণ করে (Neo4j)।
5. **Time-Series Databases** – সময় অনুযায়ী ডাটা সংরক্ষণ করে (InfluxDB, TimescaleDB)।

---

✍️ **সংক্ষেপে**

- Consistency: Immediate বনাম Eventual
- Isolation: চার ধাপ (RU → RC → RR → S)
- Problems: Dirty, Non-Repeatable, Phantom
- Databases: RDBMS, NoSQL, NewSQL, Graph, Time-Series