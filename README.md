# Tugas Praktikum {Pertemuan ke 13}

# Exceptions Handling

Exception (eksepsi) merupakan suatu kesalahan (error) yang terjadi saat proses eksekusi program sedang berjalan,
Kesalahan ini akan menyebabkan program berakhir dengan tidak normal.

# Handling

Penanganan file adalah bagian penting dari aplikasi apa pun.

# Assertion

Assertion(pernyataan) adalah kewajaran program yang kamu bisa aktif/nonaktifkan ketika kamu selesai menjalankan program.

## The Assert Statement

- Saat menemukan pernyataan, Python mengevaluasi ekspresi yang menyertainya, yang mana semoga benar. Jika ekspresi salah, Python memunculkan pengecualian AssertionError.

Sintaks untuk pernyataan yaitu :
assert Expression[, Arguments]

Jika pernyataan gagal, Python menggunakan ArgumentExpression ArgumentExpression sebagai argumen argumen untuk AssertionError AssertionError. Pengecualian AssertionError Pengecualian AssertionError dapat ditangkap dan ditangani ditangani seperti pengecualian lainnya menggunakan try- kecuali pernyataan, tetapi jika dibiarkan, mereka akan menghentikan program dan menghasilkan backtrace.

**Contoh**
- Berikut adalah fungsi fungsi yang mengubah suhu dari derajat Kelvin menjadi derajat Fahrenheit.Karena nol derajat Kelvin dingin, fungsi fungsi menyimpannya jika melihat negatif negatif suhu.
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:

```py
def KevinToFahrenheit(Temperature):
    assert(Temperature >= 0 ),""
    return ((Temperature-273)*1.8)+32
print (KevinToFahrenheit(273))
print (int(KevinToFahrenheit)(505.78))
print (KevinToFahrenheit(-5))
```
Output :  
![1](https://user-images.githubusercontent.com/115573041/208524299-71d4715b-1918-4a45-bb39-77e7f09748ba.png)


## Menangani Pengecualian

Jika Anda memiliki beberapa kode mencurigakan yang mungkin mengeluarkan pengecualian, Anda dapat mempertahankan program Anda letakkan kode yang mencurigakan di *try: blok. Setelah coba: blok, sertakan pernyataan sertakan *except: statemen, diikuti oleh blok kode yang menangani masalah seanggun mungkin.

**Contoh**

- Contoh-contoh ini membuka file, menulis konten file, dan keluar dengan aman karena ada tidak masalah

- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:

```py
try:
    fh = open("testfile", "w")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print ("Error: can\'t find file or read data")
else:
    print ("Written content in the file successfully")
fh.close()
```
Output :![2](https://user-images.githubusercontent.com/115573041/208524346-bc3d1e0e-7b8a-4ff4-ab69-2cd118250007.png)



- Contoh ini mencoba membuka file yang Anda tidak memiliki izin menulis, sehingga membuat file pengecualian

- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:

```py
try:
    fh = open("testfile", "r")
    fh.write("This is my test file for exception handling!!")
except IOError:
    print ("Error: can\'t find file or read data")
else:
    print ("Written content in the file successfully")
```
![3](https://user-images.githubusercontent.com/115573041/208524382-3d360393-453a-458d-a05c-2812a8f8ff85.png)


## Fasal kecuali tanpa Pengecualian

- Anda juga dapat menggunakan pernyataan exception tanpa exception yang didefinisikan sebagai berikut:

try: You do your operations here; ...................... except: If there is any exception, then execute this block. ...................... else: If there is no exception then execute this block.

Pernyataan coba-kecuali jenis ini menangkap semua pengecualian pengecualian yang terjadi. Menggunakan percobaan seperti try-expect pernyataan tidak dianggap sebagai praktik pemrograman yang baik, karena mereka menangkap semuanya pengecualian tetapi tidak membuat programmer mengidentifikasi kemungkinan penyebab masalah terjadi

## Klausa kecuali dengan Berbagai Pengecualian

- Anda juga dapat menggunakan pernyataan exception yang sama untuk menangani beberapa exception sebagai berikut:

try: You do your operations here; ...................... except(Exception1[, Exception2[,...ExceptionN]]]): If there is any exception from the given exception list, then execute this block. ...................... else: If there is no exception then execute this block.

**Contoh**

- Jika Anda tidak memiliki izin untuk membuka file dalam mode tulis yang dapat ditulis, maka ini akan menghasilkan hasil berikut:
```py
try:
   fh = open("testfile", "w")
   fh.write("This is my test file for exception handling!!")
finally:
    print ("Error: can\'t find file or read data")
```
![3](https://user-images.githubusercontent.com/115573041/208524397-4e7dbd54-4ed0-406a-b1db-f4554e1fc543.png)


- Contoh yang sama dapat ditulis lebih bersih sebagai berikut:
```py
try:
    fh = open("testfile", "w")
    try:
        fh.write("This is my test file for exception handling!!")
    finally:
     print ("Going to close the file")
     fh.close()
except IOError:
   print ("Error: can\'t find file or read data")
```
![5](https://user-images.githubusercontent.com/115573041/208524443-bc56bdb1-ff8c-4d9e-8c74-dbb4fd60312e.png)
