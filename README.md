
## 1.What is PostgreSQL?
Postgre SQL হল একটি ওপেন-সোর্স ডেটাবেস ম্যানেজমেন্ট সিস্টেম , এটি ডেটা সংরক্ষণ, ডেটা ম্যানেজ ও ডেটা এনালাইসিস করতে ব্যবহৃত হয়
উদাহরণ:
CREATE TABLE লাইব্রেরি (
লাইব্রেরি SERIAL PRIMARY KEY, লাইব্রেরি আইডি, ডার্টা অ্যাক্সেস
    নাম JAVA HEAD FIRST(200) NOT NULL, -- লেখকের নাম, খালি রাখা যাবে না
ইস্যু তারিখ DATE - গ্রাহোকারের নাম
);

## 2.Explain the primary Key and Foreign Key concepts in postgreSQL
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


## 3.How can you calculate aggregate functions like COUNT(), SUM(), and AVG() in PostgreSQL?
PostgreSQL এ COUNT() , SUM(), এবং AVG() এই aggregate function গুলো ব্যবহার করে সহজে ডাটাবেসের নির্দিষ্ট ডেটার উপর গণনা করা যায়। নিচে বাংলায় বিস্তারিতভাবে ব্যাখ্যা করা হলো: 
১. COUNT() - মোট রেকর্ডের সংখ্যা গণনা 
     এই ফাংশনটি নির্দিষ্ট একটি কলামে কতটি রিপোর্ট আছে তা বর্ণনা করে। 
Ex: SELECT COUNT (*) FORM student;
এখানে student, টেবিলের মোট রেকর্ড সংখ্যা দেখাবে।

২. SUM()- মোট যোগফল নির্ণয়
   এই ফাংশনটি কোন একটি সংখ্যার কলামের সব মানের যোগফল হিসাব করে।

Ex: SELECT SUM( marks ) FROM students;
এখানে Student টেবিলের marks কলামের সব মানে যোগ করে দেখাবে।

৩. AVG()- গড় নির্ণয় 
    এই ফাংশনটির নির্দিষ্ট একটি সংখ্যাসূচক কলামের গড় মান নির্ণয় করে।
EX: SELECT AVG( marks ) FORM student;
এখানে marks কলামের গড় মান দেখাবে।

## 4.How can you modify data using UPDATE statements?
UPDATE এর গঠন (Syntax):
UPDATE table_name
SET column1 = value1,
        column2 = value2,
        ....
WHERE Condition;

table_name : যে টেবিল আপডেট করতে হবে।
SET : যে যে কলামের মান পরিবর্তন করতে হবে। 
WHERE : এটি কোন record বা রেকর্ডগুলো পরিবর্তন করতে হবে তা নির্ধারণ করে। 

EX 1: একটি কলাম আপডেট, 
UPDATE students
SET marks = 85
WHERE id = 1;

EX 2: একাধিক কলাম আপডেট 
UPDATE students
SET name = 'Sabbir', marks = 90
WHERE id = 2;

EX 3: এটি শর্ত অনুযায়ী অনেক রেকর্ড আপডেট করতে ব্যবহৃত হয়। 
UPDATE students
SET grade = 'A'
WHERE marks >= 80;
