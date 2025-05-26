
## 1.What is PostgreSQL?
Postgre SQL হল একটি ওপেন-সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম , এটি ডেটা সংরক্ষণ, ডেটা ম্যানেজ ও ডেটা এনালাইসিস করতে ব্যবহৃত হয়
উদাহরণ:
CREATE TABLE লাইব্রেরি (
লাইব্রেরি SERIAL PRIMARY KEY, লাইব্রেরি আইডি, ডার্টা অ্যাক্সেস
    নাম JAVA HEAD FIRST(200) NOT NULL, -- লেখকের নাম, খালি রাখা যাবে না
ইস্যু তারিখ DATE - গ্রাহোকারের নাম
);

## Explain the primary Key and Foreign Key concepts in postgreSQL
primary key হলো একটি কলাম বা একাধিক কলামের সেট যা একটি টেবিলের প্রতিটি রেকর্ডকে অন্যদের থেকে আলাদা করে। এটি কখনো null বা ডুপ্লিকেট হয়না।
বৈশিষ্ট: প্রতিটি টেবিলের একটি প্রাইমারি কি থাকতে পারে।এবং এর মানগুলো অবশ্যই ইউনিক হতে হবে।এছাড়া এটি স্বয়ংক্রিয়ভাবে একটি ইন্ডেক্স তৈরি করে।

Foreign Key
Foreign Key হলো এমন একটি কলাম, যেটি অন্য একটি টেবিলের Primary Key এর দিকে রেফারেন্স করে। দুইটি টেবিলের মধ্যে রিলেশন তৈরি করা এর কাজ। 
বৈশিষ্ট্য: 
এটি মূলত Parent Table  এবং child table এর মধ্যে সম্পর্ক তৈরি করে।
এটি ডাটাবেজের ডেটা ইন্টিগ্রিটি নিশ্চিত করে যাতে কোনো ভুল রেকর্ড না ঢুকে।
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    class INTEGER
);

CREATE TABLE enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    student_id INTEGER REFERENCES students(student_id),
    course_name VARCHAR(100)
);
