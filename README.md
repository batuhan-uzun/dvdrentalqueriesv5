# SQL Ödev 12

Bu proje, SQL kullanarak verilen ödev senaryolarına dayalı sorguları içerir. Aşağıda her bir sorunun açıklaması ve gerekli SQL sorguları bulunmaktadır.

## 1. Film tablosunda film uzunluğu `length` sütununda gösterilmektedir. Uzunluğu ortalamadan uzun olan kaç tane film vardır?

### Sorgu:
```sql
SELECT COUNT(*) 
FROM film 
WHERE length > (SELECT AVG(length) FROM film);
```
- Bu sorgu, film tablosundaki `length` sütunundaki değerleri ortalama uzunluktan büyük olan filmleri sayar.

## 2. Film tablosunda en yüksek `rental_rate` değerine sahip kaç tane film vardır?

### Sorgu:
```sql
SELECT COUNT(*)
FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
```
- Bu sorgu, film tablosundaki en yüksek `rental_rate` değerine sahip filmleri sayar.

## 3. Film tablosunda en düşük `rental_rate` ve en düşük `replacement_cost` değerlerine sahip filmleri sıralayınız.

### Sorgu:
```sql
SELECT * 
FROM film 
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);
```
- Bu sorgu, film tablosundaki en düşük `rental_rate` ve en düşük `replacement_cost` değerine sahip olan filmleri listeleyerek sıralar.

## 4. `payment` tablosunda en fazla alışveriş yapan müşterileri (`customer`) sıralayınız.

### Sorgu:
```sql
SELECT customer_id, COUNT(*) AS num_payments
FROM payment
GROUP BY customer_id
ORDER BY num_payments DESC;
```
- Bu sorgu, `payment` tablosundaki verileri kullanarak her müşteri için yapılan alışveriş sayısını sayar ve en fazla alışveriş yapanları sıralar.

---

## Kullanım

Bu SQL sorguları, `dvdrental` veritabanındaki `film`, `payment` gibi tablolara yönelik olarak yazılmıştır. Veritabanınızı uygun şekilde oluşturduktan sonra sorguları çalıştırarak sonuçları gözlemleyebilirsiniz.

## Lisans

Bu proje [MIT Lisansı](https://opensource.org/licenses/MIT) altında lisanslanmıştır.
