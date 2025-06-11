---
title: SUBSET SUM PROBLEM
date: 2025-06-11 13:14:00 +0800
categories: [Desain dan Analisis Algoritma]
tags: [greedy, dynamic programming, np-complete, subset sum]
---

# Subset Sum Problem

Dokumen ini membahas **Subset Sum Problem (SSP)**, yaitu permasalahan klasik dalam ilmu komputer yang bertujuan menentukan apakah terdapat subset dari suatu himpunan bilangan bulat yang jumlahnya sama dengan nilai target tertentu.

---

## Definisi

Diberikan sebuah himpunan bilangan bulat dan nilai target, Subset Sum Problem bertujuan mencari apakah terdapat subset dari bilangan tersebut yang jumlah elemennya sama dengan nilai target.

Contoh:
- Himpunan: {3, 34, 4, 12, 5, 2}
- Target: 9
- Solusi: Ya, karena terdapat subset {4, 5} yang jumlahnya 9.

---

## Relevansi

SSP memiliki berbagai aplikasi nyata, antara lain:

- **Kriptografi:** Digunakan dalam skema kriptografi berbasis subset sum.
- **Manajemen Anggaran:** Untuk memilih kombinasi elemen yang sesuai dengan total tertentu.
- **Genetika dan AI:** Digunakan dalam pencocokan pola dan pengambilan keputusan.
- **Manajemen Proyek:** Menentukan subset tugas yang sesuai dengan batas anggaran atau sumber daya.

---

## Klasifikasi Kompleksitas

SSP termasuk dalam kelas masalah **NP-Complete**:
- Solusi dapat diverifikasi dalam waktu polinomial.
- Tidak ada algoritma yang diketahui dapat menyelesaikannya dalam waktu polinomial untuk semua kasus.

---

## Pendekatan Penyelesaian

### 1. Brute Force
Memeriksa semua kemungkinan subset. Kompleksitas waktu: O(2ⁿ). Cocok hanya untuk data kecil.

### 2. Rekursif
Pendekatan rekursif memecah masalah menjadi submasalah yang lebih kecil. Namun, tetap memiliki kompleksitas eksponensial.

### 3. Dynamic Programming (DP)
Pendekatan paling efisien secara praktis:
- Kompleksitas waktu: O(n × sum)
- Kompleksitas memori: O(n × sum)

---

## Contoh Tabel DP

Untuk himpunan {1, 2, 3} dan target 3, DP Table adalah:

```
  j→  0   1   2   3
i↓
0    T   F   F   F
1    T   T   F   F
2    T   T   T   T
3    T   T   T   T
```

---

## Variasi Masalah

- **Bounded SSP:** Setiap elemen hanya dapat digunakan satu kali.
- **Unbounded SSP:** Elemen dapat digunakan lebih dari satu kali.
- **Exact k Elements:** Hanya subset dengan k elemen yang valid.
- **Partition Problem:** Memeriksa apakah himpunan dapat dibagi menjadi dua subset dengan jumlah yang sama.
- **Multi-target Constraints:** Melibatkan dua atau lebih batasan seperti total nilai dan berat.
- **Approximate SSP:** Mencari subset dengan jumlah mendekati nilai target.

---

## Implementasi C++

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool isSubsetSum(const vector<int>& arr, int n, int sum) {
    vector<vector<bool>> dp(n+1, vector<bool>(sum+1, false));
    for (int i = 0; i <= n; i++) dp[i][0] = true;

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= sum; j++) {
            if (arr[i-1] > j)
                dp[i][j] = dp[i-1][j];
            else
                dp[i][j] = dp[i-1][j] || dp[i-1][j - arr[i-1]];
        }
    }

    return dp[n][sum];
}

int main() {
    vector<int> arr = {3, 34, 4, 12, 5, 2};
    int sum = 9;

    if (isSubsetSum(arr, arr.size(), sum))
        cout << "Subset ditemukan!\n";
    else
        cout << "Tidak ada subset yang sesuai.\n";

    return 0;
}
```

---

## Kompleksitas Algoritma

| Pendekatan            | Kompleksitas Waktu | Kompleksitas Memori |
|-----------------------|--------------------|----------------------|
| Rekursif              | O(2ⁿ)              | O(n)                 |
| Dynamic Programming   | O(n × sum)         | O(n × sum)           |
| DP - Optimasi Memori  | O(n × sum)         | O(sum)               |

---

## Kesimpulan

Subset Sum Problem merupakan salah satu permasalahan kombinatorial penting dengan banyak penerapan praktis. Meskipun termasuk dalam kategori NP-Complete, pendekatan seperti dynamic programming memungkinkan penyelesaian yang efisien untuk ukuran input yang moderat.

