# SQL Komutları - Ödev 1
1. **film** tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```sql
Select title description From film; 
```
2. **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük **VE** 75 ten küçük olma koşullarıyla sıralayınız.
```sql
Select * From film WHERE length <75 AND length >60;
```
3. **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.
```sql
SELECT * FROM film 
WHERE rental_rate = 0.99 AND (replacement_cost=28.99 OR replacement_cost = 12.99);
```
4. **customer** tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```sql
SELECT * FROM customer WHERE first_name = 'Mary';
```
5. **film** tablosundaki uzunluğu(length) 50 ten büyük **OLMAYIP** aynı zamanda rental_rate değeri 2.99 **VEYA** 4.99 **OLMAYAN** verileri sıralayınız.
```sql
SELECT * FROM film 
WHERE NOT length > 50 AND NOT (rental_rate = 4.99 OR rental_rate = 2.99);
```
# SQL Komutları - Ödev 2

1. **film** tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( **BETWEEN** - **AND** yapısını kullanınız.)
```sql
SELECT * FROM film WHERE replacement_cost  BETWEEN 12.99 AND 16.99
```
2. **.actor** tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( **IN** operatörünü kullanınız.)
```sql
SELECT first_name, last_name FROM actor 
WHERE first_name IN ('Penelope','Nick');
```
3. **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 **VE** replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( **IN** operatörünü kullanınız.)
```sql
SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```
# SQL Komutları - Ödev 3
1. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```sql
SELECT * FROM country WHERE country LIKE  'A%a'
```
2. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```sql
SELECT * FROM country WHERE country LIKE  '_____%n'
```
3. **film** tablosunda bulunan **title** sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```sql
SELECT * FROM film WHERE title ILIKE 'T%T%T%T%';
```
4. **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```sql
SELECT * FROM film 
WHERE title LIKE 'C%' AND length >90 AND rental_rate = 2.99;
```
# SQL Komutları - Ödev 4
1. **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.
```sql
SELECT DISTINCT(replacement_cost) FROM film;
```
2. **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır?
```sql
SELECT COUNT(DISTINCT(replacement_cost)) FROM film;
```
3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```sql
SELECT COUNT(*) FROM film WHERE title LIKE ('T%') AND rating IN ('G') ;
```
4. **country** tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```sql
SELECT COUNT(*) FROM country WHERE country LIKE ('_____') 
```
5. **city** tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```sql
SELECT COUNT(*) FROM city WHERE city ILIKE ('%R');
```
# SQL Komutları - Ödev 5
1. **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```sql
SELECT * FROM film WHERE title LIKE ('%n')
ORDER BY length DESC LIMIT 5; 
```
2. **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```sql
SELECT * FROM film WHERE title LIKE ('%n')
ORDER BY length ASC LIMIT 5 OFFSET 5 ;
```
3. **customer** tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```sql
SELECT * FROM customer WHERE store_id = 1 
ORDER BY last_name DESC LIMIT 4; 
```
# SQL Komutları - Ödev 6
1. **film** tablosunda bulunan **rental_rate** sütunundaki değerlerin ortalaması nedir?
```sql
SELECT ROUND(AVG(rental_rate),3) FROM film;
```
2. **film** tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```sql
SELECT COUNT(*) FROM film WHERE title LIKE ('C%');
```
3. **film** tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```sql
SELECT MAX(length) FROM film WHERE rental_rate = 0.99;
```
4. **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```sql
SELECT COUNT(DISTINCT replacement_cost) FROM film WHERE length >150;
```
# SQL Komutları - Ödev 7
1. **film** tablosunda bulunan filmleri **rating** değerlerine göre gruplayınız.
```sql
SELECT rental_rate, COUNT(*) FROM film 
GROUP BY rental_rate;
```
2. **film** tablosunda bulunan filmleri **replacement_cost**sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;
```
3. **customer** tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
```sql
SELECT store_id,COUNT(*) FROM customer
GROUP BY store_id;
```
 4. **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
 ```sql
SELECT country_id,COUNT(city) FROM city 
GROUP BY country_id
ORDER BY COUNT(city) DESC
LIMIT 1;
```
# SQL Komutları - Ödev 8
1. **test** veritabanınızda **employee** isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```sql
CREATE TABLE employee (
    id INT NOT NULL,
    name VARCHAR(50) NOT NULL,
    birtday DATE,
    email VARCHAR(100)
);
```
2. Oluşturduğumuz **employee** tablosuna '[Mockaroo](https://www.mockaroo.com/)' servisini kullanarak 50 adet veri ekleyelim.
```sql
insert into employee (id, name, birtday, email) values (1, 'Wynny Aynsley', '1941-09-12', 'waynsley0@unc.edu');
```
3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet **UPDATE** işlemi yapalım.
```sql
UPDATE employee 
SET name = 'name_last',
    birtday = '1900-01-01'
WHERE id >45;
```
```sql
UPDATE employee
SET name = 'Alice'
WHERE birtday > '1980-02-02';
```
```sql
UPDATE employee 
SET email ='alice@frank.com'
WHERE name LIKE ('A%');
```
```sql
UPDATE employee 
SET birtday = '2000-02-01'
WHERE email ='alice@frank.com' ;
```
```sql
UPDATE employee 
SET birtday = NULL
WHERE id>32;
```
4. Sütunların her birine göre ilgili satırı silecek 5 adet **DELETE** işlemi yapalım.
```sql
DELETE FROM employee
WHERE id>45;
```
```sql
DELETE FROM employee
WHERE name = 'Alice';
```
```sql
DELETE FROM employee
WHERE name LIKE ('%i');
```
```sql
DELETE FROM employee
WHERE email = 'hbaldickn@icio.us';
```
```sql
DELETE FROM employee
WHERE birthday< '2000-02-01';
```
# SQL Komutları - Ödev 9
1. **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz **INNER JOIN** sorgusunu yazınız.
```sql
SELECT country.country, city.city FROM country
INNER JOIN city ON  city.country_id = country.country_id;
```
2. **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT customer.first_name,customer.last_name,payment.payment_id FROM customer
INNER JOIN payment ON payment.customer_id = customer.customer_id;
```
3. **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT rental.rental_id, customer.first_name,customer.last_name FROM rental
INNER JOIN customer ON rental.customer_id = customer.customer_id;
```
# SQL Komutları - Ödev 10
1. **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz **LEFT JOIN** sorgusunu yazınız.
```sql
SELECT country.country,city.city FROM city
LEFT JOIN country ON country.country_id = city.country_id;
```
2. **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz **RIGHT JOIN** sorgusunu yazınız.
```sql
SELECT customer.first_name,customer.last_name,payment.payment_id FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
```
3. **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```sql
SELECT rental.rental_id, customer.first_name,customer.last_name FROM rental
FULL JOIN customer ON rental.customer_id = customer.customer_id;
```
# SQL Komutları - Ödev 11
1. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için tüm verileri sıralayalım.
```sql
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```
2. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için kesişen verileri sıralayalım.
```sql
(SELECT first_name FROM actor)
INTERSECT 
(SELECT first_name FROM customer);
```
3. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```sql
(SELECT first_name FROM actor)
EXCEPT 
(SELECT first_name FROM customer);
```
4. İlk 3 sorguyu tekrar eden veriler için de yapalım.
```sql
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
```
```sql 
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);
```
```sql 
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```
# SQL Komutları - Ödev 12

1. **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```sql
SELECT COUNT(*) FROM film
WHERE length > (
    SELECT AVG(film.length)FROM film
);
```
2. **film** tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```sql
SELECT COUNT(*) FROM film
WHERE rental_rate = (
    SELECT MAX(film.rental_rate)FROM film
);
```
3. **film** tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
```sql
SELECT COUNT(*) FROM film
WHERE rental_rate = (
    SELECT MIN(film.rental_rate) FROM film
) AND replacement_cost = (
    SELECT MIN(film.replacement_cost) FROM film
);
```
3. **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```sql
SELECT SUM(payment.amount), customer.first_name,customer.last_name  FROM payment
INNER JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id,customer.first_name,customer.last_name
ORDER BY SUM(payment.amount) DESC;
```
# Son Tekrar
1. **film** tablosundan 'K' karakteri ile başlayan en uzun ve replacenet_cost u en düşük 4 filmi sıralayınız.
```sql
SELECT title, length, replacement_cost FROM film
WHERE title LIKE 'K%'
ORDER BY length DESC, replacement_cost ASC
LIMIT 3;
```
2. **film** tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?
```sql
SELECT COUNT(rating),rating FROM film
GROUP BY rating
ORDER BY COUNT(rating) DESC
LIMIT 1;
```
3. **cutomer** tablosunda en çok alışveriş yapan müşterinin adı nedir?
```sql
SELECT SUM(payment.amount), customer.first_name,customer.last_name  FROM payment
INNER JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id,customer.first_name,customer.last_name
ORDER BY SUM(payment.amount) DESC
LIMIT 1;
```
4. **category** tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.
```sql
SELECT  COUNT(*),category.name FROM  category
JOIN film_category ON film_category.category_id = category.category_id
JOIN film ON film.film_id = film_category.film_id
GROUP BY category.name;
```
5. **film** tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kç tane film vardır?
```sql
SELECT count(*) FROM film
WHERE title ILIKE '%e%e%e%e%';
```
