# PRAKTIKUM

| Variable | Isi |
| -------- | --- |
| **Nama** | Thondy Autarliandi |
| **NIM** |  312310668 |
| **Kelas** | TI.23.A.6 |
| **Mata Kuliah** | BASIS DATA |
| **Dosen** | Agung Nugroho,S.Kom.,M.Kom |

### DATA MODEL MAPPING
Mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)

Dosen (kd_ds, nama)

Matakuliah (kd_mk, nama, sks)

JadwalMengajar (kd_ds, kd_mk, hari, jam, ruang)

KRSMahasiswa (nim, kd_mk, kd_ds, semester, nilai)

### Tugas Praktikum
- Buat DDL Script berdasarkan skema ERD tersebut diatas.
- Jalankan script DDL tersebut pada DBMS MySQL.
langkah-langkahnya :

1. buat dulu script untuk table mahasiswa :
```
CREATE TABLE Mahasiswa (
nim VARCHAR(10) PRIMARY KEY,
nama VARCHAR(255) NOT NULL,
jenis_kelamin ENUM('Laki-Laki', 'Perempuan'),
tgl_lahir DATE,
jalan VARCHAR(255) NOT NULL,
kota VARCHAR(255) NOT NULL,
kodepos VARCHAR(5) NOT NULL,
no_hp VARCHAR(15) NOT NULL,
kd_ds VARCHAR(10) NOT NULL,
FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
);
```

<img width="402" alt="ss11" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/ed0d1bb3-9523-41e0-8a9f-4d7ad1276c15">


tampilkan hasil table :

``desc mahasiswa;``


<img width="525" alt="ss6" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/6bb968c4-bc64-4d2a-a157-ea1a79ce8930">


2. buat script untuk table dosen :

``CREATE TABLE Dosen (
    ->     kd_ds VARCHAR(10) PRIMARY KEY,
    ->     nama VARCHAR(255) NOT NULL
    -> );``


<img width="346" alt="ss12" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/45baa729-193e-4c2f-9037-4440793d222f">


tampiilkan tabel :

``desc dosen;``

<img width="445" alt="ss7" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/2c5e02ad-0ccc-4aee-b991-c81c0ff084ba">


3. buat script untuk mata kuliah :

`` CREATE TABLE Matakuliah (
    ->     kd_mk VARCHAR(10) PRIMARY KEY,
    ->     nama VARCHAR(255) NOT NULL,
    ->     sks INT NOT NULL
    -> );``

<img width="347" alt="ss13" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/20f41f02-7a94-4e06-9251-6b0b9a01dcf5">



tampilkan table :

``desc Matakuliah;``

<img width="445" alt="ss8" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/6c3cc450-49d6-4b4b-b374-c9471fb3ac5b">


4. buat script untuk jadwal mengajar :

``CREATE TABLE JadwalMengajar (
    ->     kd_ds VARCHAR(10) NOT NULL,
    ->     kd_mk VARCHAR(10) NOT NULL,
    ->     hari ENUM('Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu') NOT NULL,
    ->     jam TIME NOT NULL,
    ->     ruang VARCHAR(255) NOT NULL,
    ->     PRIMARY KEY (kd_ds, kd_mk, hari, jam),
    ->     FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds),
    ->     FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk)
    -> ); ``


<img width="520" alt="ss14" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/95050b78-5824-4c5b-95f0-1868a9c05f96">



tampilkan table :

``desc JadwalMengajar;``


<img width="648" alt="ss9" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/1cd88417-c67e-4741-819c-a6516fe6691f">



5. buat script untuk KRSMahasiswa :

``CREATE TABLE KRSMahasiswa (
    ->     nim VARCHAR(10) NOT NULL,
    ->     kd_mk VARCHAR(10) NOT NULL,
    ->     kd_ds VARCHAR(10) NOT NULL,
    ->     semester VARCHAR(10) NOT NULL,
    ->     nilai FLOAT NOT NULL,
    ->     PRIMARY KEY (nim, kd_mk),
    ->     FOREIGN KEY (nim) REFERENCES Mahasiswa(nim),
    ->     FOREIGN KEY (kd_mk) REFERENCES Matakuliah(kd_mk),
    ->     FOREIGN KEY (kd_ds) REFERENCES Dosen(kd_ds)
    -> );``

<img width="468" alt="ss15" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/7e27edc6-ab1c-481a-9fa1-21454efcb98c">


tampilkan table :

``desc KRSMahasiswa;``


<img width="438" alt="ss10" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/7b6a1d93-a6bd-4be3-8c0b-047032502d85">


berikut script secara keseluruhan :


<img width="444" alt="ss16" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/f876dc43-7199-4259-a404-39a74f381337">


## Praktikum 2 Manipulasi Data (DML)
Berdasarkan table Mahasiswa pada praktikum sebelumnya:
(nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds)


1. Isi data pada table tersebut sebanyak minimal 5 record data.
Tampilkan semua isi/record tabel!


• Ubah data tanggal lahir mahasiswa yang bernama Ari menjadi: 1979-08-31!


• Tampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja!


• Hapus Mahasiswa yang bernama Dina!


• Tampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2!


• Tampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan!


• Tampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita!


• Tampilkan data nama dan alamat mahasiswa saja dari tabel tersebut


• Tampilkan data mahasiswa terurut berdasarkan nama.


1. Mengisi tabel dengan minimal 5 record data :

``insert into mahasiswa (nim, nama, jenis_kelamin, tgl_lahir, jalan, kota, kodepos, no_hp, kd_ds) values
    -> (11223344,"ari santoso","Laki-laki","1998-10-12","","Bekasi","","",""),
    -> (11223345,"ario talib","Laki-laki","1999-11-16","","Cikarang","","",""),
    -> (11223346,"dina marlina","Perempuan","1997-12-01","","Karawang","","",""),
    -> (11223347,"lisa ayu","perempuan","1996-01-02","","Bekasi","","",""),
    -> (11223348,"tiara wahidah","perempuan","1980-02-05","","Bekasi","","",""),
    -> (11223349,"anton sinaga","laki-laki","1988-03-10","","Cikarang","","","");``

<img width="683" alt="ss17" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/5e4c2c06-ec35-408a-9160-e79de9ead32a">


2. menampilkan semua isi/record pada tabel bisa menggunakan kode berikut : 


``select*from mahasiswa;``


<img width="583" alt="ss18" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/1a46025d-e7fc-4c9d-8128-51d68dd51e8b">


3. mengubah data tanggal lahir mahasiswa yang bernama Ari menjadi : 1979-08-31 menggunakan kode berikut :

``update mahasiswa set tgl_lahir='1979-08-31' where nim=11223344;``


<img width="578" alt="ss19" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/a3993b0e-2e9f-49e9-a8a7-a5f33df8c5af">


4. Menampilkan satu baris / record data yang telah diubah tadi yaitu record dengan nama Ari saja dengan cara sebagai berikut :

``select*from mahasiswa where nim=11223344;``


<img width="584" alt="ss20" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/dec01c59-25d8-4c12-a7cd-a510161d8b4c">



5. Menghapus Mahasiswa yang bernama Dina dengan cara sebagai berikut:

``delete from mahasiswa where nim=11223346;``


<img width="586" alt="ss21" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/e42f475c-7776-487a-a631-774b8f61fcfb">



6. Menampilkan record atau data yang tanggal kelahirannya lebih dari atau sama dengan 1996-1-2 dengan cara sebagai berikut :

`` select*from mahasiswa where tgl_lahir<='1996-1-2';``


<img width="760" alt="ss22" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/29599dbb-9b79-4973-b1f6-56114bde96bb">



7. Menampilkan semua Mahasiswa yang berasal dari Bekasi dan berjenis kelamin perempuan dengan cara sebagai berikut :


``select * from mahasiswa where kota='bekasi' and jenis_kelamin='Perempuan';``


<img width="583" alt="ss23" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/256e0b45-c4e6-46b9-8031-f31bfa08fe65">



8. Menampilkan semua Mahasiswa yang berasal dari Bekasi dengan kelamin laki-laki atau Mahasiswa yang berumur lebih dari 22 tahun dengan kelamin wanita dengan cara sebagai berikut :


`` select * from mahasiswa where kota='Bekasi' and jenis_kelamin='Laki-laki' or tgl_lahir<='1997-01-02' and jenis_kelamin='Perempuan';``


<img width="837" alt="ss24" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/6426af24-db41-49c2-b02b-2848227bcd0c">



9. Menampilkan data nama dan jalan mahasiswa saja dari tabel tersebut dengan cara sebagai berikut :


``select nama, jalan from mahasiswa;``


<img width="321" alt="ss25" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/c2bdb2aa-6ed2-435f-9691-8dc32a0d2243">



10. Menampilkan data mahasiswa terurut berdasarkan nama dengan cara sebagai berikut :


`` select * from mahasiswa
    -> order by nama asc;``


<img width="609" alt="ss26" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/54bc258c-d92c-4246-ad04-d754a11495f4">




## Evaluasi 

* Tulis semua perintah-perintah SQL percobaan di atas beserta
outputnya!

1. menambah data :

``INSERT INTO <table> (field1, ..., fieldn) VALUE (value1, ..., valuen)``

contoh : 


``INSERT INTO biodata (nim, nama, alamat) VALUE ('1234','Rio','Bekasi');``


<img width="319" alt="ss27" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/e78576b4-a697-4bbb-8569-c7f700c86d1a">



2. menampilkan data :


``SELECT * FROM <table>``
``SELECT [field1, ..., fieldn] FROM <table>``

contoh :


``select * from biodata;``


<img width="230" alt="ss28" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/2254412b-6d82-4d58-8f66-a45c7a47c135">



atau untuk memfilter data gunakan perintah :

``SELECT * FROM WHERE <kondisi>``


<img width="575" alt="ss31" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/3e64461d-147f-4c46-86dd-29b83c40bb05">





3. mengubah data :

``UPDATE <table> SET field1=val1, ..., fieldn=valn WHERE <kondisi>``

contoh : 

``UPDATE biodata SET nama='Rio', alamat='Bekasi' where nim='123344';``


<img width="481" alt="ss29" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/a6a929fc-d9c4-47f6-800d-f01c1476eaeb">



4. Menghapus data :

``DELETE FROM <table> WHERE <kondisi>``


contoh :


``DELETE FROM biodata WHERE nim=‘12334’``

<img width="346" alt="ss30" src="https://github.com/Thndyyy/praktikum2_Sql/assets/148066593/6c516fa9-853f-4b9d-b947-52b660d3bf83">




* Apa bedanya penggunaan BETWEEN dan penggunaan operator >=
dan <= ?

• (misal: tgl_lahir BETWEEN '1990-10-10' AND '1992-10-11')


• (misal: tgl_lahir >= '1990-10-10' AND tgl_lahir <= '1992-10-11')


jawab : 

Operator between ini untuk menangani operasi “jangkauan” sedangkan operator >= dan <= termasuk pada operator relasional. Operator yang digunakan yntuk perbandingan antara dua buah nilai. Jenis dari operator ini adalah: = , >, <, >=, <=, <>


* Berikan kesimpulan anda! 

jawab :


Data Manipulation Language (DML) adalah bahasa pemrograman yang digunakan untuk mengakses, memanipulasi, dan mengelola data dalam sebuah database. DML memungkinkan pengguna untuk melakukan operasi seperti penyisipan data baru, pembaruan data yang sudah ada, penghapusan data, dan kueri data untuk pengambilan informasi yang diperlukan.

Dalam DML, pengguna dapat menggunakan perintah SQL (Structured Query Language) untuk mengakses data. SQL adalah bahasa standar untuk mengakses dan mengelola data dalam database relasional. Perintah SQL yang digunakan dalam DML termasuk menambah, mengubah, menghapus, dan menampilkan data seperti yang telah dipraktekan diatas.

