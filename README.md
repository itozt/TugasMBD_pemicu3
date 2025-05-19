# Pemicu 3 MBD - Procedure Pemesanan Ulang Otomatis

# Identifikasi Database
Sumber : [Link Database NOrthwind](https://drive.google.com/file/d/1g_OGEaDeOvwNqglYqdX8l87gs1VicFQ1/view)
# Identifikasi Database yang Diperlukan
Saya memiliki sebuah database northwind di postgreSQL. <br>
Saya minta kamu berfokus pada 2 table/entitas dan atributnya sebagai berikut : <br>
**1. Entitas products.** <br>
Memiliki atribut dan penjelasannya sebagai berikut : <br>
- product_id (bigint) sebagai Primary Key. 
- product_name (character varying (40)).
- supplier_id (bigint). Foreign key ke tabel suppliers.
- category_id (bigint). Foreign key ke tabel categories.
- quantity_per_unit (character varying(20)).
- unit_price (real). <br>Harga satuan barang.
- unit_in_stock (bigint). <br>Banyaknya stok barang yang tersedia.
- unit_in_order (bigint). <br>Banyaknya stok barang yang sedang dipesan toko dari supplier.
- reorder_level (bigint). <br>Banyaknya stok barang yang tersedia sebagai batas minimal untuk melakukan order/pemesenanan ke supllier. <br>Nantinya, atribut ini digunakan sebagai acuan dalam menentukan kapan toko harus melakukan pemesanan ulang ke supplier.
- discontinued (integer). <br>Kelanjutan dari suatu barang, apakah akan terus dijual&direstock atau tidak direstock lagi. <br>Jika bernilai 0, maka barang akan terus dijual. <br>Jika bernilai 1, maka barang tidak akan direstock/dibiarkan terjual sampai habis dan tidak dilakukan pemesanan ulang ke supplier.

**2. Entitas suppliers.**
Memiliki atribut dan penjelasannya sebagai berikut :
- supplier_id (bigint). Sebagai Primary Key.
- company_name (character varying (40)).
- contact_name (character varying (30)).
- contact_title (character varying (30)).
- address (character varying (60)).
- city (character varying (15)).
- region (character varying (15)).

Pahamilah dengan sungguh-sungguh.
Nantinya, saya akan berikan perintah dan tugas tambahan.
# Perintah Membuat Procedure 
Buatlah Procedure untuk Pemesanan Ulang Otomatis. <br>
Langkah-Langkah/Alur kerja dari procedure yang kamu buat harus sebagai berikut :
1. Mengecek apakah jumlah stok suatu barang ada di bawah batas minimum. <br>Artinya, cek apakah unit_in_stock lebih kecil dari reorder_level. Jika iya, maka lanjut ke langkah selanjutnya. Jika tidak, maka barang tersebut dapat dilewati dan lakukan pengecekan ke barang selanjutnya.
2. Mengecek apakah barang yang jumlah stoknya ada di bawah batas minimum tadi masih perlu untuk dilakukan restock. <br>Cek nilai discontinued dari barang tersebut. Jika 0, maka barang perlu dilakukan pemesanan ulang dan lanjut ke langkah selanjutnya. Jika 1, maka barang tidak perlu dilakukan pemesanan ulang dan tidak lanjut ke langkah selanjutnya.
3. Mengecek apakah barang yang jumlah stoknya ada di bawah batas minimum tadi sudah dilakukan pemesanan ulang atau belum. <br>Cek pada unit_in_order. Jika bukan bernilai 0, artinya barang sudah dilakukan pemesanan ulang dan masih dalam proses pengiriman. Jika bernilai 0, artinya barang belum dilakukan pemesanan ulang dan perlu melakukan pemesenan ulang ke supplier dari barang tersebut (didasarkan dari supplier_id). Lakukan pemesanan ulang barang tersebut dengan jumlah pemesanan 2 kali dari nilai reorder_level.
<br>
Buatlah query procedure sesuai dengan tugas yang saya berikan ini.
