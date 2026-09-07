Praktikum 1: Konsep Dasar Class, Object, dan Attribute
Pertanyaan:
Apa yang terjadi jika kamu mengubah hero1.hp menjadi 500 setelah baris hero1 = Hero(...)? Coba lakukan print(hero1.hp).

Jawaban:
Nilai HP hero1 bakal langsung berubah jadi 500, dan saat di-print, output-nya juga menampilkan angka 500.

Penjelasan:
Di Python, variabel seperti self.hp itu sifatnya public secara default. Efeknya, kita bisa langsung ngakses atau ngubah nilainya dari luar class kapan saja tanpa ada batasan atau validasi khusus.

Praktikum 2: Method dan Interaksi Antar Objek
Pertanyaan:
Perhatikan parameter lawan pada method serang. Parameter tersebut menerima sebuah objek utuh, bukan hanya string nama. Mengapa ini penting?

Jawaban:
Soalnya method serang butuh akses langsung ke data sekaligus fungsi milik objek lawan tersebut.

Penjelasan:
Kalau kita ngirim objek utuh, method serang nggak cuma bisa baca datanya (kayak nama atau attack power), tapi juga bisa langsung manggil method lawan.diserang() buat motong HP-nya di memori. Kalau cuma ngirim string nama kayak "Zilong", Python cuma menganggapnya teks biasa—nggak bakal bisa ngutak-atik status HP milik objek Zilong yang asli.

Praktikum 3: Inheritance (Pewarisan) dan Super()
Pertanyaan 1:
Error apa yang muncul saat kamu mencoba melihat info Eudora (eudora.info()) setelah menghapus/menjadikan komentar baris super().__init__(name, hp, attack_power)? Mengapa error tersebut mengatakan Mage object has no attribute 'name'?

Jawaban:
Error yang muncul itu AttributeError: 'Mage' object has no attribute 'name'.

Penjelasan:
Masalahnya ada di method __init__ milik class Mage yang menimpa (override) __init__ kepunyaan parent class (Hero). Pas perintah super().__init__() dihapus atau di-comment, proses penyiapan atribut dasar—kayak name, hp, sama attack_power dari Hero—dilewati begitu aja alias nggak pernah dijalankan.

Pertanyaan 2:
Jelaskan peran fungsi super() dalam menghubungkan data dari class Anak ke class Induk!

Jawaban:
Fungsi super() dipake buat nembus dan manggil constructor atau method milik parent class. Peran utamanya ngoper data dari class anak ke class induk, jadi kita nggak perlu repot-repot nulis ulang kode inisialisasi atribut dari nol.

Praktikum 4: Encapsulation dan Access Modifier
Pertanyaan 1 (Percobaan Hacking):
Apakah nilai HP muncul atau Error saat menjalankan print(f"Mencoba akses paksa: {hero1._Hero__hp}")? Jelaskan konsep Name Mangling!

Jawaban:
Nilainya tetap muncul dan kodenya berjalan normal tanpa error.

Penjelasan:
Ini bisa terjadi karena Python menerapkan mekanisme Name Mangling. Saat kita bikin atribut private pakai dua underscore (__hp), Python bakal ngubah nama variabel itu secara internal jadi _NamaClass__namaVariabel. Walaupun trik ini bisa dipakai buat "mengintip" variabel private, cara ini sebenarnya menyalahi aturan enkapsulasi dan sebaiknya dihindari supaya data program nggak sengaja rusak.

Pertanyaan 2 (Uji Validasi Setter):
Apa yang terjadi jika logika if/elif di dalam method set_hp dihapus lalu dijalankan hero1.set_hp(-100)? Mengapa keberadaan method Setter sangat penting?

Jawaban:
HP hero bakal langsung jebol ke angka -100, padahal nilai minus itu nggak masuk akal dalam gameplay.

Penjelasan:
Di sinilah fungsi krusial Setter. Dia bertindak layaknya filter atau "satpam" yang menyeleksi data sebelum disimpan ke dalam objek. Jadi, data yang masuk dipastikan selalu aman dan sesuai aturan (misalnya, HP nggak boleh kurang dari 0).

Praktikum 5: Abstraction dan Interface (abc Module)
Pertanyaan 1 (Melanggar Kontrak):
Error apa yang muncul saat seluruh blok def serang di class Hero dihapus? Jelaskan arti pesan error tersebut!

Jawaban:
Pesan error-nya: TypeError: Can't instantiate abstract class Hero with abstract method serang.

Penjelasan:
Singkatnya, class GameUnit udah bikin aturan wajib kalau semua turunannya harus punya method serang() (lewat dekorator @abstractmethod). Karena class Hero nggak menyediakan method tersebut, Python menganggap Hero masih berupa class abstrak yang belum selesai. Makanya, kita dilarang bikin objek dari class tersebut.

Pertanyaan 2 (Mencetak Cetakan):
Mengapa class GameUnit dilarang untuk dibuat menjadi objek (unit = GameUnit())? Apa gunanya jika tidak bisa dibuat objek nyata?

Jawaban:
Soalnya GameUnit cuma berupa cetak biru atau kerangka abstrak yang method-nya belum punya isi/logika yang jelas.

Penjelasan:
Tujuan dibikinnya class abstrak adalah sebagai panduan atau standar (interface). Fungsinya buat memastikan semua class turunan (kayak Hero atau Monster) punya struktur dan nama method yang seragam.

Praktikum 6: Polymorphism
Pertanyaan 1 (Uji Skalabilitas - Class Healer):
Apakah program berjalan lancar setelah menambahkan class Healer ke daftar pasukan? Apa keuntungan Polimorfisme?

Jawaban:
Program tetap berjalan mulus tanpa kendala sama sekali.

Penjelasan:
Ini dia keunggulan utama Polimorfisme. Kita bebas nambahin jenis karakter baru (kayak Healer) kapan aja tanpa perlu mengacak-acak kode perulangan utamanya (for pahlawan in pasukan:). Kodenya jadi lebih fleksibel dan gampang kalau mau dikembangin lagi nanti.

Pertanyaan 2 (Konsistensi Penamaan):
Apa yang terjadi jika nama method serang pada class Archer diubah menjadi tembak_panah? Mengapa nama method harus persis sama?

Jawaban:
Saat looping memanggil pahlawan.serang(), objek Archer nggak bakal menjalankan tembak_panah(). Objek tersebut malah bakal memanggil method serang() bawaan dari parent class-nya.

Penjelasan:
Nama method wajib dibuat persis sama supaya Polimorfisme bisa jalan. Dengan nama yang konsisten, satu perintah panggil yang sederhana bisa langsung mengenali dan menjalankan tindakan yang sesuai dengan karakteristik tiap-tiap objek.
