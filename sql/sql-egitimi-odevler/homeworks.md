# ÖDEV 1
<br/>

# 1
> **film** tablosunda bulunan **title** ve **description** sütunlarındaki verileri sıralayınız.
```SQL
SELECT title, description FROM film;
```

# 2
> **film** tablosunda bulunan tüm sütunlardaki verileri **film uzunluğu (length)** 60 dan büyük **VE** 75 ten küçük olma koşullarıyla sıralayınız.
```SQL
SELECT * FROM film 
WHERE length > 60 AND length < 75
```

# 3
> **film** tablosunda bulunan tüm sütunlardaki verileri **rental_rate** 0.99 **VE** **replacement_cost** 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.
```SQL
SELECT * FROM film 
WHERE rental_rate = 0.99 
AND (replacement_cost = 12.99 OR replacement_cost = 28.99)
```

# 4
> **customer** tablosunda bulunan **first_name** sütunundaki değeri 'Mary' olan müşterinin **last_name** sütunundaki değeri nedir?
```SQL
SELECT last_name FROM customer 
WHERE first_name = 'Mary'
```

# 5
> **film** tablosundaki **uzunluğu(length)** 50 ten büyük **OLMAYIP** aynı zamanda **rental_rate** değeri 2.99 veya 4.99 **OLMAYAN** verileri sıralayınız.
```SQL
SELECT * FROM film
WHERE length <= 50 AND NOT ( rental_rate = 2.99 AND rental_rate = 4.99);
```
<br/>

# ÖDEV 2
<br/>

# 1
> **film** tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```SQL
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

# 2
> **actor** tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```SQL
SELECT first_name, last_name FROM actor
WHERE first_name IN('Penelope','Nick','Ed');
```

# 3
> **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 **VE** replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```SQL
SELECT * FROM film
WHERE rental_rate IN(0.99, 2.99, 4.99) 
AND replacement_cost  IN(12.99, 15.99, 28.99);
```

<br/>

# ÖDEV 3
<br/>

# 1
> **country**  tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```SQL
SELECT country FROM country
WHERE country LIKE 'A%a';
```

# 2
> **country**  tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```SQL
SELECT country FROM country
WHERE country LIKE '_____%n';
```

# 3
> **film** tablosunda bulunan title sütunundaki **film** isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren **film** isimlerini sıralayınız.
```SQL
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%'
```

# 4
> **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```SQL
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```

<br/>

# ÖDEV 4
<br/>

# 1
> **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.
```SQL
SELECT DISTINCT replacement_cost FROM film;
```

# 2
> **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır?
```SQL
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

# 3
> **film** tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```SQL
SELECT COUNT(title) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```

# 4
> **country** tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```SQL
SELECT COUNT(country) FROM country
WHERE country LIKE '_____';
```

# 5
> **city** tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

```SQL
SELECT COUNT(city) FROM city
WHERE city ILIKE '%r';
```

<br/>

# ÖDEV 5
<br/>

# 1
> **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```SQL
SSELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

# 2
> **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```SQL
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
LIMIT 5
OFFSET 5;
```

# 3
> **customer** tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```SQL
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

<br/>

# ÖDEV 6
<br/>

# 1
> **film** tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```SQL
SELECT AVG(rental_rate) FROM film;
2.98
```

# 2
> **film** tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```SQL
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
92
```

# 3
> **film** tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```SQL
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
184
```

# 4
> **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```SQL
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
21
```

<br/>

# ÖDEV 7
<br/>

# 1
> **film** tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```SQL
SELECT rating FROM film
GROUP BY rating;
```

# 2
> **film** tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan **replacement_cost** değerini ve karşılık gelen film sayısını sıralayınız.
```SQL
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) >50 ;
```

# 3
> **customer** tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
```SQL
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;

```

# 4
> **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```SQL
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```


<br/>

# ÖDEV 8
<br/>

# 1
> **test** veritabanınızda **employee** isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```SQL
SELECT rating FROM film

```

# 2
>Oluşturduğumuz **employee** tablosuna **'Mockaroo'** servisini kullanarak 50 adet veri ekleyelim.
<details>
<summary>INSERT Queries</summary>
<br>
<pre>
insert into employee (id, name, birthday, email) values (1, 'Zerk', '2019-02-15', 'zphetteplace0@hostgator.com');
insert into employee (id, name, birthday, email) values (2, 'Kathryn', '1986-12-02', 'kdowdall1@jigsy.com');
insert into employee (id, name, birthday, email) values (3, 'Alasteir', '1991-01-14', 'abrodway2@rambler.ru');
insert into employee (id, name, birthday, email) values (4, 'Umeko', '2006-01-02', 'ujewess3@usnews.com');
insert into employee (id, name, birthday, email) values (5, 'Rosie', '1954-12-31', 'rcutts4@wix.com');
insert into employee (id, name, birthday, email) values (6, 'Marne', '1977-10-28', 'mgainsburgh5@joomla.org');
insert into employee (id, name, birthday, email) values (7, 'Stevie', '2016-05-01', 'sbullas6@latimes.com');
insert into employee (id, name, birthday, email) values (8, 'Nev', '1951-09-17', 'nlangelay7@wired.com');
insert into employee (id, name, birthday, email) values (9, 'Cart', '1992-04-09', 'chofton8@who.int');
insert into employee (id, name, birthday, email) values (10, 'Christan', '2007-12-31', 'creinbech9@g.co');
insert into employee (id, name, birthday, email) values (11, 'Kizzie', '2019-07-30', 'kdurranta@smugmug.com');
insert into employee (id, name, birthday, email) values (12, 'Netta', '1955-07-23', 'nmellandb@diigo.com');
insert into employee (id, name, birthday, email) values (13, 'Cris', '1983-10-24', 'csimesterc@hostgator.com');
insert into employee (id, name, birthday, email) values (14, 'Melosa', '1980-10-31', 'mbatecokd@people.com.cn');
insert into employee (id, name, birthday, email) values (15, 'Glenden', '1975-06-08', 'garmfielde@google.fr');
insert into employee (id, name, birthday, email) values (16, 'Emmy', '1967-11-12', 'eskinnerf@nsw.gov.au');
insert into employee (id, name, birthday, email) values (17, 'Whit', '1989-01-08', 'wgarredg@cisco.com');
insert into employee (id, name, birthday, email) values (18, 'Izak', '1979-05-20', 'iramelh@mlb.com');
insert into employee (id, name, birthday, email) values (19, 'Isobel', '1951-08-22', 'istychei@google.nl');
insert into employee (id, name, birthday, email) values (20, 'Benetta', '2011-08-01', 'bdendlej@pcworld.com');
insert into employee (id, name, birthday, email) values (21, 'Kora', '1954-04-18', 'keakleek@elegantthemes.com');
insert into employee (id, name, birthday, email) values (22, 'Rees', '1981-09-14', 'ryurlovl@nifty.com');
insert into employee (id, name, birthday, email) values (23, 'Lezlie', '1958-06-26', 'linggallm@hhs.gov');
insert into employee (id, name, birthday, email) values (24, 'Gaynor', null, 'ggotteliern@fc2.com');
insert into employee (id, name, birthday, email) values (25, 'Donetta', '2020-01-17', 'dgioanio@nyu.edu');
insert into employee (id, name, birthday, email) values (26, 'Shayla', '1958-03-09', 'spenneyp@pinterest.com');
insert into employee (id, name, birthday, email) values (27, 'Minnnie', '1988-12-03', 'mwannellq@taobao.com');
insert into employee (id, name, birthday, email) values (28, 'Andras', '1976-02-26', 'amatejr@slashdot.org');
insert into employee (id, name, birthday, email) values (29, 'Hodge', '2016-09-18', 'hgibletts@netlog.com');
insert into employee (id, name, birthday, email) values (30, 'Poppy', '1989-07-12', 'pwarrilowt@mapy.cz');
insert into employee (id, name, birthday, email) values (31, 'Elwood', '1980-11-24', 'ekilgallonu@sciencedaily.com');
insert into employee (id, name, birthday, email) values (32, 'Rosalinde', '1983-10-30', 'rwildev@instagram.com');
insert into employee (id, name, birthday, email) values (33, 'Shawna', '1976-02-20', 'spoatw@1688.com');
insert into employee (id, name, birthday, email) values (34, 'Dag', '1958-08-06', 'dcollisonx@de.vu');
insert into employee (id, name, birthday, email) values (35, 'Farrel', null, 'fblewy@acquirethisname.com');
insert into employee (id, name, birthday, email) values (36, 'Colleen', '2007-11-11', 'cpontinz@rakuten.co.jp');
insert into employee (id, name, birthday, email) values (37, 'Mitchael', null, 'mburston10@newsvine.com');
insert into employee (id, name, birthday, email) values (38, 'Karissa', '1955-12-28', 'kpeeter11@tinypic.com');
insert into employee (id, name, birthday, email) values (39, 'Sholom', '2000-10-06', 'svanetti12@last.fm');
insert into employee (id, name, birthday, email) values (40, 'Kaleena', '1954-08-11', 'kcorbyn13@webnode.com');
insert into employee (id, name, birthday, email) values (41, 'Brendin', '1978-02-14', 'brixon14@delicious.com');
insert into employee (id, name, birthday, email) values (42, 'Gunther', '2009-12-14', 'ggronaver15@goodreads.com');
insert into employee (id, name, birthday, email) values (43, 'Sammy', '1952-09-26', 'sprantl16@amazon.co.uk');
insert into employee (id, name, birthday, email) values (44, 'Inness', '1958-04-16', 'imcvanamy17@squarespace.com');
insert into employee (id, name, birthday, email) values (45, 'Chester', '1999-03-22', 'cpruce18@toplist.cz');
insert into employee (id, name, birthday, email) values (46, 'Gun', '2002-01-14', 'ggalle19@qq.com');
insert into employee (id, name, birthday, email) values (47, 'Addie', '1958-06-27', 'abache1a@edublogs.org');
insert into employee (id, name, birthday, email) values (48, 'Eddie', '1994-10-31', 'ehailes1b@cnn.com');
insert into employee (id, name, birthday, email) values (49, 'Burnard', '2008-03-14', 'bluna1c@soup.io');
insert into employee (id, name, birthday, email) values (50, 'Desirae', '1996-07-06', 'dallgood1d@yellowpages.com');
</pre>
</details>

# 3
> Sütunların her birine göre diğer sütunları güncelleyecek 5 adet **UPDATE** işlemi yapalım.
```SQL
UPDATE employee
SET email = 'doroteya@ed.gov'
WHERE id = 5;

UPDATE employee
SET email = 'umeko@gmail.com'
WHERE name = 'Umeko';

UPDATE employee
SET birthday = '1991-01-14'
WHERE name = 'Nev';

UPDATE employee
SET name = 'alper',
	email = 'alper@mail.com',
	birthday = '1980-05-15'
WHERE id = 9;

UPDATE employee
SET email = 'n@gmail.com'
WHERE name = 'N__';
```

# 4
> Sütunların her birine göre ilgili satırı silecek 5 adet **DELETE** işlemi yapalım.
```SQL
DELETE FROM employee
WHERE id = 5;

DELETE FROM employee
WHERE name = 'Umeko';

DELETE FROM employee
WHERE email IS NULL;

DELETE FROM employee
WHERE email ILIKE '%a';

DELETE FROM employee
WHERE name = 'N__';

```

<br/>

# ÖDEV 9
<br/>

# 1
> **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```SQL
SELECT city,country FROM city
INNER JOIN country ON city.country_id=country.country_id;
```

# 2
> **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```SQL
SELECT payment_id, first_name,last_name FROM customer
INNER JOIN payment ON customer.customer_id=payment.payment_id;
```

# 3
> **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```SQL
SELECT rental_id, first_name,last_name FROM customer
INNER JOIN rental ON customer.customer_id=rental.rental_id;
```

<br/>

# ÖDEV 10
<br/>

# 1
> **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```SQL
SELECT city,country FROM city
LEFT JOIN country ON city.country_id=country.country_id;
```

# 2
> **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```SQL
SELECT payment_id, first_name,last_name FROM customer
RIGHT JOIN payment ON customer.customer_id=payment.payment_id;
```

# 3
> **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```SQL
SELECT rental_id, first_name,last_name FROM customer
FULL JOIN rental ON customer.customer_id=rental.rental_id;
```

<br/>

# ÖDEV 11
<br/>

# 1
> **actor** ve **customer** tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```SQL
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```

# 2
> **actor** ve **customer** tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```SQL
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
```

# 3
> **actor** ve **customer** tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```SQL
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
```

# 4
> İlk 3 sorguyu tekrar eden veriler için de yapalım.
```SQL
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
```

```SQL
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
```

```SQL
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```

<br/>

# ÖDEV 12
<br/>

# 1
> **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```SQL
SELECT COUNT(*) FROM film
WHERE length > 
(SELECT ROUND(AVG(length)) FROM film);
```

# 2
> **film** tablosunda en yüksek **rental_rate** değerine sahip kaç tane film vardır?
```SQL
SELECT * FROM film
WHERE rental_rate = 
(SELECT MAX(rental_rate) FROM film);
```

# 3
> **film** tablosunda en düşük **rental_rate** ve en düşün **replacement_cost** değerlerine sahip filmleri sıralayınız.
```SQL
SELECT * FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) 
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);
```

# 4
> **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```SQL
SELECT DISTINCT(customer_id) FROM payment 
WHERE customer_id = ANY 
( SELECT COUNT(*) FROM payment GROUP BY customer_id );
```
<br/>

# RECAP
<br/>

# 1
> **film** tablosundan 'K' karakteri ile başlayan en uzun ve replacement_cost u en düşük 4 filmi sıralayınız.
```SQL
SELECT title, length, replacement_cost FROM film
WHERE title LIKE 'K%'
ORDER BY length DESC, replacement_cost ASC
LIMIT 4; 
```

# 2
> **film** tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?
```SQL
SELECT COUNT(*), rating FROM film
GROUP BY rating
ORDER BY COUNT(*) DESC
LIMIT 1;
```

# 3
> **customer** tablosunda en çok alışveriş yapan müşterinin adı nedir?
```SQL
SELECT SUM(amount), customer.first_name, customer.last_name FROM payment
JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id, customer.first_name, customer.last_name
ORDER BY SUM(amount) DESC
LIMIT 1;
```

# 4
> **category** tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.
```SQL
SELECT COUNT(*),category.name FROM category
JOIN film_category ON film_category.category_id = category.category_id
JOIN film ON film.film_id = film_category.film_id
GROUP BY category.name;
```

# 5
> **film** tablosunda isminde en az 4 adet 'e' veya 'E' karakteri bulunan kç tane film vardır?
```SQL
SELECT title FROM film
WHERE title ILIKE '%e%e%e%e';
```