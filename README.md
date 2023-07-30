

![68747470733a2f2f722e726573696d6c696e6b2e636f6d2f517671624a7a55672e706e67](https://github.com/BusraZenbilci/SQL_Homeworks/assets/88310614/8669da81-2f21-4a01-b2ac-c2eadf8bd8ac)

# SQL_Homeworks
Bu repoda Başlangıç Seviye Veri Bilimi Patika'nın SQL derslerinin ödevleri bulunmaktadır. 

### SQL Ödev 01 | WHERE ve Karşılaştırma & Mantıksal 
### SQL Ödev 02 | BETWEEN ve IN 
### SQL Ödev 03 | LIKE ve ILIKE 
### SQL Ödev 04 | DISTINCT ve COUNT 
### SQL Ödev 05 | ORDER BY | LIMIT ve OFFSET 
### SQL Ödev 06 | Aggregate Fonksiyonlar 
### SQL Ödev 07 | GROUP BY | HAVING 
### SQL Ödev 08 | Tablo Oluşturma | Veri Güncelleme" 
### SQL Ödev 09 | INNER JOIN 
### SQL Ödev 10 | LEFT, RIGHT, FULL JOIN 
### SQL Ödev 11 | UNION, INTERSECT ve EXCEPT 
### SQL Ödev 12 | ALT SORGULAR

## SQL Ödev 01 | WHERE ve Karşılaştırma & Mantıksal 
1) film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
   ```
   "SELECT title, description FROM film;"
   ```
2) film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
   ```
   SELECT *  FROM film WHERE length > 60 AND length < 75;
   ```
3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
    ```
   SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99)
    ```
4) customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
   ```
   SELECT last_name FROM customer WHERE first_name = 'Mary';
   ```
5) film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
   ```
    SELECT * FROM film WHERE length < 50 AND NOT(rental_rate = 2.99 OR rental_rate = 4.99)
   ```
## SQL Ödev 02 | BETWEEN ve IN 
1) film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
   ```
   SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99
   ```
2) actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
   ```
   SELECT first_name, last_name FROM actor 
   WHERE first_name IN ('Penelope' , 'Nick' , 'Ed');
   ```
3) film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
   ```
   SELECT * FROM film 
   WHERE rental_rate IN (0.99 , 2.99 , 4.99)
   AND replacement_cost IN (12.99 , 15.99 , 28.99);
   ```
## SQL Ödev 03 | LIKE ve ILIKE 
1) country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
   ```
   SELECT country FROM country 
   WHERE country LIKE 'A%a';
   ```
2) country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
   ```
   SELECT country FROM country 
   WHERE country LIKE '_____n';
   ```
3) film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
   ```
   SELECT title FROM film 
   WHERE title ILIKE '%T'
   AND LENGTH(title) >= 4;
   ```
4) film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
   ```
   SELECT * FROM film 
   WHERE title LIKE 'C%' AND LENGTH > 90 AND rental_rate = 2.99;
   ```

## SQL Ödev 04 | DISTINCT ve COUNT 
1) film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```
SELECT DISTINCT replacement_cost
FROM film;
```
2) film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```
SELECT COUNT (DISTINCT replacement_cost)
FROM film;
```
3) film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```
SELECT COUNT (title) 
FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
4) country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
SELECT COUNT (country)
FROM country
WHERE country LIKE '_____';
```
5) city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```
SELECT COUNT (city)
FROM city
WHERE city ILIKE '%R%';
```
## SQL Ödev 05 | ORDER BY | LIMIT ve OFFSET 
1) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```
SELECT title 
FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
LIMIT 5;
```
2) film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```
SELECT title, length 
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
OFFSET 5
LIMIT 5;
```
3) customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```
SELECT * 
FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

## SQL Ödev 06 | Aggregate Fonksiyonlar 
1) film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```
SELECT ROUND(AVG((rental_rate)), 3) 
FROM film;
```
2) film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```
SELECT COUNT (title)
FROM film
WHERE title ILIKE 'c%';
```
3) film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```
SELECT MAX(length) title
FROM film
WHERE rental_rate = 0.99;
```
4) film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```
SELECT COUNT(DISTINCT replacement_cost)
FROM film
WHERE length > 150;
```
## SQL Ödev 07 | GROUP BY | HAVING 
film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```
SELECT rating
FROM film
GROUP BY rating;
```
film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```
SELECT replacement_cost, COUNT(*)
FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```
customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?  
```
SELECT store_id, COUNT(*)
FROM customer
GROUP BY store_id;
```
city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```
SELECT country_id, COUNT(*) 
FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```
## SQL Ödev 08 | Tablo Oluşturma | Veri Güncelleme" 
test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```
CREATE TABLE employee(
	id SERIAL PRIMARY KEY,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
);
```
Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```
insert into employee (id, name, email, birthday) values (1, 'Banky Valler', 'bvaller0@hatena.ne.jp', '2003-02-10');
insert into employee (id, name, email, birthday) values (2, 'Raimondo Abramamov', 'rabramamov1@wisc.edu', '2015-04-22');
insert into employee (id, name, email, birthday) values (3, 'Selena Johanning', 'sjohanning2@nytimes.com', '1981-11-03');
insert into employee (id, name, email, birthday) values (4, 'Genny Litzmann', 'glitzmann3@qq.com', '1995-02-17');
insert into employee (id, name, email, birthday) values (5, 'Corey Swafford', 'cswafford4@vk.com', '1990-11-25');
insert into employee (id, name, email, birthday) values (6, 'Glenn Palin', 'gpalin5@state.gov', '1997-08-26');
insert into employee (id, name, email, birthday) values (7, 'Danila Richt', 'dricht6@cornell.edu', '2014-09-09');
insert into employee (id, name, email, birthday) values (8, 'Winn Frushard', null, '1979-06-13');
insert into employee (id, name, email, birthday) values (9, 'Stanly Isaksen', 'sisaksen8@sitemeter.com', '2007-07-17');
insert into employee (id, name, email, birthday) values (10, 'Travus Bertlin', 'tbertlin9@theguardian.com', '2018-05-18');
insert into employee (id, name, email, birthday) values (11, 'Cassie Costelow', 'ccostelowa@prweb.com', '1992-09-30');
insert into employee (id, name, email, birthday) values (12, 'Daphne Kisbee', 'dkisbeeb@multiply.com', '2016-04-18');
insert into employee (id, name, email, birthday) values (13, 'Carolann Saffin', 'csaffinc@newsvine.com', '2016-10-25');
insert into employee (id, name, email, birthday) values (14, 'Kyle Graeser', 'kgraeserd@ed.gov', '2007-08-23');
insert into employee (id, name, email, birthday) values (15, 'Milzie Rodenborch', 'mrodenborche@yahoo.com', '1967-12-28');
insert into employee (id, name, email, birthday) values (16, 'Edik Wilsee', null, '1951-10-28');
insert into employee (id, name, email, birthday) values (17, 'Shelley Laimable', 'slaimableg@oaic.gov.au', '2006-06-07');
insert into employee (id, name, email, birthday) values (18, 'Ody Totterdill', 'ototterdillh@quantcast.com', '2008-12-06');
insert into employee (id, name, email, birthday) values (19, 'Rubin Withur', null, '1980-09-06');
insert into employee (id, name, email, birthday) values (20, 'Krystal Goodday', null, '2010-10-29');
insert into employee (id, name, email, birthday) values (21, 'Chloris De Giorgis', 'cdek@mapy.cz', '1986-11-18');
insert into employee (id, name, email, birthday) values (22, 'Tedda Dummigan', 'tdummiganl@paginegialle.it', '2005-12-11');
insert into employee (id, name, email, birthday) values (23, 'Uri Twells', 'utwellsm@trellian.com', '1967-09-27');
insert into employee (id, name, email, birthday) values (24, 'Riannon Heed', 'rheedn@gnu.org', '2010-12-14');
insert into employee (id, name, email, birthday) values (25, 'Berta Climson', 'bclimsono@deviantart.com', null);
insert into employee (id, name, email, birthday) values (26, 'Kilian Try', 'ktryp@instagram.com', '2012-09-25');
insert into employee (id, name, email, birthday) values (27, 'Max Reedman', 'mreedmanq@parallels.com', '1955-04-27');
insert into employee (id, name, email, birthday) values (28, 'Berget Segrott', 'bsegrottr@smugmug.com', '1984-04-26');
insert into employee (id, name, email, birthday) values (29, 'Annette Iianon', 'aiianons@washingtonpost.com', '2019-04-17');
insert into employee (id, name, email, birthday) values (30, 'Lyn Middleditch', 'lmiddleditcht@plala.or.jp', '1960-01-10');
insert into employee (id, name, email, birthday) values (31, 'Tanner McAmish', 'tmcamishu@jalbum.net', '2014-04-14');
insert into employee (id, name, email, birthday) values (32, 'Lari Patkin', 'lpatkinv@dedecms.com', '2022-01-19');
insert into employee (id, name, email, birthday) values (33, 'Cory Gasker', 'cgaskerw@nsw.gov.au', '1994-01-18');
insert into employee (id, name, email, birthday) values (34, 'Cordell Jessup', 'cjessupx@bandcamp.com', '1967-06-18');
insert into employee (id, name, email, birthday) values (35, 'Alleyn Koubek', 'akoubeky@psu.edu', '2023-04-01');
insert into employee (id, name, email, birthday) values (36, 'Lalo Borge', null, '1991-01-30');
insert into employee (id, name, email, birthday) values (37, 'Jorey Zorzetti', 'jzorzetti10@odnoklassniki.ru', '1968-07-03');
insert into employee (id, name, email, birthday) values (38, 'Aron Clarridge', 'aclarridge11@bandcamp.com', '2000-07-07');
insert into employee (id, name, email, birthday) values (39, 'Mac Dinwoodie', 'mdinwoodie12@histats.com', '1954-08-17');
insert into employee (id, name, email, birthday) values (40, 'Gunar Texton', 'gtexton13@dyndns.org', '1957-09-09');
insert into employee (id, name, email, birthday) values (41, 'Robbin Budding', 'rbudding14@amazon.co.uk', '2018-04-14');
insert into employee (id, name, email, birthday) values (42, 'Beverly McCawley', 'bmccawley15@mail.ru', '1953-11-04');
insert into employee (id, name, email, birthday) values (43, 'Viviene Baudrey', 'vbaudrey16@slashdot.org', '1957-02-24');
insert into employee (id, name, email, birthday) values (44, 'Gerardo Januszewicz', null, '1961-07-11');
insert into employee (id, name, email, birthday) values (45, 'Alec Szymonowicz', 'aszymonowicz18@privacy.gov.au', '1963-01-12');
insert into employee (id, name, email, birthday) values (46, 'Izak Levins', 'ilevins19@prweb.com', '1963-11-16');
insert into employee (id, name, email, birthday) values (47, 'Norri Twede', 'ntwede1a@reverbnation.com', '1993-09-02');
insert into employee (id, name, email, birthday) values (48, 'Tad Darwen', 'tdarwen1b@imageshack.us', '2014-12-12');
insert into employee (id, name, email, birthday) values (49, 'Meg De Gregario', null, '1961-06-23');
insert into employee (id, name, email, birthday) values (50, 'Tori Halleday', 'thalleday1d@goo.ne.jp', '1970-05-23');
```
Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```
UPDATE employee
SET name = 'Busra',
    birthday = '1998-02-23',
	email = 'busra@zenbilci.com'
WHERE id = 10;
```
```
UPDATE employee
SET name = 'UPDATE',
    birthday = '2022-12-23',
	email = 'new@person.com'
WHERE name = 'Selena Johanning'
RETURNING (*);

Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```
DELETE FROM employee
WHERE id = 15;
```
DELETE FROM employee
WHERE id > 41
RETURNING *;
```
DELETE FROM employee
WHERE id > 41
RETURNING *;
```
```
## SQL Ödev 09 | INNER JOIN 
## SQL Ödev 10 | LEFT, RIGHT, FULL JOIN 
## SQL Ödev 11 | UNION, INTERSECT ve EXCEPT 
