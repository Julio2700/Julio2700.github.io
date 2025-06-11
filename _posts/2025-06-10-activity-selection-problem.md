---
title: ACTIVITY SELECTION PROBLEM
date: 2025-06-11 15:40:22 +0800
categories: [Desain dan Analisis Algoritma]
tags: [activity-selection-problem, greedy-algorithm, algoritma]
---

# Activity Selection Problem

Selamat datang. Apakah Anda pernah menghadapi permasalahan dalam menyusun jadwal karena adanya bentrok waktu antar kegiatan? Misalnya, ingin mengikuti acara A tetapi waktunya bersamaan dengan acara B. Permasalahan ini sering muncul dalam kehidupan nyata maupun dalam pengelolaan sumber daya secara digital. Dalam konteks algoritma, permasalahan ini dikenal sebagai **Activity Selection Problem (ASP)**.

Mari kita telaah secara mendalam.

## Definisi Activity Selection Problem

Secara sederhana, Activity Selection Problem merupakan permasalahan klasik dalam ilmu komputer yang bertujuan untuk memilih sebanyak mungkin kegiatan (aktivitas) dari sejumlah opsi yang tersedia, dengan ketentuan **tidak boleh ada dua aktivitas yang tumpang tindih dalam waktu pelaksanaannya**.

## Relevansi dalam Dunia Nyata

Permasalahan ini sering muncul dalam berbagai konteks seperti:

- **Penjadwalan Ruangan:** Mengatur penggunaan ruang di kampus atau kantor agar tidak terjadi benturan jadwal.
- **Wawancara Kerja:** HRD perlu menjadwalkan wawancara banyak kandidat dengan efisien.
- **Manajemen Sumber Daya:** Seperti penjadwalan mesin produksi atau slot waktu server.

## Batasan (Constraints)

Agar solusi valid, terdapat dua ketentuan utama:

1. Aktivitas berikutnya hanya dapat dimulai setelah aktivitas sebelumnya selesai (waktu mulai ≥ waktu selesai aktivitas sebelumnya).
2. Hanya satu aktivitas yang dapat dilakukan dalam satu waktu.

## Penyelesaian dengan Algoritma Greedy

ASP dapat diselesaikan secara efisien menggunakan pendekatan *greedy*, yakni membuat keputusan optimal pada setiap langkah lokal untuk mencapai solusi global yang optimal.

### Mengapa Greedy Cocok?

- **Optimalitas Lokal:** Memilih aktivitas yang selesai paling awal akan membuka lebih banyak waktu untuk aktivitas berikutnya.
- **Efisiensi Global:** Keputusan lokal terbaik pada setiap langkah membentuk solusi optimal keseluruhan.

## Strategi Penyelesaian

1. Urutkan aktivitas berdasarkan waktu selesai.
2. Pilih aktivitas pertama (yang selesai paling awal).
3. Dari sisa aktivitas, pilih yang waktu mulainya ≥ waktu selesai aktivitas terakhir yang dipilih.
4. Ulangi langkah 3 hingga tidak ada lagi aktivitas yang dapat dipilih.

## Contoh Soal

### Diberikan:

| Aktivitas | Waktu Mulai | Waktu Selesai |
|-----------|-------------|---------------|
| A         | 3           | 6             |
| B         | 1           | 4             |
| C         | 5           | 9             |
| D         | 8           | 10            |
| E         | 2           | 7             |

### Penyelesaian:

1. Urutkan berdasarkan waktu selesai:

| Aktivitas | Waktu Mulai | Waktu Selesai |
|-----------|-------------|---------------|
| B         | 1           | 4             |
| A         | 3           | 6             |
| E         | 2           | 7             |
| C         | 5           | 9             |
| D         | 8           | 10            |

2. Pilih B → selesai pada 4  
3. C dimulai pada 5 (≥4), pilih C → selesai pada 9

Solusi: **B, C**

## Implementasi C++

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Activity {
    int start;
    int finish;
};

bool compareActivities(Activity a, Activity b) {
    return (a.finish < b.finish);
}

void activitySelection(std::vector<Activity> activities, int n) {
    std::sort(activities.begin(), activities.end(), compareActivities);

    std::cout << "Aktivitas yang dipilih:\n";
    int i = 0;
    std::cout << "Aktivitas: (Start: " << activities[i].start 
              << ", Finish: " << activities[i].finish << ")\n";

    for (int j = 1; j < n; j++) {
        if (activities[j].start >= activities[i].finish) {
            std::cout << "Aktivitas: (Start: " << activities[j].start 
                      << ", Finish: " << activities[j].finish << ")\n";
            i = j;
        }
    }
}

int main() {
    std::vector<Activity> activities = {
        {1, 8}, {3, 4}, {0, 6}, {5, 9}, {5, 7}, {8, 9}
    };
    int n = activities.size();
    activitySelection(activities, n);
    return 0;
}
```

## Kompleksitas

- **Waktu:** O(n log n) — disebabkan proses pengurutan.
- **Ruang:** O(1) — hanya memerlukan sejumlah kecil variabel tambahan.

## Kesimpulan

Activity Selection Problem merupakan permasalahan optimasi yang umum dan signifikan. Dengan algoritma *greedy*, masalah ini dapat diselesaikan secara efisien dan sederhana. Solusinya berguna dalam konteks nyata seperti penjadwalan ruang, pengaturan tugas, dan pengelolaan sumber daya.

Selamat belajar dan semoga bermanfaat.
