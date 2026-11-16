# myportofolio_mobile
Nama : Zhafira Richas

NPM : 2506540941

Kelas : PBP C

## Pertanyaan Reflektif
### TUGAS 7
1. __Jelaskan apa yang dimaksud dengan widget tree pada Flutter dan bagaimana hubungan induk-anak (parent-child) bekerja antar-widget!__

    Widget Tree adalah struktur hierarki berbentuk pohon yang merepresentasikan seluruh elemen User interface dalam aplikasi Flutter. Di Flutter, hampir segalanya adalah widget (mulai dari teks, tombol, gambar, hingga tata letak seperti padding dan baris).

2. __Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya masing-masing!__

    MaterialApp: Menyediakan struktur dasar aplikasi berbasis Material Design, termasuk pengaturan tema global, rute navigasi, dan lokalisasi.

    Scaffold: Menyediakan kerangka tata letak visual standar untuk sebuah halaman layar, seperti area AppBar, body, serta dukungan untuk memunculkan SnackBar.

    AppBar: Menampilkan bilah navigasi di bagian paling atas halaman yang berisi judul aplikasi (MyPortfolio).
    Text: Menampilkan tulisan di layar dengan gaya tertentu (ukuran, ketebalan, warna).

    Padding: Memberikan jarak  di sekeliling widget child-nya agar tampilan tidak menempel langsung ke tepi layar atau elemen lain.
    
    Column: Menyusun daftar widget children secara vertikal.
    
    Row: Menyusun daftar widget children secara horizontal.
    
    InfoCard (Custom StatelessWidget): Widget buatan sendiri yang membungkus Card untuk menampilkan informasi profil (NPM, Name, Class) secara rapi.
    
    Card: Menampilkan wadah berbentuk kotak dengan sudut membulat dan efek bayangan (elevation) untuk mengelompokkan informasi.
    
    Container: Widget serbaguna yang digunakan di sini untuk mengatur lebar kartu profil secara proporsional serta memberikan padding.
    
    SizedBox: Membuat kotak kosong dengan ukuran tetap untuk memberikan jarak antar-widget.
    
    Center: Memosisikan widget child tepat di tengah ruang yang tersedia pada parent-nya.
    
    GridView (GridView.
    count): Menampilkan daftar widget dalam tata letak kisi (grid) 2 dimensi dengan jumlah kolom tetap (3 kolom).
    
    ItemCard (Custom StatelessWidget): Widget buatan sendiri yang merepresentasikan setiap kartu tombol menu di dalam GridView.
    
    Material: Memberikan permukaan visual berbahan Material Design,termasuk warna latar belakang tombol dan sudut melengkung borderRadius.

    InkWell: Membuat area widget menjadi interaktif sehingga dapat merespons sentuhan pengguna (onTap)
    SnackBar: Menampilkan pesan pemberitahuan singkat di bagian bawah layar saat tombol menu ditekan.
    
    Icon: Menampilkan ikon grafis (seperti Icons.folder, Icons.add_circle, dan Icons.logout)

3. __Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini umumnya digunakan sebagai root widget pada aplikasi Flutter!__

    Fungsinya, widget pembungkus tingkat atas yang mengonfigurasi berbagai kebutuhan esensial aplikasi bergaya Material Design, seperti sistem navigasi, tema warna dan, judul aplikasi pada task switcher OS, serta dukungan bahasa/lokalisasi.
    Umumnya digunakan sebagai root widget, karena widget-widget turunan di dalam Flutter membutuhkan informasi konfigurasi global dari MaterialApp agar dapat berfungsi dan merender tampilannya dengan benar. Dengan meletakkan MaterialApp sebagai root, seluruh halaman dan komponen di bawahnya otomatis memiliki akses terhadap tema, navigasi, arah teks, serta komponen Material Design tanpa harus mengaturnya berulang kali di setiap halaman.

4. __Jelaskan perbedaan antara StatelessWidget dan StatefulWidget! Kapan kita sebaiknya memilih StatelessWidget dan kapan harus menggunakan StatefulWidget?__

    StatelessWidget : Immutable, pembaruan UI Hanya dirender ulang jika konfigurasi dari parent-nya berubah, dan performa lebih ringan dan hemat memori karena tidak menyimpan status internal.
    Gunakan StatelessWidget ketika tampilan komponen hanya bergantung pada data awal yang dikirimkan melalui konstruktor dan tidak perlu berubah akibat interaksi pengguna di dalam widget itu sendiri.

    StatefulWidget : Mutable, dapat merender ulang dirinya sendiri kapan saja dengan memanggil fungsi setState(), dan sedikit lebih kompleks karena mengelola lifecycle objek State.
    Gunakan StatefulWidget ketika tampilan UI harus berubah secara dinamis sebagai respons terhadap interaksi pengguna atau aliran data.

5. __Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di dalam metode build?__

    BuildContext adalah objek yang merepresentasikan lokasi atau alamat spesifik sebuah widget di dalam Widget Tree. Setiap widget memiliki objek BuildContext-nya sendiri. Karena struktur aplikasi Flutter berbentuk pohon yang sangat dalam, sebuah widget membutuhkan BuildContext untuk berkomunikasi dengan widget lain di atasnya (ancestor) dan mencari informasi yang berada di posisi lebih tinggi pada pohon tersebut.Penggunaannya di dalam metode build dengan parameter context digunakan untuk:

    Mengambil Tema Global : Theme.of(context).colorScheme.primary menelusuri Widget Tree ke atas untuk menemukan ThemeData dari MaterialApp dan mengambil warna utamanya.   
    Membaca Ukuran Layar Perangkat: MediaQuery.of(context).size.width mencari widget MediaQuery di atasnya guna mendapatkan lebar layar perangkat agar lebar InfoCard dapat dibagi secara proporsional.   
    Menampilkan UI Overlay: ScaffoldMessenger.of(context) mencari Scaffold terdekat di atas ItemCard agar aplikasi tahu di mana SnackBar harus dimunculkan

6. __Jelaskan konsep hot reload di Flutter dan apa perbedaannya dengan hot restart! Kapan kita tidak bisa hanya mengandalkan hot reload dan harus melakukan hot restart atau full restart?__

    Hot reload bekerja dengan cara memasukan source code yang baru diubah ke dalam mesin virtual Dart (Dart Virtual Machine / VM) yang sedang berjalan. Setelah VM memperbarui kelas dan fungsi yang diubah, Flutter secara otomatis rebuild Widget Tree sehingga perubahan UI langsung terlihat dalam hitungan milidetik tanpa kehilangan state aplikasi saat ini.

    Hot Reload: Mempertahankan state aplikasi, misalnya posisi halaman saat ini atau teks yang sudah diketik di formulir dan tidak menjalankan ulang fungsi main().
    Hot Restart: Menghancurkan seluruh state aplikasi, compile ulang kode Dart dari awal, dan menjalankan kembali fungsi main() sehingga aplikasi kembali ke layar awal.

    Harus melakukan Hot reload ketika:
    Mengubah struktur kelas secara signifikan (misalnya mengubah StatelessWidget menjadi StatefulWidget atau sebaliknya).
    Mengubah inisialisasi variabel global, variabel static, atau kode di dalam fungsi main() dan initState().
    Mengubah tipe data pada enum atau kelas generik.
    
    Harus melakukan Full Restart  ketika:
    Menambahkan atau memperbarui plugin / pustaka pihak ketiga di file pubspec.yaml yang melibatkan kode native (Android/iOS).
    Mengubah file konfigurasi native (seperti AndroidManifest.xml, build.gradle, atau Info.plist).
    Menambahkan aset baru (seperti gambar atau font) di folder proyek yang baru didaftarkan pada pubspec.yaml.

## AI Disclosure
### Tugas 7
    Untuk penggunaan gen ai pada tugas ini, saya menggunakan Gemini. Penggunaan ai hanya untuk memahami agar bisa menjawab beberapa pertanyaan reflektif.




