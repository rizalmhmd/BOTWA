import java.time.LocalDate;

// Interface Mobil
interface Mobil {
 String getNomorPolisi();
 String getMerk();
}

// Abstract class
abstract class MobilAbstract implements Mobil {
 private String nomorPolisi;
 private String merk;

 public MobilAbstract(String nomorPolisi, String merk) {
 this.nomorPolisi = nomorPolisi;
 this.merk = merk;
 }

 @Override
 public String getNomorPolisi() {
 return nomorPolisi;
 }

 @Override
 public String getMerk() {
 return merk;
 }

 @Override
 public String toString() {
 return merk + " [" + nomorPolisi + "]";
 }
}

// Subclass
class MobilSedan extends MobilAbstract {
 public MobilSedan(String nomorPolisi, String merk) {
 super(nomorPolisi, merk);
 }
}

// Class Supir
class Supir {
 private String nip;
 private String nama;

 public Supir(String nip, String nama) {
 this.nip = nip;
 this.nama = nama;
 }

 public String getNip() {
 return nip;
 }

 public String getNama() {
 return nama;
 }

 @Override
 public String toString() {
 return nama + " (NIP: " + nip + ")";
 }
}

// Class Rental
class Rental {
 private Mobil mobil;
 private Supir supir;
 private LocalDate tanggalPinjam;
 private LocalDate tanggalKembali;

 public Rental(Mobil mobil, Supir supir, LocalDate tanggalPinjam, LocalDate tanggalKembali) {
 this.mobil = mobil;
 this.supir = supir;
 this.tanggalPinjam = tanggalPinjam;
 this.tanggalKembali = tanggalKembali;
 }

 public void tampilkanInfoRental() {
 System.out.println("===== Informasi Rental =====");
 System.out.println("Mobil : " + mobil);
 System.out.println("Supir : " + supir);
 System.out.println("Tanggal Pinjam : " + tanggalPinjam);
 System.out.println("Tanggal Kembali: " + tanggalKembali);
 }
}

// Main class
public class Main {
 public static void main(String[] args) {
 Mobil mobil = new MobilSedan("B 1234 ABC", "Toyota");
 Supir supir = new Supir("1234567890", "Budi");
 LocalDate tanggalPinjam = LocalDate.now();
 LocalDate tanggalKembali = tanggalPinjam.plusDays(3);

 Rental rental = new Rental(mobil, supir, tanggalPinjam, tanggalKembali);
 rental.tampilkanInfoRental(); // menampilkan hasil ke konsol
 }
}