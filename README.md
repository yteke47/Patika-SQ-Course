# Patika-SQL-Course

Merhaba, bu git reposunda Patika üzerinden almakta olduğum [SQL](https://academy.patika.dev/courses/sql) kursunun ödevleri yer almaktadır.

* Çalışmalar **[dvdrental](https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database)** adlı örnek veri tabanı üzerinden gerçekleştirilmiştir.

## Ödev 1
1.  **film**  tablosunda bulunan  **title**  ve  **description**  sütunlarındaki verileri sıralayınız.
``` SQL
SELECT title, description FROM film;
```
2.  **film**  tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük  **VE**  75 ten küçük olma koşullarıyla sıralayınız.
``` SQL
SELECT * FROM film
WHERE length > 60 AND length < 75;
```
3.  **film**  tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99  **VE**  replacement_cost 12.99  **VEYA**  28.99 olma koşullarıyla sıralayınız.

``` SQL
SELECT * FROM film
WHERE rental_rate = 0.99 AND length replacement_cost = 12.99 OR replacement_cost = 28.99;
```
4.  **customer**  tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
``` SQL
SELECT last_name FROM customer
WHERE first_name = "Mary";
```
5.  **film**  tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
``` SQL
SELECT * FROM film
WHERE NOT length > 50 AND rental_rate = 2.99 OR NOT rental_rate = 4.99;
```

## Ödev 2 


1.  **film**  tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
``` SQL
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
2.  .**actor**  tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
``` SQL
SELECT first_name, last_name FROM actor
WHERE first_name IN('Penelope', 'Nick', 'Ed');
```
3.  **film**  tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99  **VE**  replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
``` SQL
SELECT * FROM film
WHERE (rental_rate IN(0.99, 2.99, 4.99)) AND (replacement_cost IN(12.99, 15.99, 28.99));
```
## Ödev 3
1.  **country**  tablosunda bulunan  **country**  sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
``` SQL
SELECT * FROM country
WHERE country LIKE 'A%a';
```
2.  **country**  tablosunda bulunan  **country**  sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
``` SQL
SELECT * FROM country
WHERE country LIKE '_____n';
```
3.  **film**  tablosunda bulunan  **title**  sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
``` SQL
SELECT title FROM film
WHERE title ILIKE '%T%T%T%T%';
```
4.  **film**  tablosunda bulunan tüm sütunlardaki verilerden  **title**  'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
``` SQL
SELECT * FROM film
WHERE (title LIKE 'C%') AND (length > 90) AND (rental_rate = 2.99);
```

## Ödev 4

1.  **film**  tablosunda bulunan  **replacement_cost**  sütununda bulunan birbirinden farklı değerleri sıralayınız.
``` SQL
SELECT DISTINCT replacement_cost FROM film;
```
2.  **film**  tablosunda bulunan  **replacement_cost**  sütununda birbirinden farklı kaç tane veri vardır?
``` SQL
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```
3.  **film**  tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
``` SQL
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
4.  **country**  tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
``` SQL
SELECT COUNT(*) FROM country
WHERE country LIKE '_____';
```
5.  **city**  tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
``` SQL
SELECT COUNT(*) FROM city
WHERE city ILIKE '%r';
```

## Ödev 5

1.  **film**  tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
``` SQL
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```
2.  **film**  tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
``` SQL
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```
3.  **customer**  tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
``` SQL
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

## Ödev 6
1.  **film**  tablosunda bulunan  **rental_rate**  sütunundaki değerlerin ortalaması nedir?
``` SQL
SELECT ROUND(AVG(rental_rate),2) FROM film;
```
2.  **film**  tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
``` SQL
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
```
3.  **film**  tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
``` SQL
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```
4.  **film**  tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
``` SQL
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
```

## Ödev 7
1.  **film**  tablosunda bulunan filmleri  **rating**  değerlerine göre gruplayınız.
``` SQL
SELECT rating FROM film
GROUP BY rating;
```
2.  **film**  tablosunda bulunan filmleri  **replacement_cost**  sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
``` SQL
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```
3.  **customer**  tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
``` SQL
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```
4.  **city**  tablosunda bulunan şehir verilerini  **country_id**  sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
``` SQL
SELECT country_id , COUNT(*) FROM city
GROUP BY country_id
ORDER BY count DESC
LIMIT 1;
```
## Ödev 8
1.  **test**  veritabanınızda  **employee**  isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
``` SQL
CREATE TABLE employee (
	id serial PRIMARY KEY,
	name varchar(50) NOT NULL,
	email varchar(100),
	birthday date
)
```
2.  Oluşturduğumuz  **employee**  tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
``` SQL
insert into employee (name, email, birthday) values ('Monroe Rehn', 'mrehn0@icio.us', '4/1/1976');

insert into employee (name, email, birthday) values ('Netta Heims', 'nheims1@dedecms.com', '12/31/1997');

insert into employee (name, email, birthday) values ('Weidar Exter', 'wexter2@vinaora.com', '2/6/1979');

insert into employee (name, email, birthday) values ('Son Frany', 'sfrany3@php.net', '7/11/1970');

insert into employee (name, email, birthday) values ('Tybie Stroulger', 'tstroulger4@com.com', '10/27/1991');

insert into employee (name, email, birthday) values ('Stevena Dymick', 'sdymick5@hao123.com', '6/15/1970');

insert into employee (name, email, birthday) values ('Caressa Ozanne', 'cozanne6@flavors.me', '5/16/1999');

insert into employee (name, email, birthday) values ('Avie Greneham', 'agreneham7@nyu.edu', '2/12/1992');

insert into employee (name, email, birthday) values ('Lauree Edington', 'ledington8@sina.com.cn', '3/13/1992');

insert into employee (name, email, birthday) values ('Arne Hailwood', 'ahailwood9@de.vu', '9/9/1977');

insert into employee (name, email, birthday) values ('Raymond Kubiak', 'rkubiaka@msn.com', '10/3/1989');

insert into employee (name, email, birthday) values ('Gus Buncom', 'gbuncomb@hc360.com', '4/16/1982');

insert into employee (name, email, birthday) values ('Bern Fawssett', 'bfawssettc@theatlantic.com', '6/5/1976');

insert into employee (name, email, birthday) values ('Karilynn McCorrie', 'kmccorried@go.com', '5/29/1995');

insert into employee (name, email, birthday) values ('Jobye Antonucci', 'jantonuccie@hp.com', '2/8/1996');

insert into employee (name, email, birthday) values ('Berri Trewman', 'btrewmanf@ebay.co.uk', '5/25/2000');

insert into employee (name, email, birthday) values ('Randy Ronca', 'rroncag@marketwatch.com', '1/2/1994');

insert into employee (name, email, birthday) values ('Petra Gronauer', 'pgronauerh@howstuffworks.com', '6/8/1977');

insert into employee (name, email, birthday) values ('Ailis Fincke', 'afinckei@mayoclinic.com', '5/20/1990');

insert into employee (name, email, birthday) values ('Jackie Liccardo', 'jliccardoj@blogtalkradio.com', '10/29/1990');

insert into employee (name, email, birthday) values ('Donella Stewart', 'dstewartk@bloglovin.com', '3/6/1976');

insert into employee (name, email, birthday) values ('Alysia Breckenridge', 'abreckenridgel@nymag.com', '11/9/1989');

insert into employee (name, email, birthday) values ('Matty Clew', 'mclewm@mozilla.com', '12/16/1972');

insert into employee (name, email, birthday) values ('Elli Condon', 'econdonn@nyu.edu', '5/1/1973');

insert into employee (name, email, birthday) values ('Rahal Domanek', 'rdomaneko@mapy.cz', '4/13/1994');

insert into employee (name, email, birthday) values ('Leigh Pitcaithley', 'lpitcaithleyp@utexas.edu', '6/12/1973');

insert into employee (name, email, birthday) values ('Tatiana Hursthouse', 'thursthouseq@goo.gl', '3/9/1980');

insert into employee (name, email, birthday) values ('Constantine Triggle', 'ctriggler@cpanel.net', '8/23/1996');

insert into employee (name, email, birthday) values ('Ralina Rivers', 'rriverss@mashable.com', '7/8/1970');

insert into employee (name, email, birthday) values ('Trev Learoid', 'tlearoidt@dmoz.org', '7/3/1980');

insert into employee (name, email, birthday) values ('Sergei Schwandt', 'sschwandtu@netscape.com', '5/17/1977');

insert into employee (name, email, birthday) values ('Vallie Dines', 'vdinesv@unicef.org', '3/22/1979');

insert into employee (name, email, birthday) values ('Winthrop Ruddock', 'wruddockw@apache.org', '10/26/1973');

insert into employee (name, email, birthday) values ('Dolli Fellini', 'dfellinix@mac.com', '1/27/1974');

insert into employee (name, email, birthday) values ('Constancia Helis', 'chelisy@trellian.com', '11/18/1986');

insert into employee (name, email, birthday) values ('Kayley Antonowicz', 'kantonowiczz@bloglovin.com', '6/28/1987');

insert into employee (name, email, birthday) values ('Jenni Ingall', 'jingall10@microsoft.com', '11/24/1991');

insert into employee (name, email, birthday) values ('Humfrid Fletcher', 'hfletcher11@altervista.org', '6/2/1977');

insert into employee (name, email, birthday) values ('Kerwin Poley', 'kpoley12@ning.com', '8/7/1975');

insert into employee (name, email, birthday) values ('Kettie Burnhill', 'kburnhill13@infoseek.co.jp', '12/3/1988');

insert into employee (name, email, birthday) values ('Merwyn Wollard', 'mwollard14@scientificamerican.com', '5/20/1973');

insert into employee (name, email, birthday) values ('Ulysses Heliot', 'uheliot15@constantcontact.com', '12/4/1986');

insert into employee (name, email, birthday) values ('Artus Ogborne', 'aogborne16@vk.com', '1/2/1998');

insert into employee (name, email, birthday) values ('Che Dimitriev', 'cdimitriev17@bloomberg.com', '8/27/1991');

insert into employee (name, email, birthday) values ('Paton Curd', 'pcurd18@hatena.ne.jp', '2/14/1991');

insert into employee (name, email, birthday) values ('Philippine Coaker', 'pcoaker19@dropbox.com', '6/28/1981');

insert into employee (name, email, birthday) values ('Hamil Bonhome', 'hbonhome1a@blinklist.com', '11/18/1998');

insert into employee (name, email, birthday) values ('Gerta Wyson', 'gwyson1b@wix.com', '12/24/1970');

insert into employee (name, email, birthday) values ('Shane Upcraft', 'supcraft1c@comcast.net', '12/2/1993');

insert into employee (name, email, birthday) values ('Aldous Nequest', 'anequest1d@ebay.co.uk', '9/1/1981');
```
3.  Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```SQL
UPDATE employee
SET first_name = 'UPDATED'
WHERE first_name LIKE 'E%' OR last_name LIKE 'N%
RETURNING *;
```
4.  Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```SQL
DELETE FROM employee
WHERE first_name LIKE 'E%' OR last_name LIKE 'N%'
RETURNING *;
```
