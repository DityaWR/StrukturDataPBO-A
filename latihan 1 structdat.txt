#include <iostream>
#include <vector>
#include <string>

struct Data {
    std::string nama;
    int umur;
    std::string alamat;
};

std::vector<Data> database;

void tampilkanData() {
    if (database.empty()) {
        std::cout << "Database kosong." << std::endl;
        return;
    }

    for (const auto& entry : database) {
        std::cout << "Nama: " << entry.nama << ", Umur: " << entry.umur << ", Alamat: " << entry.alamat << std::endl;
    }
}

void tambahData() {
    Data baru;
    std::cout << "Masukkan Nama: ";
    std::cin >> baru.nama;
    std::cout << "Masukkan Umur: ";
    std::cin >> baru.umur;
    std::cout << "Masukkan Alamat: ";
    std::cin >> baru.alamat;
    

    database.push_back(baru);
    std::cout << "Data berhasil ditambahkan." << std::endl;
}

void hapusData() {
    if (database.empty()) {
        std::cout << "Database kosong." << std::endl;
        return;
    }

    int index;
    std::cout << "Masukkan indeks data yang ingin dihapus: ";
    std::cin >> index;

    if (index >= 0 && index < database.size()) {
        database.erase(database.begin() + index);
        std::cout << "Data berhasil dihapus." << std::endl;
    } else {
        std::cout << "Indeks tidak valid." << std::endl;
    }
}

void ubahData() {
    if (database.empty()) {
        std::cout << "Database kosong." << std::endl;
        return;
    }

    int index;
    std::cout << "Masukkan indeks data yang ingin diubah: ";
    std::cin >> index;

    if (index >= 0 && index < database.size()) {
        Data& target = database[index];
        std::cout << "Nama (" << target.nama << "): ";
        std::cin >> target.nama;
        std::cout << "Umur (" << target.umur << "): ";
        std::cin >> target.umur;
        std::cout << "Alamat (" << target.alamat << "): ";
        std::cin >> target.alamat;

        std::cout << "Data berhasil diubah." << std::endl;
    } else {
        std::cout << "Indeks tidak valid." << std::endl;
    }
}

void cariData() {
    if (database.empty()) {
        std::cout << "Database kosong." << std::endl;
        return;
    }

    std::string namaCari;
    std::cout << "Masukkan nama yang ingin dicari: ";
    std::cin >> namaCari;

    bool ditemukan = false;

    for (const auto& entry : database) {
        if (entry.nama == namaCari) {
            std::cout << "Nama: " << entry.nama << ", Umur: " << entry.umur << ", Alamat: " << entry.alamat << std::endl;
            ditemukan = true;
        }
    }

    if (!ditemukan) {
        std::cout << "Data tidak ditemukan." << std::endl;
    }
}

int main() {
    while (true) {
        std::cout << "\nMenu:\n";
        std::cout << "1. Tampilkan Data\n";
        std::cout << "2. Tambah Data\n";
        std::cout << "3. Hapus Data\n";
        std::cout << "4. Ubah Data\n";
        std::cout << "5. Cari Data\n";
        std::cout << "6. Keluar\n";
        std::cout << "Pilihan Anda: ";

        int pilihan;
        std::cin >> pilihan;

        switch (pilihan) {
            case 1:
                tampilkanData();
                break;
            case 2:
                tambahData();
                break;
            case 3:
                hapusData();
                break;
            case 4:
                ubahData();
                break;
            case 5:
                cariData();
                break;
            case 6:
                return 0;
            default:
                std::cout << "Pilihan tidak valid. Silakan coba lagi." << std::endl;
        }
    }

    return 0;
}
