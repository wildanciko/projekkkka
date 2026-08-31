Berikut adalah versi jawaban Tugas Analisis Praktikum 1–6 dengan bahasa yang lebih natural, mengalir, dan mudah dipahami, tetap rapi serta tanpa emoji.

JAWABAN TUGAS ANALISIS PRAKTIKUM 1–6
Praktikum 1: Konsep Dasar Class, Object, dan Attribute
Pertanyaan:

Apa yang terjadi jika kamu mengubah hero1.hp menjadi 500 setelah baris hero1 = Hero(...)? Coba lakukan print(hero1.hp).

Jawaban:

Nilai HP dari hero1 akan langsung berubah menjadi 500, dan saat di-print nilainya juga menampilkan 500.

Penjelasan:

Hal ini terjadi karena variabel self.hp di Python bersifat public secara default. Jadi, kodenya bisa diakses dan diubah nilainya secara langsung dari luar class tanpa ada batasan atau validasi sama sekali.

Praktikum 2: Method dan Interaksi Antar Objek
Pertanyaan:

Perhatikan parameter lawan pada method serang. Parameter tersebut menerima sebuah objek utuh, bukan hanya string nama. Mengapa ini penting?

Jawaban:

Parameter tersebut harus menerima objek utuh agar method serang bisa berinteraksi langsung dengan data dan fungsi milik objek lawan.

Penjelasan:

Dengan membawa objek utuh, method serang bisa membaca data lawan (seperti nama atau daya serangnya) sekaligus langsung memanggil method lawan.diserang() untuk mengurangi HP lawan di memori. Kalau yang dikirim cuma string nama seperti "Zilong", program cuma mengolah teks biasa dan tidak bisa mengubah status HP objek Zilong yang sebenarnya.

Praktikum 3: Inheritance (Pewarisan) dan Super()
Pertanyaan 1:

Error apa yang muncul saat kamu mencoba melihat info Eudora (eudora.info()) setelah menghapus/menjadikan komentar baris super().__init__(name, hp, attack_power)? Mengapa error tersebut mengatakan Mage object has no attribute 'name'?

Jawaban:

Error yang keluar adalah AttributeError: 'Mage' object has no attribute 'name'.

Penjelasan:

Penyebabnya karena method __init__ di class Mage menimpa (override) method __init__ milik parent class (Hero). Saat baris super().__init__() dihapus atau di-comment, proses pembuatan atribut dasar seperti name, hp, dan attack_power dari class Hero jadi tidak pernah dijalankan.

Pertanyaan 2:

Jelaskan peran fungsi super() dalam menghubungkan data dari class Anak ke class Induk!

Jawaban:

Fungsi super() bertugas untuk memanggil constructor atau method milik parent class. Perannya adalah meneruskan data dari class anak ke class induk, supaya atribut dasarnya bisa langsung dibuat tanpa perlu kita tulis ulang kodenya dari awal.

Praktikum 4: Encapsulation dan Access Modifier
Pertanyaan 1 (Percobaan Hacking):

Apakah nilai HP muncul atau Error saat menjalankan print(f"Mencoba akses paksa: {hero1._Hero__hp}")? Jelaskan konsep Name Mangling!

Jawaban:

Nilainya tetap muncul dan tidak error.

Penjelasan:

Ini terjadi karena Python menggunakan fitur bernama Name Mangling. Ketika kita membuat variabel private dengan dua garis bawah (__hp), Python di balik layar mengubah nama variabel itu menjadi _NamaClass__namaVariabel. Walaupun cara ini bisa dipakai untuk "mengintip" data private, tindakan ini melanggar aturan enkapsulasi dan sebaiknya dihindari agar data program tidak rusak secara tidak sengaja.

Pertanyaan 2 (Uji Validasi Setter):

Apa yang terjadi jika logika if/elif di dalam method set_hp dihapus lalu dijalankan hero1.set_hp(-100)? Mengapa keberadaan method Setter sangat penting?

Jawaban:

Nilai HP hero akan langsung berubah menjadi -100, padahal nilai HP minus itu tidak masuk akal dalam game.

Penjelasan:

Di sinilah pentingnya method Setter. Setter berfungsi sebagai satpam atau pemvalidasi data sebelum disimpan ke dalam objek. Jadi data yang masuk dijamin selalu sesuai aturan (misalnya HP tidak boleh bernilai negatif).

Praktikum 5: Abstraction dan Interface (abc Module)
Pertanyaan 1 (Melanggar Kontrak):

Error apa yang muncul saat seluruh blok def serang di class Hero dihapus? Jelaskan arti pesan error tersebut!

Jawaban:

Pesan error yang muncul adalah TypeError: Can't instantiate abstract class Hero with abstract method serang.

Penjelasan:

Artinya, class GameUnit sudah menetapkan aturan bahwa method serang() hukumnya wajib ada (melalui @abstractmethod). Kalau class Hero tidak membuat method serang(), maka Hero masih dianggap sebagai class abstrak yang belum lengkap, sehingga Python melarang kita untuk membuat objek dari class tersebut.

Pertanyaan 2 (Mencetak Cetakan):

Mengapa class GameUnit dilarang untuk dibuat menjadi objek (unit = GameUnit())? Apa gunanya jika tidak bisa dibuat objek nyata?

Jawaban:

GameUnit dilarang dibuat jadi objek karena sifatnya masih berupa kerangka abstrak yang isi method-nya belum ada logika pastinya.

Penjelasan:

Gunanya dibuat class abstrak adalah sebagai patokan atau standar (interface). Dengan begitu, semua class turunannya (seperti Hero atau Monster) dijamin punya struktur method yang seragam.

Praktikum 6: Polymorphism
Pertanyaan 1 (Uji Skalabilitas - Class Healer):

Apakah program berjalan lancar setelah menambahkan class Healer ke daftar pasukan? Apa keuntungan Polimorfisme?

Jawaban:

Program tetap berjalan lancar tanpa ada error sama sekali.

Penjelasan:

Inilah keuntungan utama dari Polimorfisme. Kita bisa menambah jenis karakter baru (seperti Healer) kapan saja tanpa perlu mengubah kode perulangan utama (for pahlawan in pasukan:). Kodenya jadi jauh lebih fleksibel dan gampang dikembangkan di kemudian hari.

Pertanyaan 2 (Konsistensi Penamaan):

Apa yang terjadi jika nama method serang pada class Archer diubah menjadi tembak_panah? Mengapa nama method harus persis sama?

Jawaban:

Saat perulangan memanggil pahlawan.serang(), objek Archer tidak akan menjalankan tembak_panah(), melainkan malah memanggil method serang() bawaan dari parent class-nya.

Penjelasan:

Nama method harus dibuat sama persis supaya fitur Polimorfisme bisa bekerja. Dengan nama yang sama, satu perintah pemanggilan yang sederhana bisa langsung mengenali dan menjalankan aksi yang sesuai dengan masing-masing jenis objek