# H1D023029 TUGAS 6

Tugas 6: Passing Data Antar Halaman

Nama: Reva Septia Wulandari

NIM: H1D023029

Shift Baru: F

## Deskripsi Aplikasi

Aplikasi Flutter sederhana ini mendemonstrasikan proses passing data (pengiriman data) dari satu halaman (form input) ke halaman lain (tampilan data). Aplikasi ini terdiri dari dua halaman utama:

- form_data.dart: Halaman untuk menginput Nama, NIM, dan Tahun Lahir.

- tampil_data.dart: Halaman untuk menampilkan data yang diinput, beserta perhitungan umur.

## Penjelasan Proses Passing Data dari Form Menuju Tampilan

Proses *passing data* dilakukan untuk memindahkan informasi dari halaman FormDataPage menuju TampilDataPage.  
Teknik yang digunakan adalah parameter konstruktor antar widget dan navigasi halaman menggunakan `Navigator.push()`.

---

### Pengisian Data pada Form

Halaman `FormDataPage` berfungsi untuk menginput tiga data utama:  
- Nama  
- NIM  
- Tahun Lahir  

Setiap input menggunakan `TextFormField` dengan controller yang menyimpan teks pengguna.

📁 **`lib/ui/form_data.dart`**
```dart
final _namaController = TextEditingController();
final _nimController = TextEditingController();
final _tahunController = TextEditingController();

```

### Validasi dan Pengiriman Data

Setelah seluruh data diisi, pengguna menekan tombol "Simpan Data".
Tombol tersebut akan memanggil fungsi _kirimData() yang bertugas untuk memvalidasi form dan melakukan navigasi ke halaman berikutnya apabila validasi berhasil.

📁 **`lib/ui/form_data.dart`**
Kode berikut menunjukkan proses tersebut:
```dart
// Ambil data dari controller, validasi, lalu kirim
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => TampilDataScreen(
      nama: _namaController.text,
      nim: _nimController.text,
      tahunLahir: _tahunController.text,
    ),
  ),
);
```
Pada bagian ini, data dikirim melalui parameter konstruktor TampilDataPage, sehingga nilai-nilai dari ketiga field dapat diteruskan ke halaman berikutnya.

### Penerimaan Data pada Halaman Tampilan
Halaman TampilDataPage berfungsi untuk menerima dan menampilkan data yang telah dikirim dari halaman form.
Data diterima melalui konstruktor dengan menggunakan parameter bertipe String:

📁 **`lib/ui/tampil_data.dart`**
```dart
final String nama;
final String nim;
final String tahunLahir;

const TampilDataPage({
  Key? key,
  required this.nama,
  required this.nim,
  required this.tahunLahir,
}) : super(key: key);
```
Dengan demikian, data yang dikirim dari FormDataPage dapat diakses secara langsung melalui properti nama, nim, dan tahunLahir.

### Menampilkan Data pada Antarmuka
Data yang diterima kemudian ditampilkan dalam elemen-elemen UI seperti Text dan Card.
Selain itu, dilakukan pula proses perhitungan usia berdasarkan tahun lahir yang diinputkan pengguna dengan menggunakan metode sederhana berikut:

📁 **`lib/ui/tampil_data.dart`**
```dart
int hitungUmur() {
  int tahun = int.parse(tahunLahir);
  return DateTime.now().year - tahun;
}
```
Nilai umur yang dihasilkan selanjutnya ditampilkan bersama data lainnya.

### Navigasi Kembali ke Halaman Form
Pada halaman TampilDataPage, terdapat tombol “Kembali” yangmemungkinkan pengguna untuk kembali ke halaman form dengan menggunakan perintah:

📁 **`lib/ui/tampil_data.dart`**
```dart
Navigator.pop(context);
```
Perintah ini menutup halaman tampilan dan mengembalikan pengguna ke halaman sebelumnya.

### Kesimpulan
Proses passing data antar halaman pada aplikasi ini dilakukan melalui tiga tahapan utama:

1. Input data oleh pengguna pada halaman form menggunakan TextEditingController.
2. Pengiriman data ke halaman baru menggunakan konstruktor widget melalui Navigator.push().
3. Penerimaan dan penampilan data pada halaman tujuan dengan memanfaatkan parameter yang diterima dari konstruktor.

Dengan pendekatan ini, aplikasi dapat menampilkan data pengguna secara dinamis dan interaktif, sekaligus menerapkan prinsip stateful navigation dalam Flutter.

### Tampilan Aplikasi
<img width="1365" height="686" alt="image" src="https://github.com/user-attachments/assets/32be24e2-f837-4fb6-bc5e-ff38dcb11113" />

### Halaman Form (form_data.dart)
<img width="1365" height="678" alt="image" src="https://github.com/user-attachments/assets/eb9d9b2a-6c14-43dd-a297-e497532cc7c8" />

### Halaman Tampil Data (tampil_data.dart)
<img width="1364" height="678" alt="image" src="https://github.com/user-attachments/assets/9d20bf9a-3def-4372-b84a-d4e1cbda80ce" />


