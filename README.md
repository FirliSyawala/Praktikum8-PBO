# Praktikum Pemrograman Berorientasi Objek (PBO)
## Struktur Folder

Praktikum8-PBO/
├── src/
│   └── praktikum8/
│       └── pbo/
│           ├── AlatElektronik.java
│           ├── Anjing.java
│           ├── BangunDatar.java
│           ├── Hewan.java
│           ├── Kamera.java
│           ├── Kucing.java
│           ├── Lingkaran.java
│           ├── PoliTester.java
│           ├── Smartphone.java
│           ├── TesBangunDatar.java
│           └── TesSmartphone.java
└── README.md
## Identitas

Nama: Firli Syawala

NIM: L0325025

## Package

Package yang digunakan dalam program ini adalah praktikum8.pbo. Package berfungsi untuk mengelompokkan class agar kode program lebih terorganisasi dan mudah dikelola.

Deklarasi package pada setiap file Java:

package praktikum8.pbo;
## 1. Hewan.java

### Deklarasi Class dan Method

public class Hewan {
    public void bersuara() {
        System.out.println(
            "Hewan ini mengeluarkan suara yang tidak spesifik."
        );
    }
}
Penjelasan:

- public class Hewan merupakan deklarasi class induk bernama Hewan.
- public void bersuara() merupakan method yang digunakan untuk menampilkan suara hewan.
- System.out.println() berfungsi menampilkan teks ke layar.

Class ini menjadi class induk yang diwarisi oleh class Kucing dan Anjing.

## 2. Kucing.java

### Penerapan Inheritance dan Method Overriding

public class Kucing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Kucing: Mew meow!");
    }
}
Penjelasan:

- extends Hewan menunjukkan bahwa class Kucing mewarisi class Hewan.
- @Override menandakan bahwa method bersuara() ditulis ulang dari class induk.
- Method bersuara() menampilkan suara khas kucing.

Class ini menerapkan inheritance atau pewarisan dan method overriding.

## 3. Anjing.java

### Penerapan Inheritance dan Method Overriding

public class Anjing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Anjing: Guk guk");
    }
}
Penjelasan:

- extends Hewan membuat class Anjing menjadi turunan dari class Hewan.
- @Override digunakan untuk menandai penulisan ulang method bersuara().
- Method tersebut menampilkan suara khas anjing.

Class Kucing dan Anjing memiliki method yang sama, tetapi menghasilkan keluaran berbeda.

## 4. PoliTester.java

### Pengujian Polymorphism

public class PoliTester {
    public static void main(String[] args) {
        Hewan[] daftarHewan = new Hewan[3];
        daftarHewan[0] = new Hewan();
        daftarHewan[1] = new Kucing();
        daftarHewan[2] = new Anjing();

        for (Hewan h : daftarHewan) {
            h.bersuara();
        }
    }
}
Penjelasan:

- main() merupakan method utama yang dijalankan pertama kali.
- Hewan[] daftarHewan = new Hewan[3] membuat array yang dapat menampung tiga objek bertipe Hewan.
- Objek Hewan, Kucing, dan Anjing dimasukkan ke dalam array tersebut.
- Perulangan for-each digunakan untuk mengakses setiap objek.
- h.bersuara() memanggil method yang sesuai dengan jenis objek.

Program ini menerapkan polymorphism karena pemanggilan method yang sama menghasilkan keluaran berbeda sesuai objeknya. Penyimpanan objek Kucing dan Anjing dalam variabel bertipe Hewan juga menunjukkan upcasting.

## 5. BangunDatar.java

### Penerapan Abstract Class

public abstract class BangunDatar {
    String warna;

    public BangunDatar(String warna) {
        this.warna = warna;
    }

    public abstract double hitungLuas();

    public void cetakWarna() {
        System.out.println(
            "Warna bangun ini adalah: " + warna
        );
    }
}
Penjelasan:

- abstract class BangunDatar merupakan class abstrak yang menjadi dasar bagi class turunannya.
- - Atribut warna digunakan untuk menyimpan warna bangun datar.
- Constructor BangunDatar(String warna) digunakan untuk mengisi nilai warna.
- hitungLuas() merupakan method abstrak yang wajib diimplementasikan oleh class turunannya.
- cetakWarna() merupakan method biasa yang digunakan untuk menampilkan warna bangun datar.

Class abstrak ini tidak dapat dibuat menjadi objek secara langsung.

## 6. Lingkaran.java

### Implementasi Abstract Class

public class Lingkaran extends BangunDatar {
    private double jariJari;

    public Lingkaran(String warna, double jariJari) {
        super(warna);
        this.jariJari = jariJari;
    }

    @Override
    public double hitungLuas() {
        return Math.PI * jariJari * jariJari;
    }
}
Penjelasan:

- extends BangunDatar menunjukkan bahwa Lingkaran merupakan turunan dari class BangunDatar.
- Atribut jariJari digunakan untuk menyimpan panjang jari-jari lingkaran.
- Constructor menerima parameter warna dan jari-jari.
- super(warna) memanggil constructor dari class induk untuk mengisi warna.
- this.jariJari = jariJari menyimpan nilai jari-jari ke dalam atribut objek.
- Method hitungLuas() menghitung luas lingkaran menggunakan rumus π × r × r.
- Math.PI merupakan konstanta nilai π yang tersedia dalam Java.

## 7. TesBangunDatar.java

### Pengujian Abstract Class

public class TesBangunDatar {
    public static void main(String[] args) {
        Lingkaran lingkaran = new Lingkaran("Merah", 5);

        lingkaran.cetakWarna();
        System.out.println(
            "Luas lingkaran: " + lingkaran.hitungLuas()
        );
    }
}
Penjelasan:

- Program membuat objek Lingkaran dengan warna merah dan jari-jari 5.
- lingkaran.cetakWarna() menampilkan warna lingkaran.
- lingkaran.hitungLuas() menghitung luas lingkaran.
- Hasil perhitungan luas lingkaran dengan jari-jari 5 adalah sekitar 78,54.

Program ini menunjukkan penggunaan class turunan untuk mengimplementasikan method abstrak dari class induk.

## 8. AlatElektronik.java

### Deklarasi Interface

public interface AlatElektronik {
    void nyalakan();
    void matikan();
}
Penjelasan:

- interface AlatElektronik mendefinisikan kemampuan yang harus dimiliki oleh class yang mengimplementasikannya.
- nyalakan() merupakan method untuk menyalakan perangkat elektronik.
- matikan() merupakan method untuk mematikan perangkat elektronik.

Interface ini menjadi pedoman bagi class yang menerapkan fungsi dasar perangkat elektronik.

## 9. Kamera.java

### Deklarasi Interface Kamera

public interface Kamera {
    void ambilFoto();
}
Penjelasan:

- interface Kamera mendefinisikan kemampuan kamera.
- ambilFoto() merupakan method yang digunakan untuk mengambil foto.

Class yang mengimplementasikan interface ini harus menyediakan isi method ambilFoto().

## 10. Smartphone.java

### Implementasi Multiple Interface

public class Smartphone implements AlatElektronik, Kamera {
    private String merk;

    public Smartphone(String merk) {
        this.merk = merk;
    }

    @Override
    public void nyalakan() {
        System.out.println(merk + " menyala. Booting OS...");
    }

    @Override
    public void matikan() {
        System.out.println(merk + " dimatikan. Goodbye.");
    }

    @Override
    public void ambilFoto() {
        System.out.println(
            "Cekrek! Foto berhasil disimpan di galeri " + merk + "."
        );
    }
}
Penjelasan:

- implements AlatElektronik, Kamera menunjukkan bahwa Smartphone mengimplementasikan dua interface sekaligus.
- Atribut merk digunakan untuk menyimpan merek smartphone.
- Constructor Smartphone(String merk) mengisi nilai merek.
- Method nyalakan() menampilkan pesan ketika smartphone dinyalakan.
- Method matikan() menampilkan pesan ketika smartphone dimatikan.
- Method ambilFoto() menampilkan pesan bahwa foto berhasil disimpan.
- @Override menandai implementasi method yang berasal dari interface.
- Class ini menunjukkan bahwa satu class dapat menerapkan beberapa interface sekaligus.

## 11. TesSmartphone.java

### Pengujian Interface

public class TesSmartphone {
    public static void main(String[] args) {
        Smartphone hp = new Smartphone("Samsung");

        hp.nyalakan();
        hp.ambilFoto();
        hp.matikan();
    }
}
Penjelasan:

- Program membuat objek smartphone dengan merek Samsung.
- hp.nyalakan() menjalankan method untuk menyalakan smartphone.
- hp.ambilFoto() menjalankan fungsi kamera.
- hp.matikan() menjalankan method untuk mematikan smartphone.

Program ini menguji implementasi kedua interface melalui objek Smartphone.

## Cara Menjalankan Program

1. Buka proyek menggunakan NetBeans atau editor Java lainnya.
2. Pastikan seluruh file berada di dalam package praktikum8.pbo.
3. Pilih salah satu class yang memiliki method main().
4. Jalankan PoliTester untuk menguji polymorphism.
5. Jalankan TesBangunDatar untuk menguji abstract class.
6. Jalankan TesSmartphone untuk menguji interface.

## Kesimpulan

Praktikum ini membahas penerapan konsep Object-Oriented Programming dalam Java, yaitu inheritance, polymorphism, abstract class, dan interface. Inheritance memungkinkan class mewarisi atribut atau method dari class induk, sedangkan polymorphism memungkinkan method yang sama menghasilkan perilaku berbeda sesuai objeknya. Abstract class digunakan sebagai dasar bagi class turunan, sementara interface menetapkan method yang harus diimplementasikan. Pembagian class ke dalam package praktikum8.pbo membantu membuat struktur program lebih terorganisasi.
