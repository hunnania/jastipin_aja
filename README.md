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
2.  

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
