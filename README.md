# H1D023029 TUGAS 6

Tugas 6: Passing Data Antar Halaman

Nama: Reva Septia Wulandari

NIM: H1D023029

Shift Baru: F

## Deskripsi Proyek 

Aplikasi Flutter sederhana ini mendemonstrasikan proses passing data (pengiriman data) dari satu halaman (form input) ke halaman lain (tampilan data). Aplikasi ini terdiri dari dua halaman utama:

- form_data.dart: Halaman untuk menginput Nama, NIM, dan Tahun Lahir.

- tampil_data.dart: Halaman untuk menampilkan data yang diinput, beserta perhitungan umur.

## Penjelasan Proses Passing Data dari Form Menuju Tampilan

Pada proyek Flutter ini, proses passing data dilakukan untuk memindahkan informasi yang diinputkan oleh pengguna pada halaman form input data (form_data.dart) menuju halaman tampilan hasil data (tampil_data.dart). Proses ini memanfaatkan parameter konstruktor antar class widget dan navigasi halaman menggunakan Navigator.push().

**1. Pengisian Data pada Form**

Halaman FormDataPage berfungsi sebagai tempat bagi pengguna untuk mengisi tiga jenis data, yaitu nama, NIM, dan tahun lahir.
Setiap komponen input menggunakan TextFormField dengan controller yang berfungsi untuk mengambil nilai dari teks yang dimasukkan pengguna.
Contoh deklarasi controller:

final _namaController = TextEditingController();
final _nimController = TextEditingController();
final _tahunController = TextEditingController();


**2. Validasi dan Pengiriman Data**

Setelah seluruh data diisi, pengguna menekan tombol "Simpan Data". Tombol tersebut akan memanggil fungsi _kirimData() yang bertugas untuk memvalidasi form dan melakukan navigasi ke halaman berikutnya apabila validasi berhasil.
Kode berikut menunjukkan proses tersebut:

void _kirimData() {
  if (_formKey.currentState!.validate()) {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => TampilDataPage(
          nama: _namaController.text,
          nim: _nimController.text,
          tahunLahir: _tahunController.text,
        ),
      ),
    );
  }
}


Pada bagian ini, data dikirim melalui parameter konstruktor TampilDataPage, sehingga nilai-nilai dari ketiga field dapat diteruskan ke halaman berikutnya.

**3. Penerimaan Data pada Halaman Tampilan**

Halaman TampilDataPage berfungsi untuk menerima dan menampilkan data yang telah dikirim dari halaman form.
Data diterima melalui konstruktor dengan menggunakan parameter bertipe String:

final String nama;
final String nim;
final String tahunLahir;

const TampilDataPage({
  Key? key,
  required this.nama,
  required this.nim,
  required this.tahunLahir,
}) : super(key: key);


Dengan demikian, data yang dikirim dari FormDataPage dapat diakses secara langsung melalui properti nama, nim, dan tahunLahir.

**4. Menampilkan Data pada Antarmuka**

Data yang diterima kemudian ditampilkan dalam elemen-elemen UI seperti Text dan Card.
Selain itu, dilakukan pula proses perhitungan usia berdasarkan tahun lahir yang diinputkan pengguna dengan menggunakan metode sederhana berikut:

int hitungUmur() {
  int tahun = int.parse(tahunLahir);
  return DateTime.now().year - tahun;
}


Nilai umur yang dihasilkan selanjutnya ditampilkan bersama data lainnya.

**5. Navigasi Kembali ke Halaman Form**

Pada halaman TampilDataPage, terdapat tombol “Kembali” yang memungkinkan pengguna untuk kembali ke halaman form dengan menggunakan perintah:

Navigator.pop(context);

Perintah ini menutup halaman tampilan dan mengembalikan pengguna ke halaman sebelumnya.

**Kesimpulan**
Proses passing data antar halaman pada aplikasi ini dilakukan melalui tiga tahapan utama:

1. Input data oleh pengguna pada halaman form menggunakan TextEditingController.
2. Pengiriman data ke halaman baru menggunakan konstruktor widget melalui Navigator.push().
3. Penerimaan dan penampilan data pada halaman tujuan dengan memanfaatkan parameter yang diterima dari konstruktor.

Dengan pendekatan ini, aplikasi dapat menampilkan data pengguna secara dinamis dan interaktif, sekaligus menerapkan prinsip stateful navigation dalam Flutter.

## Tampilan Aplikasi

### Halaman Form (form_data.dart)


### Halaman Tampil Data (tampil_data.dart)

