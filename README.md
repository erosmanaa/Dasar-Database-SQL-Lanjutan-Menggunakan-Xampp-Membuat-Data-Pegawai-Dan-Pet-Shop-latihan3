# Dasar-Database-SQL-Lanjutan-Menggunakan-Xampp-Membuat-Data-Pegawai-Dan-Pet-Shop-latihan3

C:\Users\Notbook>cd..

C:\Users>cd..

C:\>cd xammp\cd..mysql
The system cannot find the path specified.

C:\>cd xampp\mysql

C:\xampp\mysql>cd..

C:\xampp>cd..

C:\>cd xampp\mysql\bin

C:\xampp\mysql\bin>mysql -u root

Membuat database #daftar_pegawai

MariaDB [(none)]> create database latihan3;
Query OK, 1 row affected (0.01 sec)

MariaDB [(none)]> use latihan3;
Database changed
MariaDB [latihan3]> create table pegawai (
    -> id_pegawai varchar (20) null,
    -> nama_depan varchar (20) null,
    -> nama_belakang varchar (20) null,
    -> email varchar (10) null,
    -> tlp varchar (12) null,
    -> tgl_kontrak varchar (30) null,
    -> id_job varchar (10) null,
    -> gaji varchar (50) null,
    -> tunjangan varchar (50) null);
Query OK, 0 rows affected (0.44 sec)



MariaDB [latihan3]> insert into pegawai (id_pegawai,nama_depan,nama_belakang,email,tlp,tgl_kontrak,id_job,gaji,tunjangan) values
    -> ("E001","Ferry","Gustiawan","ferry@yahoo.com","07112059004","2005-09-01","L001","2000000","500000"),
    -> ("E002","Aris","Gunadi","aris@yahoo.com","081321345678","2006-09-01","L002","2000000","200000"),
    -> ("E003","Fariz","Ahmad","fariz@gmail.com","081367384322","2006-10-01","L003","1500000",null),
    -> ("E004","Emma","Bunton","emma@gmail.com","081363484342","2006-10-01","L004","1500000","0"),
    -> ("E005","Mike","Scoff","mike@plasa.com","08163454555","2007-09-01","L005","1250000","0"),
    -> ("E006","lincoln","Burrous","linc@yahoo.com","08527388432","2008-09-01","L006","17500000",null);

MariaDB [latihan3]> select * from pegawai;

No1 Tampilkan pegawai yang gajinya bukan 2.000.000 dan 1.250.000 !
MariaDB [latihan3]> select * from pegawai where gaji !=2000000 and gaji !=1250000;

No2 Tampilkan pegawai yang tunjangannya NULL! 
MariaDB [latihan3]> select * from pegawai where tunjangan is null;

No3 Tampilkan pegawai yang tunjangannya tidak NULL!
MariaDB [latihan3]> select * from pegawai where tunjangan is not null;

No4 Tampilkan/hitung jumlah baris/record tabel pegawai!
MariaDB [latihan3]> select count(id_pegawai) from pegawai;

No5 Tampilkan/hitung jumlah total gaji di tabel pegawai!
MariaDB [latihan3]> select sum(gaji) from pegawai;

No6 Tampilkan/hitung rata-rata gaji pegawai!
MariaDB [latihan3]> select avg(gaji) as rata2_gaji from pegawai;

No7 Tampilkan gaji terkecil!
MariaDB [latihan3]> select min(gaji) as gaji_terkecil from pegawai;

No8 Tampilkan gaji terbesar!
MariaDB [latihan3]> select max(gaji) as gaji_terbesar from pegawai;


Membuat database #PetShop


MariaDB [latihan4]> create table pet (
    -> name varchar (10),
    -> owner varchar (20),
    -> species varchar (15),
     -> sex char(2),
    -> brith date,
    -> death date );
Query OK, 0 rows affected (0.31 sec)

MariaDB [latihan4]> insert into pet (name,owner,species,sex,brith,death) values
    -> ("Pufball","Diana","Hamster","F","1999-03-03",null),
    -> ("Claws","Gwen","Cat","M","1994-03-17",null),
    -> ("Fluffy","Harold","Cat","F","1993-02-04",null),
    -> ("Buffy","Harold","Dog","F","1989-05-13",null),
    -> ("Fang","Benny","Dog","M","1990-08-27",null),
    -> ("Bowser","Diana","Dog","M","1989-08-31","1995-07-29"),
    -> ("Chripy","Gwen","Bird","F","1998-09-11",null),
    -> ("Whistler","Gwen","Bird",null,"1997-12-09",null),
    -> ("Slim","Benny","Snake","M","1996-04-29",null);
Query OK, 9 rows affected (0.10 sec)
Records: 9  Duplicates: 0  Warnings: 0

select * from pet

No1 Tampilkan jumlah hewan yang dimiliki setiap owner
MariaDB [latihan4]> select owner, count(name) as jumlah_hewan_peliharaan from pet group by owner;
No2 Tampilkan jumlah hewan berdasarkan spesies
MariaDB [latihan4]> select species, count(species) as jumlah from pet group by species;
No3 Tampilkan jumlah hewan berdasarkan jenis kelamin
MariaDB [latihan4]> select sex, count(sex) as jumlah from pet group by sex;
No4 Tampilkan jumlah hewan berdasarkan spesies dan jenis kelamin
MariaDB [latihan4]> select species, sex, count(sex) as jumlah from pet group by species, sex;
No5 Tampilkan  jumlah  hewan  berdasarkan  spesis  (cat  dan  dog  saja)  dan  jenis kelamin
MariaDB [latihan4]> select species, sex, count(sex) as jumlah from pet group by species, sex having pet.species = "Cat" or pet.species = "Dog";
No6 Tampilkan jumlah hewan berdasarkan jenis kelamin yang diketahui saja
MariaDB [latihan4]> select species, count(sex) as jumlah from pet group by species;



