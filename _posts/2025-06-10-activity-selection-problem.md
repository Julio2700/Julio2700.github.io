---
title: Activity Selection Problem
description: Activity Selection Problem mengajarkan cara memilih aktivitas sebanyak mungkin tanpa bentrok waktu, menggunakan strategi greedy sederhana = selalu pilih yang paling cepat selesai.
date: 2025-06-10 10:39:00 +0800
categories: [Desain dan Analisis Algoritma]
tags: [Algorithm Problems]
---

# Headings

Activity Selection Problem merupakan masalah optimasi klasik dalam ilmu
komputer. Kita diberikan sejumlah aktivitas yang masing-masing didefinisikan
dengan waktu mulai (s) dan waktu selesai (f). Dua aktivitas dikatakan
kompatibel jika mereka tidak tumpang tindih secara waktu, artinya salah satu
aktivitas selesai sebelum aktivitas lainnya dimulai. Tantangannya adalah
menentukan subset terbesar dari aktivitas yang semuanya kompatibel satu
sama lain.

### Activity Selection Problem:
- Masalah pemilihan aktivitas maksimum yang tidak saling tumpang tindih
- Diberikan sekumpulan aktivitas dengan waktu mulai dan waktu selesai
- Tujuan: Memilih jumlah aktivitas maksimum yang dapat dilakukan oleh satu orang/resource

# Konsep Dasar Algoritma Greedy

Algoritma greedy adalah strategi pemecahan masalah optimasi yang
bekerja dengan membuat pilihan yang tampak paling baik pada setiap
langkah, dengan harapan rangkaian pilihan ini akan mengarah pada
solusi yang optimal secara keseluruhan. Algoritma ini bersifat "serakah"
karena langsung mengambil pilihan terbaik saat itu tanpa
mempertimbangkan konsekuensi di masa depan.