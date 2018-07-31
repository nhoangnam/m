 /etc/init.d/mysqld restart
/sbin/service httpd restart


top -c
rm -rf /home/tkmc/domains/thaykinhmanhinhcamung.com/public_html/journal-cache

cd /home/tkmc/domains/thaykinhmanhinhcamung.com/public_html/

nh0angnam

service httpd restart 
service proftpd start

DROP TABLE `oc_category`, `oc_category_description`, `oc_category_path`, `oc_category_to_store`, `oc_manufacturer`, `oc_manufacturer_to_store`, `oc_product`, `oc_product_attribute`, `oc_product_description`, `oc_product_discount`, `oc_product_image`, `oc_product_option`, `oc_product_option_value`, `oc_product_to_category`, `oc_product_to_store`;

mysql -u root -p 3 < C:\xampp\mysql\bin\ns.sql


passwd

fixme:

mysql -u fixme -p test < /home/fixme/domains/fixme.vn/public_html/fixme_oc.sql

tkmc: nh8angnam

mysql -u tkmc -p tkmc_oc < /home/tkmc/domains/thaykinhmanhinhcamung.com/public_html/1.sql



mysql -u tkip7 -p tkip7_oc < /home/tkip7/domains/thaykinhiphone7.com/public_html/1.sql




DROP TABLE `oc_category`, `oc_category_description`, `oc_category_filter`, `oc_category_path`, `oc_category_to_layout`, `oc_category_to_store`, `oc_manufacturer`, `oc_manufacturer_to_store`, `oc_product`, `oc_product_attribute`, `oc_product_description`, `oc_product_discount`, `oc_product_filter`, `oc_product_image`, `oc_product_option`, `oc_product_option_value`, `oc_product_profile`, `oc_product_recurring`, `oc_product_related`, `oc_product_reward`, `oc_product_special`, `oc_product_to_category`, `oc_product_to_download`, `oc_product_to_layout`, `oc_product_to_store`;



INSERT INTO oc_product (product_id,price) 
VALUES
 (182, 350000),
 (193, 350000),
 (111, 1700000)
ON DUPLICATE KEY UPDATE price=VALUES(price);

---------------
Số lượng update
UPDATE oc_product SET quantity = 1000 WHERE quantity = 1
---------------

INSERT INTO table1 (id,name,units,price,category_id) 
VALUES 
    (1,'name1', 'units1', 'price1', 6)
    (2,'name2', 'units2', 'price2', 6)
    (3,'name3', 'units3', 'price3', 6)
    (4,'name4', 'units4', 'price4', 6)
ON DUPLICATE KEY UPDATE 
    product_name=VALUES(name), 
    units=VALUES(units), 
    price=VALUES(price)

---------------
Update so luong
INSERT INTO oc_product (product_id, quantity) 
VALUES
(317, 0), 
(432, 1450)
ON DUPLICATE KEY UPDATE 
    quantity=VALUES(quantity);
--------------
INSERT INTO oc_product (product_id, model) 
VALUES 
(432, 'M2-2') 
ON DUPLICATE KEY UPDATE model=VALUES(model)


Xuất ra excel

0837718243

SELECT a.name as "Tên SP", c.name as "Thư Mục", a.product_id as "Mã SP", d.model as "Model", d.quantity as "Số lượng", concat(FORMAT(d.price,0)) as "Giá"
FROM oc_product_description a, oc_product_to_category b, oc_category_description c, oc_product d
where a.product_id = b.product_id and b.category_id = c.category_id and a.product_id = d.product_id and a.language_id = 2 and c.language_id = 2
group by a.product_id
ORDER by b.category_id, a.name


SELECT CONCAT('[URL="http://thaykinhdienthoai.com/index.php?route=product/product&product_id=', a.product_id, '"]', a.name, '[/URL]', concat("  --->",FORMAT(d.price,0),"₫"), '[SIZE=1][COLOR=#696969][I] <-- Click tên SP để xem thêm chi tiết[/I][/COLOR][/SIZE]') as "URL",  a.name as "Tên SP", concat(FORMAT(d.price,0),"₫") as "Giá",  c.name as "Thư Mục", a.product_id as "Mã SP"
FROM oc_product_description a, oc_product_to_category b, oc_category_description c, oc_product d
where a.product_id = b.product_id and b.category_id = c.category_id and a.product_id = d.product_id and a.language_id = 2 and c.language_id = 2
group by a.product_id
ORDER by b.category_id, a.name



SELECT a.`product_id`, b.`image`
FROM `oc_product_to_category` a, `oc_category` b
WHERE a.`category_id` = b.`category_id`


UPDATE oc_product p
SET p.image = (
    SELECT a.`product_id`, b.`image`
	FROM `oc_product_to_category` a, `oc_category` b
	WHERE a.`category_id` = b.`category_id`)


UPDATE related_category
INNER JOIN
product_category
ON related_category.rel_cat_id = product_category.cat_id
SET related_category.rel_cat_name = product_category.cat_name


UPDATE oc_product
INNER JOIN
product_category
ON related_category.rel_cat_id = product_category.cat_id
SET related_category.rel_cat_name = product_category.cat_name

UPDATE
    oc_product
SET
    Table_A.col1 = Table_B.col1,
    Table_A.col2 = Table_B.col2
FROM
    Some_Table AS Table_A
    INNER JOIN Other_Table AS Table_B
        ON Table_A.id = Table_B.id
WHERE
    Table_A.col3 = 'cool'


SELECT b.`image`
FROM `oc_product_to_category` a, `oc_category` b
WHERE a.`category_id` = b.`category_id`


UPDATE `oc_product` p
(SELECT `product_id`, `image`
FROM `oc_product_to_category` a, `oc_category` b
WHERE a.`category_id` = b.`category_id`) t1
SET t1.



UPDATE oc_product p
  FROM (SELECT b.`image`
FROM `oc_product_to_category` a, `oc_category` b
WHERE a.`category_id` = b.`category_id`)
   SET p.`image` = b.`image`
 WHERE p.`product_id` = a.`product_id`


 UPDATE `oc_product_description` SET `description`= ""
WHERE `product_id`= 2 & `language_id` = 1;

===TAG
UPDATE `oc_product_description`a SET `tag` = a.name + "," + d.`model`+ "," + "Sửa "+ d.`model`

FROM oc_product_description a, oc_product_to_category b, oc_category_description c, oc_product d 
WHERE a.product_id = b.product_id and b.category_id = c.category_id and a.product_id = d.product_id and a.language_id = 2 and c.language_id = 2;


INSERT INTO `oc_product_description` (`tag`)
SELECT a.name AS tag
FROM `oc_product_description`
WHERE `language_id` = 2;

INSERT INTO fixme_tkmc.`oc_product_description` (product_id,`tag`)
SELECT a.product_id as id, a.name AS tag
FROM fixme_tkmc.oc_product_description a, fixme_tkmc.oc_product d
where a.product_id = d.product_id and a.language_id = 2
group by a.product_id
 
To export
If it's an entire DB, then:

$ mysqldump -u [uname] -p[pass] db_name > db_backup.sql
If it's all DBs, then:

$ mysqldump -u [uname] -p[pass] --all-databases > all_db_backup.sql
If it's specific tables within a DB, then:

$ mysqldump -u [uname] -p[pass] db_name table1 table2 > table_backup.sql
You can even go as far as auto-compressing the output using gzip (if your DB is very big):

$ mysqldump -u [uname] -p[pass] db_name | gzip > db_backup.sql.gz
If you want to do this remotely and you have the access to the server in question, then the following would work (presuming the MySQL server is on port 3306):

$ mysqldump -P 3306 -h [ip_address] -u [uname] -p[pass] db_name > db_backup.sql
To import
Type the following command to import sql data file:

$ mysql -u username -p -h localhost DATA-BASE-NAME < data.sql
In this example, import 'data.sql' file into 'blog' database using sat as username:

$ mysql -u sat -p -h localhost blog < data.sql
If you have a dedicated database server, replace localhost hostname with with actual server name or IP address as follows:

$ mysql -u username -p -h 202.54.1.10 databasename < data.sql
OR use hostname such as mysql.cyberciti.biz

$ mysql -u username -p -h mysql.cyberciti.biz database-name < data.sql
If you do not know the database name or database name is included in sql dump you can try out something as follows:

$ mysql -u username -p -h 202.54.1.10 < data.sql
