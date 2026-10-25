
# Praktikum Pemrograman Berorientasi Objek (PBO)

# Polimorfisme, Abstract, dan Interface

## Struktur Folder

```text
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
```

## Identitas

Nama: Firli Syawala

NIM: L0325025

## Package

Package yang digunakan dalam program ini adalah `praktikum8.pbo`. Package berfungsi untuk mengelompokkan class agar program lebih terstruktur dan mudah dikelola.

Untuk membuat package di NetBeans, klik kanan pada bagian Source Packages, pilih New > Java Package, kemudian masukkan nama `praktikum8.pbo`.

Deklarasi package yang ditambahkan pada setiap file Java adalah sebagai berikut.

```java
package praktikum8.pbo;
```

Pastikan seluruh file Java berada di dalam package tersebut agar struktur folder dan deklarasi package sesuai.

## 1. Hewan.java

### Deklarasi Class dan Method

```java
public class Hewan {
    public void bersuara() {
        System.out.println("Hewan ini mengeluarkan suara yang tidak spesifik.");
    }
}
```

### Penjelasan Kode

- `public class Hewan` merupakan deklarasi class bernama Hewan yang menjadi class induk.
- `public void bersuara()` merupakan method untuk menampilkan suara hewan.
- `System.out.println()` digunakan untuk menampilkan teks ke layar.

Class Hewan menjadi dasar pewarisan bagi class Kucing dan Anjing.

## 2. Kucing.java

### Penerapan Inheritance

```java
public class Kucing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Kucing: Mew meow!");
    }
}
```

### Penjelasan Kode

- `extends Hewan` menunjukkan bahwa class Kucing mewarisi class Hewan.
- `@Override` menandakan bahwa method `bersuara()` ditulis ulang dari class induk.
- `System.out.println()` menampilkan suara khas kucing.

Class Kucing menerapkan inheritance atau pewarisan dan method overriding sehingga memiliki perilaku suara yang berbeda dari class induknya.

## 3. Anjing.java

### Penerapan Inheritance

```java
public class Anjing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Anjing: Guk guk");
    }
}
```

### Penjelasan Kode

- `extends Hewan` menunjukkan bahwa class Anjing merupakan turunan dari class Hewan.
- `@Override` digunakan untuk menandai penulisan ulang method `bersuara()`.
- `System.out.println()` menampilkan suara khas anjing.

Class Anjing memiliki method yang sama dengan class Hewan, tetapi menghasilkan keluaran yang berbeda.

## 4. PoliTester.java

### Pengujian Polymorphism

```java
public class PoliTester {
    public static void main(String[] args) {
        //Deklarasi array dari tipe Superclass, tetapi diisi dengan objek Subclass
        Hewan[] daftarHewan = new Hewan[3];
        daftarHewan[0] = new Hewan();
        daftarHewan[1] = new Kucing(); //Upcasting
        daftarHewan[2] = new Anjing(); //Upcasting
        
        //Polimorfisme: Pemanggilan method yang sama menghasilkan output berbeda
        for (Hewan h : daftarHewan) {
            h.bersuara();
        }
    }
}
```

### Penjelasan Kode

- `main()` merupakan method utama yang pertama kali dijalankan oleh program.
- `Hewan[] daftarHewan = new Hewan[3]` membuat array yang dapat menampung tiga objek bertipe Hewan.
- `new Hewan()`, `new Kucing()`, dan `new Anjing()` membuat objek dari masing-masing class.
- Upcasting terjadi ketika objek Kucing dan Anjing disimpan dalam variabel bertipe Hewan.
- Perulangan `for-each` digunakan untuk mengakses setiap objek dalam array.
- `h.bersuara()` memanggil method yang sesuai dengan jenis objek.

Program ini menerapkan polymorphism karena pemanggilan method yang sama menghasilkan keluaran berbeda sesuai dengan objeknya.

### Hasil Program

```text
Hewan ini mengeluarkan suara yang tidak spesifik.
Kucing: Mew meow!
Anjing: Guk guk
```

## 5. BangunDatar.java

### Penerapan Abstract Class

```java
public abstract class BangunDatar {
    String warna;
    
    public BangunDatar(String warna) {
        this.warna = warna;
    }
    
    //Abstract method: Tidak memiliki isi, wajib di-override subclass
    public abstract double hitungLuas();
    
    //Concrete method: Punya isi, bisa langsung dipakai
    public void cetakWarna() {
        System.out.println("Warna bangun ini adalah: " + warna);
    }
}
```

### Penjelasan Kode

- `abstract class BangunDatar` mendefinisikan class abstrak yang menjadi dasar bagi class turunannya.
- Atribut `warna` digunakan untuk menyimpan warna bangun datar.
- Constructor `BangunDatar(String warna)` digunakan untuk mengisi nilai warna.
- `this.warna = warna` menyimpan nilai parameter ke dalam atribut objek.
- `public abstract double hitungLuas()` merupakan method abstrak yang harus diimplementasikan oleh class turunannya.
- `cetakWarna()` merupakan method konkret yang digunakan untuk menampilkan warna bangun datar.

Class abstrak tidak dapat dibuat menjadi objek secara langsung, tetapi dapat diwarisi oleh class lain.

## 6. Lingkaran.java

### Implementasi Abstract Class

```java
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
```

### Penjelasan Kode

- `extends BangunDatar` menunjukkan bahwa Lingkaran merupakan turunan dari class BangunDatar.
- `private double jariJari` digunakan untuk menyimpan panjang jari-jari lingkaran.
- Constructor menerima parameter warna dan jari-jari.
- `super(warna)` memanggil constructor class induk untuk mengisi atribut warna.
- `this.jariJari = jariJari` menyimpan nilai jari-jari ke dalam atribut objek.
- `@Override` menandakan bahwa method `hitungLuas()` mengimplementasikan method abstrak dari class induk.
- `Math.PI * jariJari * jariJari` digunakan untuk menghitung luas lingkaran dengan rumus π × r × r.

Class Lingkaran menunjukkan penerapan abstract class melalui implementasi method yang sebelumnya hanya dideklarasikan pada class BangunDatar.

## 7. TesBangunDatar.java

### Pengujian Abstract Class

```java
public class TesBangunDatar {
    public static void main(String[] args) {
        Lingkaran lingkaran = new Lingkaran("Merah", 5);

        lingkaran.cetakWarna();
        System.out.println("Luas lingkaran: " + lingkaran.hitungLuas());
    }
}
```

### Penjelasan Kode

- `main()` merupakan method utama untuk menjalankan program.
- `new Lingkaran("Merah", 5)` membuat objek lingkaran berwarna merah dengan jari-jari 5.
- `lingkaran.cetakWarna()` menampilkan warna lingkaran.
- `lingkaran.hitungLuas()` memanggil method untuk menghitung luas lingkaran.
- Hasil perhitungan luas lingkaran ditampilkan menggunakan `System.out.println()`.

### Hasil Program

```text
Warna bangun ini adalah: Merah
Luas lingkaran: 78.53981633974483
```

## 8. AlatElektronik.java

### Deklarasi Interface

```java
public interface AlatElektronik {
    void nyalakan();
    void matikan();
}
```

### Penjelasan Kode

- `interface AlatElektronik` mendefinisikan sekumpulan method yang harus diimplementasikan oleh class yang menggunakan interface tersebut.
- `nyalakan()` merupakan method untuk menyalakan perangkat elektronik.
- `matikan()` merupakan method untuk mematikan perangkat elektronik.

Interface ini berfungsi sebagai pedoman bagi class yang menerapkan fungsi dasar perangkat elektronik.

## 9. Kamera.java

### Deklarasi Interface Kamera

```java
public interface Kamera {
    void ambilFoto();
}
```

### Penjelasan Kode

- `interface Kamera` mendefinisikan kemampuan yang berkaitan dengan fungsi kamera.
- `ambilFoto()` merupakan method untuk mengambil foto.

Class yang mengimplementasikan interface Kamera wajib menyediakan implementasi method `ambilFoto()`.

## 10. Smartphone.java

### Implementasi Multiple Interface

```java
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
        System.out.println("Cekrek! Foto berhasil disimpan di galeri " + merk + ".");
    }
}
```

### Penjelasan Kode

- `implements AlatElektronik, Kamera` menunjukkan bahwa class Smartphone mengimplementasikan dua interface sekaligus.
- `private String merk` merupakan atribut untuk menyimpan merek smartphone.
- Constructor `Smartphone(String merk)` digunakan untuk memberikan nilai merek pada objek.
- `nyalakan()` menampilkan pesan ketika smartphone dinyalakan.
- `matikan()` menampilkan pesan ketika smartphone dimatikan.
- `ambilFoto()` menampilkan pesan bahwa foto berhasil disimpan di galeri.
- `@Override` menandakan implementasi method yang berasal dari interface.

Class Smartphone menerapkan interface untuk menyediakan beberapa kemampuan dalam satu class.

## 11. TesSmartphone.java

### Pengujian Interface

```java
public class TesSmartphone {
    public static void main(String[] args) {
        Smartphone hp = new Smartphone("Samsung");

        hp.nyalakan();
        hp.ambilFoto();
        hp.matikan();
    }
}
```

### Penjelasan Kode

- `main()` merupakan method utama untuk menjalankan program.
- `new Smartphone("Samsung")` membuat objek smartphone dengan merek Samsung.
- `hp.nyalakan()` memanggil method untuk menyalakan smartphone.
- `hp.ambilFoto()` memanggil method untuk mengambil foto.
- `hp.matikan()` memanggil method untuk mematikan smartphone.

Program ini menguji fungsi-fungsi yang telah diimplementasikan dari interface AlatElektronik dan Kamera.

### Hasil Program

```text
Samsung menyala. Booting OS...
Cekrek! Foto berhasil disimpan di galeri Samsung.
Samsung dimatikan. Goodbye.
```

