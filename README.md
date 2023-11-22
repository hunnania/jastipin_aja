Nama: Alifa Hanania Ardha<br>
NPM: 2206024392<br>
Kelas: PBP B<br>

# Tugas 9
1. Ya, kita bisa mengambil data JSON tanpa membuat model terlebih dahulu, tetapi itu dapat terjadi kalau kita tidak melakukan mapping data. Akan tetapi, membuat model terlebih dahulu tentu akan lebih optimal agar kode kita mudah dibaca dan diketahui tipe datanya.
2. CookieRequest dapat menghandle HTTPRequest dengan autentikasi berbasis cookie dan mengatur semua cookie untuk sesi user.
3. - Mendapatkan data json dari web tugas sebelumnya dengan fetch data
   - Membuat model Dart yang mencerminkan struktur data JSON agar dapat diakses Flutter.
   - Menggunakan metode json.decode untuk mengurai string JSON menjadi objek Dart.
   - Menampilkan data pada widget
4. User akan diminta untuk menginput username dan passwordnya pada halaman login. Kemudian, input-an user tersebut akan dicek dengan mengirimkan ke method login pada Django. Lalu, jika username dan password sudah benar, user dapat mengakses halam lain yang ada pada aplikasi. Jika tidak sesuai, user akan diminta lagi untuk menginput username dan password.
5. Berikut widget yang saya pakai dan fungsinya:<br>
| Widget | Fungsi | 
| ----- | ----- |
| MaterialPageRoute | Mengarahkan routing ke halaman (widget) tertentu | 
| Drawer | Membuat drawer navigator |
| ListTile | Membuat list beberapa tile |
| Scaffold | Mengatur layout dari widget yang ada di dalamnya |
| AppBar | Menambahkan bar aplikasi yang berisi title dengan align left | 
| Text | Berisi sebuah Text dengan properti di dalamnya |
| Center | Mengatur layout widget di dalamnya agar centered |
| Column | Mengatur layout widget di dalamnya agar turun ke bawah (tidak inline-flex) |
| TextStyle | Mengatur style dari sebuah text |
| Container | Menampung beberapa widget di dalamnya |

7. - membuat app django baru bernama authentication
   - membuat fungsi login pada views.py di authentication
   - Menginstall package pada proyek flutter dengan `flutter pub add provider` dan `flutter pub add pbp_django_auth`
   - membuat page login untuk aplikasi Flutter
   - membuat file `list_product.dart` untuk menampilkan semua item dalam card

# Tugas 8
1. `Navogator.push()` akan **menambahkan** route baru ke dalam route stack yang dikelola oleh Navigator, sedangkan `Navigator.pushReplacement()` akan **mengganti** route teratas pada route stack dengan route terbaru yang mau di-push ke stack tanpa mengubah kondisi elemen yang ada di bawahnya.
   Contoh penerapan `Navogator.push()` pada tugas sekarang ada pada `shop_card.dart` di mana ketika user menekan tombol "Tambah Item", route `ShopFormPage()` akan ditambahkan di atas stack dan menampilkan route `ShopFormPage()` dan dapat menekan tombol Back agar kembali ke halaman menu. Berikut potongan kodenya:
   ```dart
   if (item.name == "Tambah Item") {
      Navigator.push(context, MaterialPageRoute(builder: (context) => const ShopFormPage()));
   }
   ```
   
   Contoh penerapan `Navigator.pushReplacement()` pada tugas sekarang ada pada `left_drawer.dart` di mana ketika user menekan tombol "Tambah Item", route teratas pada stack akan di-replace dengan `ShopFormPage()` sehingga route yang ditampilkan ke user adalah route `ShopFormPage()`, tetapi user tidak dapat menekan tombol Back untuk kembali ke halaman menu secara langsung. Berikut potongan kodenya:
   ```dart
   ListTile(
      leading: const Icon(Icons.add_shopping_cart),
      title: const Text('Tambah Item'),
      // Bagian redirection ke ShopFormPage
      onTap: () {
         Navigator.pushReplacement(
         context,
         MaterialPageRoute(
            builder: (context) => const ShopFormPage(),
         ));
      },
   ),
   ```
2.  - Padding: mengatur seberapa jauh sebuah elemen dari tepi widget yang mengandungnya.
      ```dart
      child: Padding(
         padding: const EdgeInsets.all(10.0), // Set padding dari halaman
         child: Column(
         ...
         ),
      ),
      ```
    - GridView: untuk menampilkan item dalam bentuk grid atau kotak.
      ```dart
      GridView.count(
         // Container pada card kita.
         primary: true,
         padding: const EdgeInsets.all(20),
         crossAxisSpacing: 10,
         mainAxisSpacing: 10,
         crossAxisCount: 3,
         shrinkWrap: true,
         children: items.map((ShopItem item) {
            // Iterasi untuk setiap item
            return ShopCard(item);
         }).toList(),
       ),
      ```
    - Row dan Column: Row digunakan untuk mengatur widget secara horizontal, sementara Column digunakan untuk mengatur widget secara vertikal.
      ```dart
      child: Column(
         crossAxisAlignment: CrossAxisAlignment.start,
         children: [
         ...
         ],
      )
      ```
    - Align: untuk menempatkan widget dalam container sesuai dengan posisi yang diinginkan, seperti bagian atas, bawah, kiri, atau kanan.
      ```dart
      Align(
         alignment: Alignment.bottomCenter,
         child: Padding(
         ...
         ),
      )
      ```
    - ListView: untuk menampilkan daftar item yang dapat di-scroll.
      ```dart
      child: ListView(
         children: [
            const DrawerHeader(
            ...
            ),
         ],
      )
      ```
3. Elemen input form yang saya pakai hanya `TextFormField()` karena data yang saya butuhkan hanya barupa input teks atau angka.
4. Penerapan Clean Architecture pada aplikasi Flutter dapat membantu dalam mengorganisir kode kita dengan cara yang memisahkan logika bisnis dari detail implementasi dan infrastruktur. Clean Architecture memiliki beberapa lapisan utama, yaitu "Entity", "Use Case", "Interface Adapters", dan "Frameworks & Drivers".
   Langkah-langkah menerapkan clean architecture:
   - Tentukan entitas atau objek bisnis yang mewakili data atau model domain Anda.
   - Implementasikan entitas ini sebagai plain Dart objects atau menggunakan kelas data (data class) di Flutter.
   - Identifikasi use case atau fitur aplikasi yang mewakili tindakan tertentu dalam domain bisnis.
   - Implementasikan use case ini sebagai kelas Dart yang terpisah, yang bertanggung jawab untuk logika bisnis dan berkomunikasi dengan entitas.
   - Pisahkan antara logika bisnis (use case) dan detil implementasi seperti UI dan database.
   - Buat kelas atau modul yang bertanggung jawab untuk mengonversi data dari format yang digunakan di dalam use case ke format yang sesuai untuk UI atau infrastruktur.
   - Gunakan Presenter atau ViewModel untuk menghubungkan logika bisnis dengan tampilan (UI) di Flutter.
   - Tempatkan seluruh kode yang berkaitan dengan kerangka kerja dan infrastruktur di lapisan framework & drivers.
   - Implementasikan repository yang berkomunikasi dengan data sumber eksternal seperti database atau API.
   - Gunakan widget Flutter dan fungsi framework untuk menghubungkan UI dengan presentasi.
   - Gunakan teknik Dependency Injection untuk memasukkan dependensi ke dalam kelas-kelas kita. Di Flutter, kita bisa menggunakan package seperti get_it atau provider untuk mengelola dependensi.
   - Pastikan setiap lapisan dapat diuji secara terpisah.
   - Tulis unit test untuk setiap use case dan fungsi bisnis.
   - Mock dependensi untuk mengisolasi setiap lapisan selama pengujian.
5. - membuat left_drawer.dart yang berfungsi seperti navbar
   - membuat shoplist_form.dart yang berisikan Class untuk membuat model saya.
   - membuat form yang meminta input sesuai dengan model tersebut.
   - membuat validasi pada input form
   - membuat dialog window yang akan memunculkan apa yang sudah saya input
   - mengatur semua navigasi buttonnya ke window yang dituju

# Tugas 7
1. Stateless widget berarti semua konfigurasi yang ada sudah diinisiasi di awal, sedangkan Stateful widget bersifat dinamis yang berarti widget dapat diganti atau diperbaharui kapan pun berdasarkan aksi atau saat terjadi perubahan data.
2. - "MyApp": widget yang berfungsi sebagai widget utama aplikasi
   - "MaterialApp": berfungsi mengatur tema aplikasi seperti "title", "theme", dan "home".
   - "title": berfungsi mengatur judul aplikasi yang ditampilkan pada toolbar.
   - "theme": berfungsi mengatur tapilan elemen-elemen pada aplikasi.
   - "useMaterial3": berfungsi mengatur penggunaan Material You (Material Design 3.0) pada aplikasi.
   - "home": berfungsi mengatur halaman beranda aplikasi yaitu "MyHomePage".
   - "Scaffold": berfungsi mengatur elemen-elemen dasar seperti "AppBar", body, dan lain-lain.
   - "AppBar": berfungsi mengatur bagian atas aplikasi yang menampilkan "title".
   - "SingleChildScrollView": berfungsi sebagai container aplikasi agar konten aplikasi tidak melebihi ukuran windows.
   - "Padding": berfungsi sebagai padding yang mengatur jarak antar elemen.
   - "Column": berfungsi mengatur widget agar ditampilkan secara vertikal.
   - "Text": berfungsi menampilkan tulisan dengan gaya tertentu.
   - "GridView.count": berfungsi membuat layout grid dengan jumlah kolom yang tetap
   - "ShopItem": berfungsi menampilkan informasi tentang item toko seperti nama dan ikon.
   - "ShopCard": berfungsi membuat card yang menampilkan item toko.
   - "Material": berfungsi untuk pengatur tampilan card seperti warna.
   - "InkWell": berfungsi memberikan respons saat tombol ditekan.
   - "Icon": berfungsi untuk menampilkan ikon.
   - "SnackBar": berfungsi untuk menampilkan pesan saat tombol ditekan pengguna.
3. - Membuat aplikasi flutter bernama "jastipin_aja" dengan menjalankan flutter create "jastipin_aja" pada cmd
   - Membuat kelas MyApp yang mengatur aplikasi utama pada file main.dart
   - Mengatur widget pada aplikasi utama seperti colorScheme
   - Membuat file menu.dart dan kelas MyHomePage yang mengatur tampilan homepage
   - Membuat kelas ShopItem yang mengatur objek tombol pada homepage
   - Membuat kelas ShopCard (stateless widget) yang mengatur tampilan tombol
   - Membuat 3 tombol yaitu tombol "Lihat Item", "Tambah Item", dan "Logout"
   - Mengatur warna 3 tombol tersebut dengan warna yang berbeda-beda
