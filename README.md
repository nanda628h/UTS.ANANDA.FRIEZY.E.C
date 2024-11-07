# Tugas UTS

1. Buatkan Struktur data untuk Program Kasir yang mempunyai fitur

a. Menambah barang ke dalam keranjang.

b. Menampilkan daftar barang.

c. Menghitung total harga.

d. Mencetak struk.

## kode program
``` python
class Kasir:
    def _init_(self):
        # Keranjang belanja: daftar barang (nama, harga, jumlah)
        self.keranjang = []

    def tambah_barang(self, nama, harga, jumlah):
        # Menambah barang ke dalam keranjang
        barang = {'nama': nama, 'harga': harga, 'jumlah': jumlah}
        self.keranjang.append(barang)
        print(f"{nama} telah ditambahkan ke keranjang.")

    def tampilkan_barang(self):
        # Menampilkan daftar barang yang ada di keranjang
        if not self.keranjang:
            print("Keranjang Anda kosong.")
        else:
            print("Daftar Barang di Keranjang:")
            for index, barang in enumerate(self.keranjang, start=1):
                print(f"{index}. {barang['nama']} - {barang['jumlah']} x {barang['harga']} IDR")

    def hitung_total(self):
        # Menghitung total harga dari barang yang ada di keranjang
        total = 0
        for barang in self.keranjang:
            total += barang['harga'] * barang['jumlah']
        return total

    def cetak_struk(self):
        # Mencetak struk belanja
        if not self.keranjang:
            print("Keranjang Anda kosong, tidak ada struk untuk dicetak.")
            return
        print("\n----- STRUK PEMBELIAN -----")
        for barang in self.keranjang:
            subtotal = barang['harga'] * barang['jumlah']
            print(f"{barang['nama']} - {barang['jumlah']} x {barang['harga']} = {subtotal} IDR")
        total = self.hitung_total()
        print(f"\nTotal Harga: {total} IDR")
        print("---------------------------")
        print("Terima kasih atas belanja Anda!")

# Main Program
def main():
    kasir = Kasir()

    while True:
        print("\nMenu Kasir:")
        print("1. Tambah Barang")
        print("2. Tampilkan Daftar Barang")
        print("3. Hitung Total Harga")
        print("4. Cetak Struk")
        print("5. Keluar")
        
        pilihan = input("Pilih menu (1-5): ")

        if pilihan == '1':
            nama_barang = input("Masukkan nama barang: ")
            harga_barang = float(input("Masukkan harga barang: "))
            jumlah_barang = int(input("Masukkan jumlah barang: "))
            kasir.tambah_barang(nama_barang, harga_barang, jumlah_barang)
        
        elif pilihan == '2':
            kasir.tampilkan_barang()
        
        elif pilihan == '3':
            total = kasir.hitung_total()
            print(f"Total harga barang di keranjang: {total} IDR")
        
        elif pilihan == '4':
            kasir.cetak_struk()
        
        elif pilihan == '5':
            print("Terima kasih! Program kasir telah selesai.")
            break
        
        else:
            print("Pilihan tidak valid, silakan coba lagi.")

if _name_ == "_main_":
    main()
```
## Penjelasan

1. Class Kasir
Class ini bertujuan untuk menangani proses transaksi sederhana dengan menggunakan metode untuk menambahkan barang, menampilkan daftar barang, menghitung total harga, dan mencetak struk belanja.

__init__: Metode ini adalah konstruktor yang digunakan untuk menginisialisasi atribut keranjang, yang merupakan list kosong untuk menyimpan barang-barang yang akan ditambahkan ke dalam keranjang belanja.

tambah_barang(self, nama, harga, jumlah): Metode ini menambahkan barang ke dalam keranjang. Barang yang ditambahkan berupa dictionary yang berisi nama, harga, dan jumlah. Barang ini kemudian disimpan dalam list keranjang. Metode ini juga mencetak pesan bahwa barang telah berhasil ditambahkan.

tampilkan_barang(self): Metode ini menampilkan seluruh barang yang ada di dalam keranjang beserta informasi jumlah dan harga per item. Jika keranjang kosong, program akan mencetak pesan bahwa keranjang kosong.

hitung_total(self): Metode ini mengembalikan total harga semua barang di dalam keranjang. Total harga dihitung dengan mengalikan harga per item dengan jumlahnya, lalu menambahkannya ke dalam total keseluruhan.

cetak_struk(self): Metode ini mencetak struk belanja yang menampilkan rincian setiap barang (nama barang, jumlah, harga per item, dan subtotal), serta total harga keseluruhan. Jika keranjang kosong, metode ini mencetak pesan bahwa keranjang kosong dan tidak ada struk untuk dicetak.

2. Program Utama (main)
Fungsi main() berfungsi sebagai antarmuka utama untuk berinteraksi dengan pengguna. Berikut langkah-langkah yang terjadi di dalam fungsi ini:

Instansiasi Objek Kasir: Membuat objek kasir dari class Kasir.

Menu Utama: Program menampilkan menu utama dengan beberapa pilihan untuk pengguna, yaitu:

Tambah Barang
Tampilkan Daftar Barang
Hitung Total Harga
Cetak Struk
Keluar
Input Pilihan Menu: Pengguna diminta memilih opsi dengan menginput angka 1 hingga 5. Setiap pilihan akan menjalankan metode yang sesuai dari objek kasir:

Pilihan 1: Pengguna akan diminta memasukkan nama, harga, dan jumlah barang, kemudian memanggil tambah_barang() untuk menambahkan barang ke keranjang.
Pilihan 2: Memanggil tampilkan_barang() untuk menampilkan daftar barang di keranjang.
Pilihan 3: Memanggil hitung_total() untuk menghitung dan menampilkan total harga seluruh barang di keranjang.
Pilihan 4: Memanggil cetak_struk() untuk mencetak struk belanja.
Pilihan 5: Menghentikan program dengan menampilkan pesan perpisahan dan keluar dari loop.
