# Kisi-Kisi & Ringkasan Materi UAS — Calculus
**MATH 6031 / MATH 6135031 · Computer Science Department · Bina Nusantara University**

> Dokumen ini disusun berdasarkan diktat resmi MATH 6031, soal latihan tutorial, dan pola soal Tugas Besar 2 (2025/2026). Materi dibagi sesuai kisi-kisi UAS: teknik integrasi, aplikasi integral, kekonvergenan deret, serta deret Maclaurin dan Taylor.

---

## Daftar Isi

1. [Teknik-Teknik Integral](#1-teknik-teknik-integral)
   - 1.1 Strategi Pemilihan Teknik (Flowchart)
   - 1.2 Substitusi Sederhana
   - 1.3 Integral Parsial (Integration by Parts)
   - 1.4 Integral Trigonometri
   - 1.5 Substitusi Trigonometri
   - 1.6 Pecahan Parsial (Partial Fractions)
2. [Aplikasi Integral](#2-aplikasi-integral)
   - 2.1 Luas Daerah (Area)
   - 2.2 Panjang Kurva (Arc Length)
   - 2.3 Volume Benda Putar
3. [Kekonvergenan Deret Tak Hingga](#3-kekonvergenan-deret-tak-hingga)
   - 3.1 Konsep Dasar Deret
   - 3.2 Uji Kedivergenan (Divergence Test)
   - 3.3 Uji Deret-p (p-Series Test)
   - 3.4 Uji Integral (Integral Test)
   - 3.5 Uji Perbandingan Langsung (Direct Comparison Test)
   - 3.6 Uji Banding Limit (Limit Comparison Test)
   - 3.7 Uji Leibniz / Deret Ganti Tanda (Alternating Series Test)
   - 3.8 Uji Rasio (Ratio Test)
   - 3.9 Uji Akar (Root Test)
   - 3.10 Konvergensi Mutlak vs. Bersyarat
   - 3.11 Strategi Pemilihan Uji
4. [Deret Maclaurin dan Taylor](#4-deret-maclaurin-dan-taylor)
   - 4.1 Deret Taylor
   - 4.2 Deret Maclaurin
   - 4.3 Daftar Deret Maclaurin Penting
5. [Tabel Rumus Referensi Cepat](#5-tabel-rumus-referensi-cepat)
6. [Prediksi Pola Soal UAS](#6-prediksi-pola-soal-uas)

---

## 1. Teknik-Teknik Integral

### 1.1 Strategi Pemilihan Teknik

Sebelum menggunakan teknik yang rumit, selalu periksa urutan berikut:

| Langkah | Periksa | Tindakan |
|---------|---------|----------|
| 1 | Bisa disederhanakan secara aljabar? | Faktorkan, bagi, manipulasi dahulu |
| 2 | Ada u = g(x) sehingga g′(x) muncul di integran? | **Substitusi sederhana** |
| 3 | Integran berbentuk P(x)/Q(x)? | **Pecahan parsial** |
| 4 | Ada √(a²−x²), √(a²+x²), atau √(x²−a²)? | **Substitusi trigonometri** |
| 5 | Ada pangkat sin/cos/tan/sec? | **Integral trigonometri** |
| 6 | Perkalian dua jenis fungsi berbeda (L·I·A·T·E)? | **Integral parsial** |
| 7 | Belum berhasil | Manipulasi khusus, sekawan, identitas |

---

### 1.2 Substitusi Sederhana

**Ide pokok:** Jika turunan dari satu bagian integran muncul di bagian lain (sampai konstanta), gunakan substitusi u = g(x).

**Rumus:**
$$\int f(g(x))\, g'(x)\, dx = \int f(u)\, du, \quad u = g(x)$$

#### Contoh Khas yang Sering Muncul

**Contoh 1 — Pembilang adalah turunan penyebut:**
$$\int \frac{\cos x}{2 + \sin x}\, dx$$

Misal $u = 2 + \sin x$, maka $du = \cos x\, dx$.
$$= \int \frac{du}{u} = \ln|u| + C = \ln(2 + \sin x) + C$$

**Contoh 2 — Eksponensial:**
$$\int \frac{e^{2x}}{1 + e^{2x}}\, dx$$

Misal $u = 1 + e^{2x}$, $du = 2e^{2x}\, dx$, sehingga $e^{2x}\, dx = \frac{du}{2}$.
$$= \frac{1}{2}\int \frac{du}{u} = \frac{1}{2}\ln(1 + e^{2x}) + C$$

**Contoh 3 — Substitusi akar:**
$$\int \frac{\sin\sqrt{1-x}}{\sqrt{1-x}}\, dx$$

Misal $u = \sqrt{1-x}$, maka $u^2 = 1-x$, $2u\, du = -dx$.
$$= \int \frac{\sin u}{u} \cdot (-2u)\, du = -2\int \sin u\, du = 2\cos u + C = 2\cos\sqrt{1-x} + C$$

**Contoh 4 — Substitusi untuk bentuk komposit:**
$$\int \frac{\sin(4x-1)}{1 - \sin^2(4x-1)}\, dx$$

Perhatikan $1 - \sin^2\theta = \cos^2\theta$, sehingga $\frac{\sin\theta}{\cos^2\theta} = \tan\theta\sec\theta$.
$$= \int \frac{\sin(4x-1)}{\cos^2(4x-1)}\, dx = \int \tan(4x-1)\sec(4x-1)\, dx$$
Misal $u = 4x-1$, $du = 4\, dx$:
$$= \frac{1}{4}\sec(4x-1) + C$$

---

### 1.3 Integral Parsial (Integration by Parts)

**Rumus Kunci:**
$$\boxed{\int u\, dv = uv - \int v\, du}$$

Untuk integral tentu:
$$\int_a^b u\, dv = \Big[uv\Big]_a^b - \int_a^b v\, du$$

#### Aturan LIATE — Cara Memilih u

Pilih u dari fungsi yang **paling atas** dalam urutan berikut:

| Huruf | Kelas | Contoh | Alasan |
|-------|-------|--------|--------|
| **L** | Logaritma | $\ln x$, $\ln(x^2+1)$ | Sulit diintegralkan, mudah diturunkan |
| **I** | Invers Trigonometri | $\arctan x$, $\arcsin x$ | Sama seperti L |
| **A** | Aljabar (polinomial) | $x^2$, $3x+1$ | Derajat turun setiap diturunkan |
| **T** | Trigonometri | $\sin x$, $\cos x$ | Mudah diintegralkan → jadi dv |
| **E** | Eksponensial | $e^x$, $2^x$ | Mudah diintegralkan → jadi dv |

> **Cek validitas:** Setelah memilih u dan dv, pastikan $\int v\, du$ **lebih mudah** dari $\int u\, dv$.

#### Tipe 1: Polinomial × Eksponensial

$$\int x e^x\, dx: \quad u = x,\ dv = e^x dx \Rightarrow du = dx,\ v = e^x$$
$$= xe^x - \int e^x\, dx = xe^x - e^x + C = e^x(x-1) + C$$

Jika polinomial berderajat $n$, parsial dilakukan **n kali**.

$$\int x^2 e^x\, dx = e^x(x^2 - 2x + 2) + C$$

Koefisien tidak satuan:
$$\int (2x+1)e^{3x}\, dx = \frac{(6x+1)e^{3x}}{9} + C$$

#### Tipe 2: Polinomial × Trigonometri

$$\int x \sin x\, dx: \quad u = x,\ dv = \sin x\, dx \Rightarrow du = dx,\ v = -\cos x$$
$$= -x\cos x + \int \cos x\, dx = \sin x - x\cos x + C$$

Derajat dua (parsial dua kali):
$$\int x^2 \cos x\, dx = (x^2-2)\sin x + 2x\cos x + C$$

#### Tipe 3: Logaritma (Fungsi Tunggal)

Trik: gunakan $dv = dx$ sehingga $v = x$.

$$\int \ln x\, dx: \quad u = \ln x,\ dv = dx \Rightarrow du = \frac{1}{x}dx,\ v = x$$
$$= x\ln x - \int x \cdot \frac{1}{x}\, dx = x\ln x - x + C$$

Bentuk $x^n \ln x$:
$$\int x \ln x\, dx = \frac{x^2}{4}(2\ln x - 1) + C$$
$$\int \sqrt{x}\ln x\, dx = \int x^{1/2}\ln x\, dx: \quad u = \ln x,\ dv = x^{1/2}dx \Rightarrow v = \frac{2}{3}x^{3/2}$$
$$= \frac{2}{3}x^{3/2}\ln x - \int \frac{2}{3}x^{3/2} \cdot \frac{1}{x}\, dx = \frac{2}{3}x^{3/2}\ln x - \frac{4}{9}x^{3/2} + C = \frac{2x^{3/2}}{9}(3\ln x - 2) + C$$

$$\int \frac{\ln x}{x^2}\, dx: \quad u = \ln x,\ dv = x^{-2}dx \Rightarrow du = \frac{1}{x}dx,\ v = -\frac{1}{x}$$
$$= -\frac{\ln x}{x} + \int \frac{1}{x^2}\, dx = -\frac{\ln x}{x} - \frac{1}{x} + C = -\frac{1+\ln x}{x} + C$$

#### Tipe 4: Invers Trigonometri

$$\int \arctan x\, dx: \quad u = \arctan x,\ dv = dx \Rightarrow du = \frac{1}{1+x^2}dx,\ v = x$$
$$= x\arctan x - \int \frac{x}{1+x^2}\, dx = x\arctan x - \frac{1}{2}\ln(1+x^2) + C$$

#### Tipe 5: Eksponensial × Trigonometri (Kasus Siklik)

Misalkan $I = \int e^x \sin x\, dx$.

**Parsial 1:** $u = \sin x,\ dv = e^x dx$:
$$I = e^x\sin x - \int e^x\cos x\, dx$$

**Parsial 2** (konsisten, $u = \cos x$): $\int e^x\cos x\, dx = e^x\cos x + I$

Substitusi balik:
$$I = e^x\sin x - (e^x\cos x + I) \Rightarrow 2I = e^x(\sin x - \cos x)$$

$$\boxed{\int e^x \sin x\, dx = \frac{e^x}{2}(\sin x - \cos x) + C}$$

**Rumus Umum (worth memorizing):**
$$\int e^{ax}\sin(bx)\, dx = \frac{e^{ax}(a\sin bx - b\cos bx)}{a^2+b^2} + C$$
$$\int e^{ax}\cos(bx)\, dx = \frac{e^{ax}(a\cos bx + b\sin bx)}{a^2+b^2} + C$$

Untuk $\int_0^\pi \cos x \sinh x\, dx$: gunakan parsial siklik dengan $\sinh x$ dan $\cos x$, atau manfaatkan bahwa $\int e^x\cos x\, dx$ muncul dalam bentuk eksponensial setelah $\sinh x = \frac{e^x - e^{-x}}{2}$.

#### Integral Tentu dengan Parsial — Contoh Penting

$$\int_0^1 xe^x\, dx = \Big[xe^x - e^x\Big]_0^1 = (e-e)-(0-1) = 1$$

$$\int_0^\pi e^x\sin x\, dx = \Big[\frac{e^x(\sin x - \cos x)}{2}\Big]_0^\pi = \frac{e^\pi+1}{2}$$

$$\int_0^{\pi/2} \cos^5\theta\, d\theta: \text{ pangkat sinus/kosinus (lihat 1.4)}$$

---

### 1.4 Integral Trigonometri

#### A. Bentuk $\int \sin^m x \cos^n x\, dx$

| Kondisi | Strategi | Substitusi |
|---------|----------|-----------|
| $n$ ganjil ($n = 2k+1$) | Sisihkan satu $\cos x$, ubah sisa $\cos^{2k}x = (1-\sin^2 x)^k$ | $u = \sin x$ |
| $m$ ganjil ($m = 2k+1$) | Sisihkan satu $\sin x$, ubah sisa $\sin^{2k}x = (1-\cos^2 x)^k$ | $u = \cos x$ |
| Keduanya genap | Gunakan identitas sudut paruh: $\sin^2 x = \frac{1-\cos 2x}{2}$, $\cos^2 x = \frac{1+\cos 2x}{2}$ | — |

**Contoh 1 — Pangkat kosinus ganjil:**
$$\int \cos^5\theta\, d\theta = \int (1-\sin^2\theta)^2\cos\theta\, d\theta, \quad u = \sin\theta$$
$$= \int (1-u^2)^2\, du = \int (1 - 2u^2 + u^4)\, du = u - \frac{2u^3}{3} + \frac{u^5}{5} + C$$
$$= \sin\theta - \frac{2\sin^3\theta}{3} + \frac{\sin^5\theta}{5} + C$$

Evaluasi $\int_0^{\pi/2}\cos^5\theta\, d\theta = \Big[\sin\theta - \frac{2\sin^3\theta}{3} + \frac{\sin^5\theta}{5}\Big]_0^{\pi/2} = 1 - \frac{2}{3} + \frac{1}{5} = \frac{8}{15}$

**Contoh 2 — Pangkat sinus ganjil:**
$$\int \sin^5 4x \cos^2 4x\, dx$$

Misal $t = 4x$, $dt = 4\, dx$. Pangkat sinus ganjil ($m=5$), sisihkan satu $\sin t$:
$$= \frac{1}{4}\int \sin^5 t\cos^2 t\, dt = \frac{1}{4}\int (1-\cos^2 t)^2 \cos^2 t \sin t\, dt$$
Misal $u = \cos t$, $du = -\sin t\, dt$:
$$= -\frac{1}{4}\int (1-u^2)^2 u^2\, du = -\frac{1}{4}\int (u^2 - 2u^4 + u^6)\, du$$
$$= -\frac{1}{4}\left(\frac{\cos^3 4x}{3} - \frac{2\cos^5 4x}{5} + \frac{\cos^7 4x}{7}\right) + C$$

**Contoh 3 — Keduanya genap ($\sin^4 x$):**
$$\sin^4 x = \left(\frac{1-\cos 2x}{2}\right)^2 = \frac{3}{8} - \frac{1}{2}\cos 2x + \frac{1}{8}\cos 4x$$
$$\int \sin^4 x\, dx = \frac{3x}{8} - \frac{\sin 2x}{4} + \frac{\sin 4x}{32} + C$$

**Integral tentu penting:**
$$\int_0^{\pi/2}\cos^5\theta\, d\theta = \frac{8}{15}$$
$$\int_0^{\pi/4}\sin^2 x\cos^2 x\, dx = \frac{\pi}{32}$$

#### B. Bentuk $\int \tan^m x \sec^n x\, dx$

| Kondisi | Strategi | Substitusi |
|---------|----------|-----------|
| $n$ genap ($n = 2k$, $k \geq 2$) | Sisihkan $\sec^2 x$, ubah sisa $\sec^{2(k-1)}x = (1+\tan^2 x)^{k-1}$ | $u = \tan x$ |
| $m$ ganjil | Sisihkan $\sec x\tan x$, ubah $\tan^{2k}x = (\sec^2 x - 1)^k$ | $u = \sec x$ |

**Contoh klasik $\int \sec^3 x\, dx$ (parsial + identitas + siklik):**

Misal $I = \int \sec^3 x\, dx$. Pecah $\sec x \cdot \sec^2 x$, lalu $u = \sec x$, $dv = \sec^2 x\, dx$:
$$I = \sec x\tan x - \int \sec x\tan^2 x\, dx = \sec x\tan x - \int \sec x(\sec^2 x - 1)\, dx$$
$$I = \sec x\tan x - I + \ln|\sec x + \tan x|$$
$$\boxed{\int \sec^3 x\, dx = \frac{1}{2}\left(\sec x\tan x + \ln|\sec x+\tan x|\right) + C}$$

#### C. Identitas Penting yang Sering Digunakan

| Identitas | Bentuk |
|-----------|--------|
| Pythagoras | $\sin^2 x + \cos^2 x = 1$ |
| Pythagoras (sec) | $1 + \tan^2 x = \sec^2 x$ |
| Pythagoras (csc) | $1 + \cot^2 x = \csc^2 x$ |
| Sudut paruh sin | $\sin^2 x = \frac{1-\cos 2x}{2}$ |
| Sudut paruh cos | $\cos^2 x = \frac{1+\cos 2x}{2}$ |
| Sudut ganda | $\sin 2x = 2\sin x\cos x$ |
| Perkalian | $\sin x\cos x = \frac{1}{2}\sin 2x$ |

---

### 1.5 Substitusi Trigonometri

Digunakan ketika integran mengandung bentuk akar: $\sqrt{a^2-x^2}$, $\sqrt{a^2+x^2}$, atau $\sqrt{x^2-a^2}$.

#### Tabel Referensi Substitusi

| Bentuk Akar | Substitusi | Identitas yang Digunakan | Domain $\theta$ |
|-------------|-----------|--------------------------|-----------------|
| $\sqrt{a^2 - x^2}$ | $x = a\sin\theta$ | $1 - \sin^2\theta = \cos^2\theta$ | $-\frac{\pi}{2} \leq \theta \leq \frac{\pi}{2}$ |
| $\sqrt{a^2 + x^2}$ | $x = a\tan\theta$ | $1 + \tan^2\theta = \sec^2\theta$ | $-\frac{\pi}{2} < \theta < \frac{\pi}{2}$ |
| $\sqrt{x^2 - a^2}$ | $x = a\sec\theta$ | $\sec^2\theta - 1 = \tan^2\theta$ | $0 \leq \theta < \frac{\pi}{2}$ |

#### Cara Menggunakan Segitiga Referensi

Setelah substitusi, hasilnya dalam $\theta$. Untuk konversi kembali ke $x$, bangun segitiga siku-siku:

- **$x = a\sin\theta$:** sisi miring $= a$, sisi depan $= x$, sisi samping $= \sqrt{a^2-x^2}$
- **$x = a\tan\theta$:** sisi samping $= a$, sisi depan $= x$, sisi miring $= \sqrt{a^2+x^2}$
- **$x = a\sec\theta$:** sisi samping $= a$, sisi miring $= x$, sisi depan $= \sqrt{x^2-a^2}$

#### Contoh 1 — Bentuk $\sqrt{a^2+x^2}$:

$$\int \frac{1}{\sqrt{9+x^2}}\, dx$$

Gunakan $x = 3\tan\theta$, $dx = 3\sec^2\theta\, d\theta$, $\sqrt{9+x^2} = 3\sec\theta$.
$$= \int \frac{3\sec^2\theta}{3\sec\theta}\, d\theta = \int \sec\theta\, d\theta = \ln|\sec\theta + \tan\theta| + C$$

Dari segitiga: $\tan\theta = x/3$, $\sec\theta = \sqrt{9+x^2}/3$.
$$= \ln\left|\frac{\sqrt{9+x^2}}{3} + \frac{x}{3}\right| + C = \ln\left|\sqrt{9+x^2} + x\right| + C'$$

#### Contoh 2 — Bentuk $\sqrt{a^2-x^2}$:

$$\int \frac{\sqrt{4-x^2}}{x}\, dx$$

Gunakan $x = 2\sin\theta$, $dx = 2\cos\theta\, d\theta$, $\sqrt{4-x^2} = 2\cos\theta$.
$$= \int \frac{2\cos\theta}{2\sin\theta} \cdot 2\cos\theta\, d\theta = 2\int \frac{\cos^2\theta}{\sin\theta}\, d\theta = 2\int \frac{1-\sin^2\theta}{\sin\theta}\, d\theta$$
$$= 2\int (\csc\theta - \sin\theta)\, d\theta = 2\ln|\csc\theta - \cot\theta| + 2\cos\theta + C$$

Konversi balik: $\sin\theta = x/2$, $\cos\theta = \sqrt{4-x^2}/2$, $\cot\theta = \sqrt{4-x^2}/x$:
$$= \sqrt{4-x^2} - 2\arcsin\frac{x}{2} + C$$
(atau bentuk setara dengan $\ln$)

#### Contoh 3 — Bentuk $\sqrt{x^2-a^2}$:

$$\int \frac{x^2}{\sqrt{x^2-4}}\, dx$$

Gunakan $x = 2\sec\theta$, $dx = 2\sec\theta\tan\theta\, d\theta$, $\sqrt{x^2-4} = 2\tan\theta$.
$$= \int \frac{4\sec^2\theta}{2\tan\theta} \cdot 2\sec\theta\tan\theta\, d\theta = 4\int \sec^3\theta\, d\theta$$
$$= 4 \cdot \frac{1}{2}(\sec\theta\tan\theta + \ln|\sec\theta+\tan\theta|) + C$$

Konversi balik ($\sec\theta = x/2$, $\tan\theta = \sqrt{x^2-4}/2$):
$$= \frac{x\sqrt{x^2-4}}{2} + 2\ln\left|x + \sqrt{x^2-4}\right| + C$$

#### Contoh 4 — Integral tentu dengan substitusi trigonometri:

$$\int_3^{3\sqrt{2}} \frac{\sqrt{x^2-9}}{x}\, dx$$

Gunakan $x = 3\sec\theta$. Ubah batas: $x=3 \Rightarrow \theta=0$, $x=3\sqrt{2} \Rightarrow \theta=\pi/4$.
$$= \int_0^{\pi/4} \frac{3\tan\theta}{3\sec\theta}\cdot 3\sec\theta\tan\theta\, d\theta = 3\int_0^{\pi/4}\tan^2\theta\, d\theta = 3\Big[\tan\theta - \theta\Big]_0^{\pi/4} = 3\left(1-\frac{\pi}{4}\right)$$

---

### 1.6 Pecahan Parsial (Partial Fractions)

Digunakan untuk integran berbentuk fungsi rasional $\frac{P(x)}{Q(x)}$.

**Prasyarat:** Derajat $P(x)$ < derajat $Q(x)$. Jika tidak, lakukan **pembagian polinomial (long division)** dulu.

#### Kasus 1: Faktor Linear Berbeda

$$\frac{P(x)}{(a_1x+b_1)(a_2x+b_2)\cdots} = \frac{A_1}{a_1x+b_1} + \frac{A_2}{a_2x+b_2} + \cdots$$

**Contoh:**
$$\int \frac{5x-1}{x^2-x-2}\, dx = \int \frac{5x-1}{(x-2)(x+1)}\, dx$$

Faktorkan: $5x-1 = A(x+1) + B(x-2)$.
- $x=2$: $9 = 3A \Rightarrow A=3$
- $x=-1$: $-6 = -3B \Rightarrow B=2$

$$= 3\ln|x-2| + 2\ln|x+1| + C$$

#### Kasus 2: Faktor Linear Berulang

Jika Q(x) memuat $(ax+b)^r$, kontribusinya:
$$\frac{A_1}{ax+b} + \frac{A_2}{(ax+b)^2} + \cdots + \frac{A_r}{(ax+b)^r}$$

**Contoh:**
$$\int \frac{2x^2+3x+7}{(x-1)(x+1)^2}\, dx = \int \left(\frac{-1}{x+1} + \frac{-3}{(x+1)^2} + \frac{3}{x-1}\right)\, dx$$
$$= -\ln|x+1| + \frac{3}{x+1} + 3\ln|x-1| + C$$

#### Kasus 3: Faktor Kuadrat Tak Tereduksi

Jika $Q(x)$ memuat $ax^2+bx+c$ dengan $b^2-4ac < 0$:
$$\frac{Ax+B}{ax^2+bx+c}$$

Integrasi sering butuh melengkapkan kuadrat sempurna:

**Contoh:**
$$\int \frac{x}{x^2+2x+5}\, dx, \quad x^2+2x+5 = (x+1)^2+4$$

Misal $u = x+1$:
$$= \int \frac{u-1}{u^2+4}\, du = \frac{1}{2}\ln(u^2+4) - \frac{1}{2}\arctan\frac{u}{2} + C = \frac{1}{2}\ln(x^2+2x+5) - \frac{1}{2}\arctan\frac{x+1}{2} + C$$

#### Kasus 4: Faktor Kuadrat Tak Tereduksi Berulang

Kontribusi $(ax^2+bx+c)^r$:
$$\frac{A_1x+B_1}{ax^2+bx+c} + \frac{A_2x+B_2}{(ax^2+bx+c)^2} + \cdots + \frac{A_rx+B_r}{(ax^2+bx+c)^r}$$

---

## 2. Aplikasi Integral

### 2.1 Luas Daerah (Area)

#### Integrasi terhadap x

Jika $f(x) \geq g(x)$ pada $[a, b]$:
$$A = \int_a^b \left[f(x) - g(x)\right]\, dx$$

**Langkah Pengerjaan:**
1. Sketsa kurva
2. Cari titik potong (set $f(x) = g(x)$, selesaikan)
3. Tentukan mana yang di atas ($f$) dan di bawah ($g$) pada interval
4. Hitung integral

**Contoh 1 — Luas antara $y = 4x$ dan $y = x^2$:**

Titik potong: $x^2 = 4x \Rightarrow x(x-4) = 0 \Rightarrow x = 0, 4$.
Pada $[0,4]$: $4x \geq x^2$.
$$A = \int_0^4 (4x - x^2)\, dx = \left[2x^2 - \frac{x^3}{3}\right]_0^4 = 32 - \frac{64}{3} = \frac{32}{3}$$

**Contoh 2 — Daerah antara $4y^2 - 2x = 0$ dan $4y^2 + 4x - 12 = 0$:**

Dari kurva pertama: $x = 2y^2$. Dari kurva kedua: $x = 3 - y^2$.
Titik potong: $2y^2 = 3 - y^2 \Rightarrow 3y^2 = 3 \Rightarrow y = \pm 1$.
Integrasi terhadap $y$ (lebih mudah):
$$A = \int_{-1}^{1}\left[(3-y^2) - 2y^2\right]\, dy = \int_{-1}^{1}(3-3y^2)\, dy = \left[3y - y^3\right]_{-1}^{1} = (3-1) - (-3+1) = 4$$

**Contoh 3 — Daerah antara $x = 4y^4$ dan $x = 8 - 4y^4$:**

Titik potong: $4y^4 = 8 - 4y^4 \Rightarrow 8y^4 = 8 \Rightarrow y = \pm 1$.
$$A = \int_{-1}^{1}\left[(8-4y^4) - 4y^4\right]\, dy = \int_{-1}^{1}(8 - 8y^4)\, dy = \left[8y - \frac{8y^5}{5}\right]_{-1}^{1} = \frac{64}{5}$$

#### Integrasi terhadap y

Jika batas kurva lebih mudah dinyatakan sebagai $x = f(y)$:
$$A = \int_c^d \left[f_{\text{kanan}}(y) - f_{\text{kiri}}(y)\right]\, dy$$

**Contoh — Luas daerah antara $y = \sqrt{x}$ dan $y = x$:**

Titik potong: $\sqrt{x} = x \Rightarrow x = 0, 1$.
$$A = \int_0^1 (\sqrt{x} - x)\, dx = \left[\frac{2}{3}x^{3/2} - \frac{x^2}{2}\right]_0^1 = \frac{2}{3} - \frac{1}{2} = \frac{1}{6}$$

---

### 2.2 Panjang Kurva (Arc Length)

$$L = \int_a^b \sqrt{1 + \left(\frac{dy}{dx}\right)^2}\, dx$$

**Contoh — Panjang kurva $y = x\sqrt{x} = x^{3/2}$ dari $x=1$ ke $x=4$:**

$\frac{dy}{dx} = \frac{3}{2}x^{1/2}$, sehingga $\left(\frac{dy}{dx}\right)^2 = \frac{9x}{4}$.

$$L = \int_1^4 \sqrt{1 + \frac{9x}{4}}\, dx$$

Misal $u = 1 + \frac{9x}{4}$, $du = \frac{9}{4}dx$, $dx = \frac{4}{9}du$.
Batas: $x=1 \Rightarrow u=\frac{13}{4}$, $x=4 \Rightarrow u=10$.
$$L = \frac{4}{9}\int_{13/4}^{10} u^{1/2}\, du = \frac{4}{9}\cdot\frac{2}{3}\left[u^{3/2}\right]_{13/4}^{10} = \frac{8}{27}\left[10^{3/2} - \left(\frac{13}{4}\right)^{3/2}\right]$$

---

### 2.3 Volume Benda Putar

#### Metode Cakram (Disk Method) — Putar terhadap sumbu-x

$$V = \pi\int_a^b \left[f(x)\right]^2\, dx$$

**Contoh 1 — $y = x^2$ dari $x=0$ ke $x=2$, diputar terhadap sumbu-x:**
$$V = \pi\int_0^2 (x^2)^2\, dx = \pi\int_0^2 x^4\, dx = \pi\left[\frac{x^5}{5}\right]_0^2 = \frac{32\pi}{5}$$

**Contoh 2 — $y = x\sqrt{x}$ dari $x=1$ ke $x=4$, diputar terhadap sumbu-x:**
$$V = \pi\int_1^4 (x^{3/2})^2\, dx = \pi\int_1^4 x^3\, dx = \pi\left[\frac{x^4}{4}\right]_1^4 = \pi\left(64 - \frac{1}{4}\right) = \frac{255\pi}{4}$$

#### Metode Cincin (Washer Method) — Dua Kurva

$$V = \pi\int_a^b \left[R(x)^2 - r(x)^2\right]\, dx$$

di mana $R(x)$ = jari-jari luar, $r(x)$ = jari-jari dalam.

**Contoh 1 — Daerah antara $y=x$ dan $y=x^2$ ($0 \leq x \leq 1$), diputar terhadap sumbu-x:**

$R(x) = x$ (luar), $r(x) = x^2$ (dalam).
$$V = \pi\int_0^1(x^2 - x^4)\, dx = \pi\left[\frac{x^3}{3} - \frac{x^5}{5}\right]_0^1 = \pi\left(\frac{1}{3}-\frac{1}{5}\right) = \frac{2\pi}{15}$$

**Contoh 2 — Daerah $y = x\sqrt{x}$, $x=1$ ke $x=4$, $y=0$, diputar terhadap $y=-1$:**

Jari-jari luar: $R(x) = f(x) - (-1) = x^{3/2} + 1$, jari-jari dalam: $r(x) = 0 - (-1) = 1$.
$$V = \pi\int_1^4\left[(x^{3/2}+1)^2 - 1^2\right]\, dx = \pi\int_1^4(x^3 + 2x^{3/2})\, dx$$
$$= \pi\left[\frac{x^4}{4} + \frac{4x^{5/2}}{5}\right]_1^4 = \pi\left[\left(64 + \frac{128}{5}\right) - \left(\frac{1}{4} + \frac{4}{5}\right)\right]$$

**Contoh 3 — Putar terhadap sumbu-y (integrasi terhadap y):**

Daerah $x = 2\sqrt{y}$, $y=0$ ke $y=4$, $x=0$, diputar terhadap sumbu-y.
$$V = \pi\int_0^4 (2\sqrt{y})^2\, dy = \pi\int_0^4 4y\, dy = \pi\left[2y^2\right]_0^4 = 32\pi$$

**Contoh 4 — Daerah $x = 2/y$, $y=2$ ke $y=6$, $x=0$, diputar terhadap sumbu-y:**

$$V = \pi\int_2^6 \left(\frac{2}{y}\right)^2\, dy = 4\pi\int_2^6 \frac{dy}{y^2} = 4\pi\left[-\frac{1}{y}\right]_2^6 = 4\pi\left(-\frac{1}{6}+\frac{1}{2}\right) = \frac{4\pi}{3}$$

#### Metode Cangkang (Shell Method) — Alternatif

$$V = 2\pi\int_a^b x\cdot f(x)\, dx \quad \text{(putar terhadap sumbu-y)}$$

#### Luas Permukaan Kurva $y = x\sqrt{x}$ (Soal 2a dari Tugas Besar 2)

Ringkasan semua bagian soal 2a untuk $y = x^{3/2}$, $x \in [1,4]$, $y=0$:

| Bagian | Formula | Nilai |
|--------|---------|-------|
| i. Luas R | $\int_1^4 x^{3/2}\, dx$ | $\frac{2}{5}[x^{5/2}]_1^4 = \frac{2}{5}(32-1) = \frac{62}{5}$ |
| ii. Panjang kurva | $\int_1^4 \sqrt{1+\frac{9x}{4}}\, dx$ | Lihat 2.2 |
| iii. Volume (sbx) | $\pi\int_1^4 x^3\, dx$ | $\frac{255\pi}{4}$ |
| iv. Volume (y=-1) | $\pi\int_1^4[(x^{3/2}+1)^2-1]\, dx$ | Lihat di atas |

---

## 3. Kekonvergenan Deret Tak Hingga

### 3.1 Konsep Dasar Deret

**Deret tak hingga:**
$$\sum_{n=1}^{\infty} a_n = a_1 + a_2 + a_3 + \cdots$$

**Jumlah parsial ke-n:** $S_n = \sum_{k=1}^n a_k$

**Konvergen** jika $\lim_{n\to\infty} S_n = S$ (berhingga). **Divergen** jika tidak.

> **Peringatan penting:** $\lim a_n = 0$ adalah syarat perlu, BUKAN syarat cukup untuk konvergensi.
> Contoh: $\sum \frac{1}{n}$ divergen meskipun $\frac{1}{n} \to 0$.

**Deret Geometri (wajib hafal):**
$$\sum_{n=1}^{\infty} ar^{n-1} = \frac{a}{1-r} \quad \text{jika } |r| < 1; \quad \text{divergen jika } |r| \geq 1$$

**Deret Teleskopis:**
$$\sum_{n=1}^{\infty} \frac{1}{n(n+1)} = \sum_{n=1}^{\infty}\left(\frac{1}{n} - \frac{1}{n+1}\right) = 1$$

---

### 3.2 Uji Kedivergenan (Divergence Test / n-th Term Test)

$$\text{Jika } \lim_{n\to\infty} a_n \neq 0 \text{ atau tidak ada} \Rightarrow \sum a_n \text{ divergen}$$

> **Perhatian:** Hanya bisa membuktikan **divergensi**. Jika $\lim a_n = 0$, uji ini **tidak conclusive**.

**Kapan dipakai:** Sebagai **cek pertama** untuk setiap deret. Murah dan cepat.

**Contoh dari soal:**

$$\sum_{n=1}^{\infty} \frac{n!}{n^{100}}: \quad \lim \frac{n!}{n^{100}} = \infty \neq 0 \Rightarrow \textbf{Divergen}$$

$$\sum_{n=1}^{\infty} \frac{n^3}{(2n)!}: \quad \text{gunakan Uji Rasio (faktorial lebih cocok)}$$

---

### 3.3 Uji Deret-p (p-Series Test)

$$\sum_{n=1}^{\infty} \frac{1}{n^p} \begin{cases} \text{konvergen} & \text{jika } p > 1 \\ \text{divergen} & \text{jika } p \leq 1 \end{cases}$$

**Kasus khusus penting:**
- $p=1$: deret harmonik $\sum \frac{1}{n}$, **divergen**
- $p=2$: $\sum \frac{1}{n^2}$, **konvergen**
- $p=1/2$: $\sum \frac{1}{\sqrt{n}}$, **divergen**

**Kapan dipakai:** Langsung jika berbentuk persis $\frac{1}{n^p}$. Juga berguna sebagai pembanding di Uji Banding.

---

### 3.4 Uji Integral (Integral Test)

Jika $f(x)$ kontinu, positif, dan **menurun** pada $[1,\infty)$ dengan $a_n = f(n)$:
$$\sum_{n=1}^{\infty} a_n \text{ dan } \int_1^{\infty} f(x)\, dx \quad \text{keduanya konvergen atau keduanya divergen}$$

> Nilai integral tidak sama dengan jumlah deret.

**Kapan dipakai:** $a_n = f(n)$ dengan $f$ mudah diintegralkan, positif, dan menurun.

**Contoh:**

$$\sum_{n=1}^{\infty} \frac{1}{n^2+1}: \quad \int_1^{\infty}\frac{dx}{x^2+1} = \arctan x\Big|_1^{\infty} = \frac{\pi}{2} - \frac{\pi}{4} = \frac{\pi}{4} < \infty \Rightarrow \textbf{Konvergen}$$

$$\sum_{n=2}^{\infty}\frac{1}{n\ln n}: \quad \int_2^{\infty}\frac{dx}{x\ln x} = \Big[\ln\ln x\Big]_2^{\infty} = \infty \Rightarrow \textbf{Divergen}$$

Berguna juga untuk membuktikan **Uji Deret-p** secara formal.

---

### 3.5 Uji Perbandingan Langsung (Direct Comparison Test)

Untuk deret dengan suku-suku **positif**:
- Jika $a_n \leq b_n$ dan $\sum b_n$ konvergen $\Rightarrow \sum a_n$ **konvergen**
- Jika $a_n \geq b_n$ dan $\sum b_n$ divergen $\Rightarrow \sum a_n$ **divergen**

**Strategi memilih pembanding:** Lihat suku dominan.

**Contoh:**
$$\sum_{n=1}^{\infty}\frac{1}{n^2+5}: \quad \frac{1}{n^2+5} \leq \frac{1}{n^2}, \quad \sum\frac{1}{n^2} \text{ konvergen} \Rightarrow \textbf{Konvergen}$$

$$\sum_{n=3}^{\infty}\frac{n}{n^2-5}: \quad \frac{n}{n^2-5} \geq \frac{n}{n^2} = \frac{1}{n}, \quad \sum\frac{1}{n} \text{ divergen} \Rightarrow \textbf{Divergen}$$

---

### 3.6 Uji Banding Limit (Limit Comparison Test)

Jika $a_n, b_n > 0$ dan:
$$\lim_{n\to\infty}\frac{a_n}{b_n} = c \in (0, \infty)$$
maka $\sum a_n$ dan $\sum b_n$ **keduanya konvergen atau keduanya divergen**.

**Cara cepat memilih $b_n$:** Ambil rasio pangkat dominan dari $a_n$.

| $a_n$ | Pangkat dominan | Pilih $b_n$ |
|-------|-----------------|-------------|
| $\frac{3n-2}{n^3-2n^2+11}$ | $\frac{n}{n^3} = \frac{1}{n^2}$ | $\frac{1}{n^2}$ |
| $\frac{1}{\sqrt{n^2+1}}$ | $\frac{1}{\sqrt{n^2}} = \frac{1}{n}$ | $\frac{1}{n}$ |
| $\frac{n^2+1}{n^4+5}$ | $\frac{n^2}{n^4} = \frac{1}{n^2}$ | $\frac{1}{n^2}$ |

**Kapan dipakai:** Lebih fleksibel dari Direct Comparison. Cocok untuk fungsi rasional/aljabar.

**Contoh dari soal — $\sum \frac{\ln n}{n^2}$:**

Bandingkan dengan $b_n = \frac{1}{n^{3/2}}$ (p-series, $p = 3/2 > 1$, konvergen):
$$\lim_{n\to\infty}\frac{\ln n / n^2}{1/n^{3/2}} = \lim_{n\to\infty}\frac{\ln n}{n^{1/2}} \stackrel{L'H}{=} \lim_{n\to\infty}\frac{1/n}{1/(2\sqrt{n})} = \lim_{n\to\infty}\frac{2}{\sqrt{n}} = 0$$

Karena $c = 0$ dan $\sum b_n$ konvergen, maka $\sum a_n$ juga **konvergen**.

> Catatan: jika $c = 0$ dan $\sum b_n$ konvergen, maka $\sum a_n$ konvergen. Jika $c = \infty$ dan $\sum b_n$ divergen, maka $\sum a_n$ divergen. Kasus $c \in (0,\infty)$ bersifat ekuivalen.

---

### 3.7 Uji Leibniz / Deret Ganti Tanda (Alternating Series Test)

Deret ganti tanda:
$$\sum_{n=1}^{\infty} (-1)^{n-1} b_n = b_1 - b_2 + b_3 - b_4 + \cdots, \quad b_n > 0$$

**Konvergen** jika kedua syarat terpenuhi:
1. $b_n$ **menurun**: $b_{n+1} \leq b_n$ untuk semua $n$
2. $\lim_{n\to\infty} b_n = 0$

**Kapan dipakai:** Deret dengan faktor $(-1)^n$ atau $(-1)^{n+1}$.

**Contoh:**

$$\sum_{n=1}^{\infty}(-1)^{n+1}\frac{n}{n^2+1}: \quad b_n = \frac{n}{n^2+1}$$

Cek menurun: $b'(x) = \frac{(1-x^2)}{(x^2+1)^2} < 0$ untuk $x > 1$. ✓

Cek limit: $\lim \frac{n}{n^2+1} = 0$. ✓

Deret **konvergen** (oleh Leibniz). Cek konvergensi mutlak: $\sum \frac{n}{n^2+1} \sim \sum \frac{1}{n}$ divergen → **konvergen bersyarat**.

---

### 3.8 Uji Rasio (Ratio Test)

$$L = \lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|$$

| $L$ | Kesimpulan |
|-----|------------|
| $L < 1$ | Konvergen mutlak |
| $L > 1$ atau $L = \infty$ | Divergen |
| $L = 1$ | **Uji gagal**, perlu uji lain |

**Kapan dipakai:** Deret mengandung **faktorial** ($n!$) atau **pangkat tetap** ($r^n$), atau kombinasinya.

**Jangan dipakai untuk:** Fungsi rasional murni dari $n$ (akan selalu $L=1$, gagal).

**Contoh 1 — Faktorial:**
$$\sum_{n=1}^{\infty}\frac{2^n}{n!}: \quad \frac{a_{n+1}}{a_n} = \frac{2^{n+1}/(n+1)!}{2^n/n!} = \frac{2}{n+1} \to 0 < 1 \Rightarrow \textbf{Konvergen mutlak}$$

**Contoh 2 — Faktorial divergen:**
$$\sum_{n=1}^{\infty}\frac{n!}{n^{100}}: \quad \frac{a_{n+1}}{a_n} = \frac{(n+1)!/(n+1)^{100}}{n!/n^{100}} = (n+1)\cdot\left(\frac{n}{n+1}\right)^{100} \to \infty \Rightarrow \textbf{Divergen}$$

**Contoh 3 — Deret Taylor:**
$$\sum_{n=1}^{\infty}\frac{n^3}{(2n)!}: \quad \frac{a_{n+1}}{a_n} = \frac{(n+1)^3}{(2n+2)!}\cdot\frac{(2n)!}{n^3} = \left(\frac{n+1}{n}\right)^3 \cdot \frac{1}{(2n+2)(2n+1)} \to 0 \Rightarrow \textbf{Konvergen}$$

**Contoh 4 — Campuran:**
$$\sum_{n=1}^{\infty}k^2 e^{-k^3} = \sum k^2 \cdot \frac{1}{e^{k^3}}$$

Coba Uji Integral: $f(x) = x^2 e^{-x^3}$, misal $u = x^3$:
$$\int_1^{\infty}x^2 e^{-x^3}\, dx = \frac{1}{3}\int_1^{\infty}e^{-u}\, du = \frac{e^{-1}}{3} < \infty \Rightarrow \textbf{Konvergen}$$

$$\sum_{k=1}^{\infty} ke^{-3k^2}: \quad f(x) = xe^{-3x^2}, \quad \int_1^{\infty}xe^{-3x^2}\, dx = \frac{1}{6}e^{-3} < \infty \Rightarrow \textbf{Konvergen}$$

---

### 3.9 Uji Akar (Root Test)

$$L = \lim_{n\to\infty}\sqrt[n]{|a_n|}$$

Kesimpulan sama dengan Uji Rasio ($L < 1$ konvergen, $L > 1$ divergen, $L=1$ gagal).

**Kapan dipakai:** Seluruh $a_n$ berbentuk $(b_n)^n$.

**Contoh:**
$$\sum_{n=1}^{\infty}\left(\frac{n}{2n+1}\right)^n: \quad \sqrt[n]{a_n} = \frac{n}{2n+1} \to \frac{1}{2} < 1 \Rightarrow \textbf{Konvergen}$$

---

### 3.10 Konvergensi Mutlak vs. Bersyarat

| Istilah | Definisi |
|---------|----------|
| **Konvergen Mutlak** | $\sum|a_n|$ konvergen |
| **Konvergen Bersyarat** | $\sum a_n$ konvergen tetapi $\sum|a_n|$ divergen |
| **Divergen** | $\sum a_n$ divergen |

**Teorema:** Konvergen mutlak $\Rightarrow$ Konvergen. (Tidak berlaku sebaliknya.)

**Strategi Praktis (3 langkah):**
1. Periksa $\sum|a_n|$ dengan uji yang sesuai
2. Jika $\sum|a_n|$ konvergen → **konvergen mutlak**
3. Jika $\sum|a_n|$ divergen, periksa $\sum a_n$ (biasanya Uji Leibniz):
   - Konvergen → **konvergen bersyarat**
   - Divergen → **divergen**

**Contoh dari soal:**

$$\sum_{n=1}^{\infty}(-1)^{n+1}\frac{n^4}{2^n}$$

Uji $\sum \frac{n^4}{2^n}$ dengan Rasio: $\frac{a_{n+1}}{a_n} = \frac{(n+1)^4}{2^{n+1}} \cdot \frac{2^n}{n^4} = \frac{(n+1)^4}{2n^4} \to \frac{1}{2} < 1$ → **konvergen mutlak**.

$$\sum_{n=1}^{\infty}(-1)^{n+1}\frac{n^2}{e^n}$$

Uji $\sum \frac{n^2}{e^n}$ dengan Rasio: $\frac{(n+1)^2/e^{n+1}}{n^2/e^n} = \frac{(n+1)^2}{en^2} \to \frac{1}{e} < 1$ → **konvergen mutlak**.

$$\sum_{n=1}^{\infty}(-1)^{n+1}\frac{1}{\sqrt{n^2-1}}$$

Uji $\sum \frac{1}{\sqrt{n^2-1}} \approx \sum \frac{1}{n}$ (divergen). Uji Leibniz: $b_n = \frac{1}{\sqrt{n^2-1}}$ menurun ke 0 ✓ → **konvergen bersyarat**.

---

### 3.11 Strategi Pemilihan Uji

```
Deret Σaₙ
│
├─ lim aₙ ≠ 0? ─────────────────────────── DIVERGEN (Uji Kedivergenan)
│
├─ Berbentuk 1/nᵖ? ─────────────────────── Uji Deret-p
│
├─ Berbentuk arⁿ? ──────────────────────── Deret Geometri
│
├─ Fungsi rasional / aljabar? ───────────── Uji Banding Limit (vs deret-p)
│
├─ Ada (-1)ⁿ? ──────────────────────────── Uji Leibniz + cek mutlak
│
├─ Ada faktorial atau rⁿ? ───────────────── Uji Rasio
│
├─ Berbentuk (bₙ)ⁿ? ────────────────────── Uji Akar
│
└─ f(n) positif, menurun, integral mudah? ─ Uji Integral
```

#### Rangkuman Kapan Pakai Uji Apa

| Uji | Paling Cocok Untuk | Hindari Jika |
|-----|-------------------|--------------|
| Kedivergenan | Cek pertama selalu | Tidak untuk konvergensi |
| Deret-p | Bentuk persis $1/n^p$ | Pembilang ≠ 1 atau penyebut ≠ $n^p$ murni |
| Banding Limit | Rasional/aljabar | Ada $(-1)^n$ (modifikasi diperlukan) |
| Leibniz | Deret $(-1)^n b_n$, $b_n > 0$ menurun ke 0 | Bukan deret ganti tanda |
| Rasio | Faktorial, $r^n$, kombinasinya | Fungsi rasional murni (L=1) |
| Akar | Seluruh suku berbentuk $(b_n)^n$ | — |
| Integral | f kontinu, positif, menurun, integral elementer | Faktorial, deret ganti tanda |

---

## 4. Deret Maclaurin dan Taylor

### 4.1 Deret Taylor

Ekspansi $f(x)$ di sekitar titik $x = a$:
$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \frac{f'''(a)}{3!}(x-a)^3 + \cdots$$

**Langkah Pengerjaan:**
1. Tentukan $f(a), f'(a), f''(a), f'''(a), \ldots$ sampai orde yang diminta
2. Susun dalam rumus deret Taylor
3. Tuliskan suku-suku eksplisit

#### Contoh 1 — $f(x) = \sqrt{x}$ di sekitar $a = 2$, sampai orde ke-3:

| Turunan | Rumus | Nilai di $x=2$ |
|---------|-------|----------------|
| $f(x)$ | $x^{1/2}$ | $\sqrt{2}$ |
| $f'(x)$ | $\frac{1}{2}x^{-1/2}$ | $\frac{1}{2\sqrt{2}}$ |
| $f''(x)$ | $-\frac{1}{4}x^{-3/2}$ | $-\frac{1}{4\cdot 2\sqrt{2}} = -\frac{1}{8\sqrt{2}}$ |
| $f'''(x)$ | $\frac{3}{8}x^{-5/2}$ | $\frac{3}{8\cdot 4\sqrt{2}} = \frac{3}{32\sqrt{2}}$ |

$$\sqrt{x} = \sqrt{2} + \frac{1}{2\sqrt{2}}(x-2) - \frac{1}{8\sqrt{2}}\cdot\frac{(x-2)^2}{2!} + \frac{3}{32\sqrt{2}}\cdot\frac{(x-2)^3}{3!} + \cdots$$

$$= \sqrt{2} + \frac{(x-2)}{2\sqrt{2}} - \frac{(x-2)^2}{16\sqrt{2}} + \frac{(x-2)^3}{64\sqrt{2}} + \cdots$$

#### Contoh 2 — $f(x) = \cot^{-1} x$ di sekitar $a = 1$, sampai orde ke-3:

| Turunan | Rumus | Nilai di $x=1$ |
|---------|-------|----------------|
| $f(x)$ | $\cot^{-1} x$ | $\frac{\pi}{4}$ |
| $f'(x)$ | $-\frac{1}{1+x^2}$ | $-\frac{1}{2}$ |
| $f''(x)$ | $\frac{2x}{(1+x^2)^2}$ | $\frac{2}{4} = \frac{1}{2}$ |
| $f'''(x)$ | $\frac{2(1+x^2)^2 - 2x\cdot 2(1+x^2)\cdot 2x}{(1+x^2)^4} = \frac{2-6x^2}{(1+x^2)^3}$ | $\frac{2-6}{8} = -\frac{1}{2}$ |

$$\cot^{-1}x = \frac{\pi}{4} - \frac{1}{2}(x-1) + \frac{1/2}{2!}(x-1)^2 + \frac{-1/2}{3!}(x-1)^3 + \cdots$$

$$= \frac{\pi}{4} - \frac{(x-1)}{2} + \frac{(x-1)^2}{4} - \frac{(x-1)^3}{12} + \cdots$$

---

### 4.2 Deret Maclaurin

Kasus khusus deret Taylor dengan $a = 0$:
$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!}x^n = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f'''(0)}{3!}x^3 + \cdots$$

#### Contoh — $f(x) = \tan^{-1} x$, sampai orde ke-4:

| $n$ | $f^{(n)}(x)$ | $f^{(n)}(0)$ | $f^{(n)}(0)/n!$ |
|-----|-------------|-------------|-----------------|
| 0 | $\arctan x$ | $0$ | $0$ |
| 1 | $\frac{1}{1+x^2}$ | $1$ | $1$ |
| 2 | $-\frac{2x}{(1+x^2)^2}$ | $0$ | $0$ |
| 3 | $\frac{2(3x^2-1)}{(1+x^2)^3}$ | $-2$ | $-\frac{2}{6} = -\frac{1}{3}$ |
| 4 | (turunan ke-4, eval di 0) | $0$ | $0$ |

$$\arctan x = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots = \sum_{n=0}^{\infty}(-1)^n\frac{x^{2n+1}}{2n+1}$$

> Cara lebih cepat: gunakan deret geometri $\frac{1}{1+t} = \sum(-t)^n$, ganti $t=x^2$, lalu integralkan suku demi suku.

---

### 4.3 Daftar Deret Maclaurin Penting (Wajib Hafal)

| Fungsi | Deret Maclaurin | Radius Konvergensi |
|--------|-----------------|-------------------|
| $e^x$ | $\displaystyle\sum_{n=0}^{\infty}\frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots$ | $R = \infty$ |
| $\sin x$ | $\displaystyle\sum_{n=0}^{\infty}\frac{(-1)^n x^{2n+1}}{(2n+1)!} = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots$ | $R = \infty$ |
| $\cos x$ | $\displaystyle\sum_{n=0}^{\infty}\frac{(-1)^n x^{2n}}{(2n)!} = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots$ | $R = \infty$ |
| $\frac{1}{1-x}$ | $\displaystyle\sum_{n=0}^{\infty}x^n = 1 + x + x^2 + x^3 + \cdots$ | $R = 1$ |
| $\frac{1}{1+x}$ | $\displaystyle\sum_{n=0}^{\infty}(-1)^n x^n = 1 - x + x^2 - x^3 + \cdots$ | $R = 1$ |
| $\ln(1+x)$ | $\displaystyle\sum_{n=1}^{\infty}\frac{(-1)^{n+1}x^n}{n} = x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots$ | $-1 < x \leq 1$ |
| $\arctan x$ | $\displaystyle\sum_{n=0}^{\infty}\frac{(-1)^n x^{2n+1}}{2n+1} = x - \frac{x^3}{3} + \frac{x^5}{5} - \cdots$ | $R = 1$ |
| $e^{2x}$ | $\displaystyle\sum_{n=0}^{\infty}\frac{(2x)^n}{n!} = 1 + 2x + 2x^2 + \frac{4x^3}{3} + \cdots$ | $R = \infty$ |
| $\sinh x$ | $\displaystyle x + \frac{x^3}{3!} + \frac{x^5}{5!} + \cdots$ | $R = \infty$ |
| $\cosh x$ | $\displaystyle 1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \cdots$ | $R = \infty$ |

**Teknik Substitusi:** Untuk mendapat deret fungsi komposit, substitusi ke deret yang diketahui.

Contoh: $e^{2x}$ → ganti $x$ dengan $2x$ di deret $e^u$:
$$e^{2x} = 1 + 2x + \frac{(2x)^2}{2!} + \frac{(2x)^3}{3!} + \frac{(2x)^4}{4!} + \cdots = 1 + 2x + 2x^2 + \frac{4x^3}{3} + \frac{2x^4}{3} + \cdots$$

---

## 5. Tabel Rumus Referensi Cepat

### Antiturunan Dasar

| Fungsi | Antiturunan |
|--------|-------------|
| $x^n\ (n\neq -1)$ | $\dfrac{x^{n+1}}{n+1} + C$ |
| $\dfrac{1}{x}$ | $\ln|x| + C$ |
| $e^x$ | $e^x + C$ |
| $\sin x$ | $-\cos x + C$ |
| $\cos x$ | $\sin x + C$ |
| $\sec^2 x$ | $\tan x + C$ |
| $\tan x$ | $\ln|\sec x| + C$ |
| $\sec x$ | $\ln|\sec x + \tan x| + C$ |
| $\sinh x$ | $\cosh x + C$ |
| $\cosh x$ | $\sinh x + C$ |
| $\dfrac{1}{a^2+x^2}$ | $\dfrac{1}{a}\arctan\dfrac{x}{a} + C$ |
| $\dfrac{1}{\sqrt{a^2-x^2}}$ | $\arcsin\dfrac{x}{a} + C$ |
| $\dfrac{1}{\sqrt{x^2+a^2}}$ | $\ln\left|x+\sqrt{x^2+a^2}\right| + C$ |
| $\dfrac{1}{\sqrt{x^2-a^2}}$ | $\ln\left|x+\sqrt{x^2-a^2}\right| + C$ |

### Rumus Khusus Integral Parsial (Hasil Jadi)

| Integral | Hasil |
|----------|-------|
| $\int \ln x\, dx$ | $x(\ln x - 1) + C$ |
| $\int x\ln x\, dx$ | $\frac{x^2}{4}(2\ln x - 1) + C$ |
| $\int x^n \ln x\, dx$ | $\frac{x^{n+1}}{n+1}\left(\ln x - \frac{1}{n+1}\right) + C$ |
| $\int \arctan x\, dx$ | $x\arctan x - \frac{1}{2}\ln(1+x^2) + C$ |
| $\int \arcsin x\, dx$ | $x\arcsin x + \sqrt{1-x^2} + C$ |
| $\int e^x\sin x\, dx$ | $\frac{e^x}{2}(\sin x - \cos x) + C$ |
| $\int e^x\cos x\, dx$ | $\frac{e^x}{2}(\sin x + \cos x) + C$ |
| $\int e^{ax}\sin bx\, dx$ | $\frac{e^{ax}(a\sin bx - b\cos bx)}{a^2+b^2} + C$ |
| $\int e^{ax}\cos bx\, dx$ | $\frac{e^{ax}(a\cos bx + b\sin bx)}{a^2+b^2} + C$ |
| $\int \sec^3 x\, dx$ | $\frac{1}{2}(\sec x\tan x + \ln|\sec x+\tan x|) + C$ |
| $\int \frac{\ln x}{x^2}\, dx$ | $-\frac{1+\ln x}{x} + C$ |

---

## 6. Prediksi Pola Soal UAS

Berdasarkan analisis soal Tugas Besar 2 dan Soal Tutorial MATH6135031:

### Bagian 1 — Teknik Integral (±30 poin)

**Pola soal yang kemungkinan besar muncul:**

| Teknik | Contoh bentuk soal |
|--------|-------------------|
| Substitusi | $\int\frac{\cos x}{2+\sin x}dx$, $\int\frac{e^{2x}}{1+e^{2x}}dx$, $\int\frac{\sin\sqrt{1-x}}{\sqrt{1-x}}dx$ |
| Parsial (Log/Invers Trig) | $\int\ln x\, dx$, $\int\frac{\ln x}{x^2}dx$, $\int\sqrt{x}\ln x\, dx$, $\int x^n\ln x\, dx$ |
| Parsial (Polinomial × Eksp/Trig) | $\int xe^x dx$, $\int x^2\cos x\, dx$, $\int e^x\sin x\, dx$ |
| Parsial siklik | $\int e^x\sin x\, dx$, $\int\cos x\sinh x\, dx$ |
| Integral trig (sin/cos) | $\int\sin^5 4x\cos^2 4x\, dx$, $\int\cos^5\theta\, d\theta$, $\int_0^\pi \cos^n x\, dx$ |
| Substitusi trig (√) | $\int\frac{1}{\sqrt{9+x^2}}dx$, $\int\frac{\sqrt{4-x^2}}{x}dx$, $\int x^5\sqrt{x^3+4}dx$ |
| Substitusi trig + parsial | $\int\frac{x^2}{\sqrt{x^2-4}}dx$ |
| Pecahan parsial | $\int\frac{x+2}{(x^2+4x+1)^2}dx$, $\int\frac{\sin(4x-1)}{1-\sin^2(4x-1)}dx$ |

> **Tips:** Untuk $\int x^5\sqrt{x^3+4}\, dx$, gunakan substitusi $u = x^3+4$ (bukan substitusi trig) karena $du = 3x^2 dx$ dan $x^5 = x^3 \cdot x^2 = (u-4)\cdot \frac{du}{3}$.

### Bagian 2 — Aplikasi Integral (±25 poin)

- Sketsa daerah + titik potong: **selalu diminta**
- Luas antara dua kurva (integrasi terhadap $x$ atau $y$)
- Volume dengan metode disk dan washer
- Volume putar terhadap garis $y = c$ (bukan hanya sumbu koordinat)
- Panjang kurva $\int\sqrt{1+(y')^2}\, dx$

### Bagian 3 — Kekonvergenan Deret (±30 poin)

**Deret positif — Pola uji yang sering dipakai:**
- $\frac{\ln n}{n^2}$ → Uji Banding Limit atau Uji Integral
- $k^2 e^{-k^3}$ → Uji Integral
- $k e^{-3k^2}$ → Uji Integral
- $\frac{2^n}{n!}$ → Uji Rasio
- $\frac{n!}{n^{100}}$ → Uji Rasio
- $\frac{n^3}{(2n)!}$ → Uji Rasio

**Deret berganti tanda — selalu minta klasifikasi mutlak/bersyarat:**
- Periksa $\sum|a_n|$ dahulu
- Jika divergen, pakai Leibniz untuk $\sum a_n$

### Bagian 4 — Deret Taylor & Maclaurin (±15 poin)

- Deret Taylor $f(x)$ di sekitar $a \neq 0$ sampai orde ke-3 atau ke-4
- Deret Maclaurin $f(x)$ di sekitar $a = 0$
- Fungsi yang paling sering diuji: $\sqrt{x}$, $\arctan x$, $\cot^{-1}x$, $e^{2x}$, $\ln(1+x)$

---

> **Dokumen ini disusun berdasarkan:** Diktat Teknik Integrasi MATH 6031, Diktat Integral Parsial MATH 6031, Diktat Barisan dan Deret MATH 6031, Soal Latihan Tutorial MATH6135031, dan Tugas Besar 2 Calculus 2025/2026.
>
> **Rujukan utama:** Stewart, Clegg, Watson (2020). *Calculus: Early Transcendentals*, 9th ed.
