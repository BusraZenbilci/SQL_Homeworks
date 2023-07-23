

![68747470733a2f2f722e726573696d6c696e6b2e636f6d2f517671624a7a55672e706e67](https://github.com/BusraZenbilci/SQL_Homeworks/assets/88310614/8669da81-2f21-4a01-b2ac-c2eadf8bd8ac)

# SQL_Homeworks
Bu repoda Başlangıç Seviye Veri Bilimi Patika'nın SQL derslerinin ödevleri bulunmaktadır.

## SQL Ödev 01 | WHERE ve Karşılaştırma & Mantıksal 
1) film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
   
   SELECT title, description FROM film;
   
2) film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
   SELECT *  FROM film WHERE length > 60 AND length < 75;
3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
   SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99)
4) customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
   SELECT last_name FROM customer WHERE first_name = 'Mary';
5) film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
    SELECT * FROM film WHERE length < 50 AND NOT(rental_rate = 2.99 OR rental_rate = 4.99)

## SQL Ödev 02 | BETWEEN ve IN 
1) film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
   SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99
2) actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
   SELECT first_name, last_name FROM actor 
   WHERE first_name IN ('Penelope' , 'Nick' , 'Ed');
3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
   SELECT * FROM film 
   WHERE rental_rate IN (0.99 , 2.99 , 4.99)
   AND replacement_cost IN (12.99 , 15.99 , 28.99);
## SQL Ödev 03 | LIKE ve ILIKE 


## SQL Ödev 04 | DISTINCT ve COUNT 

## SQL Ödev 05 | ORDER BY | LIMIT ve OFFSET 

## SQL Ödev 06 | Aggregate Fonksiyonlar 
## SQL Ödev 07 | GROUP BY | HAVING 
## SQL Ödev 08 | GROUP BY | HAVING 
## SQL Ödev 09 | Tablo Oluşturma | Veri Güncelleme" 
## SQL Ödev 10 | INNER JOIN 
## SQL Ödev 11 | LEFT, RIGHT, FULL JOIN 
## SQL Ödev 12 | UNION, INTERSECT ve EXCEPT 
