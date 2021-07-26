Introduction to Data Science with R
================

NA dan default type

``` r
#Ketik nilai NA
NA
```

    ## [1] NA

``` r
#Tampilkan type dari NA dengan function typeof
typeof(NA)
```

    ## [1] "logical"

Menggunakan function is.na

``` r
#Buat variable x yang diisi dengan nilai NA
x <- NA

#Pengecekan variable x dengan nilai NA menggunakan operator ==
x == NA
```

    ## [1] NA

``` r
#Pengecekan variable x dengan nilai NA menggunakan function is.na
is.na(x)
```

    ## [1] TRUE

Variasi NA dan is.na

``` r
typeof(NA_integer_)
```

    ## [1] "integer"

``` r
typeof(NA_real_)
```

    ## [1] "double"

``` r
typeof(NA_complex_)
```

    ## [1] "complex"

``` r
typeof(NA_character_)
```

    ## [1] "character"

``` r
is.na(NA_integer_)
```

    ## [1] TRUE

``` r
is.na(NA_real_)
```

    ## [1] TRUE

``` r
is.na(NA_complex_)
```

    ## [1] TRUE

``` r
is.na(NA_character_)
```

    ## [1] TRUE

Coercion pada Vector yang mengandung NA

``` r
#Membuat vector bernama isi.vector dengan isi bilangan, dimana salah satunya memiliki missing value
isi.vector <- c(1,2,3,NA,3,1)

#Mengecek keseluruhan tipe data dengan perulangan lapply dan typeof
lapply(isi.vector, typeof)
```

    ## [[1]]
    ## [1] "double"
    ## 
    ## [[2]]
    ## [1] "double"
    ## 
    ## [[3]]
    ## [1] "double"
    ## 
    ## [[4]]
    ## [1] "double"
    ## 
    ## [[5]]
    ## [1] "double"
    ## 
    ## [[6]]
    ## [1] "double"

``` r
#Menggunakan is.na untuk mengecek keberadaan missing value dari tiap elemen pada vector 
is.na(isi.vector)
```

    ## [1] FALSE FALSE FALSE  TRUE FALSE FALSE

NULL dan Vector

``` r
#Membuat vector dengan 7 elemen termasuk NA dan NULL
isi.vector <- c(1, 2, 3, NA, 5, NULL, 7)

#Menghitung jumlah elemen dari isi.vector
length(isi.vector)
```

    ## [1] 6

NULL dan List

``` r
#Membuat list dengan 3 elemen termasuk NA dan NULL 
isi.list <- list(1,NULL,3,NA,5)

#Menghitung jumlah elemen dari isi.list
length(isi.list)
```

    ## [1] 5

Inf untuk mewakili Infinite Number

``` r
#Hitung kalkulasi 5 dibagi dengan 0
5/0
```

    ## [1] Inf

``` r
#Hitung kalkulasi -120 dibagi dengan 0
-120/0
```

    ## [1] -Inf

NaN (Not a Number)

``` r
#Hitung kalkulasi 0 dibagi dengan 0
0/0
```

    ## [1] NaN

NaN dari hasil function log()

``` r
#Hitung logaritma dari angka -1000
log(-1000)
```

    ## Warning in log(-1000): NaNs produced

    ## [1] NaN

Fungsi is.nan

``` r
#Buat variable contoh.nan
contoh.nan <- 0/0

#Periksa dengan function is.nan
is.nan(contoh.nan)
```

    ## [1] TRUE

NaN dan is.na versus NA dan is.nan

``` r
#Masukkan code di bawah ini sesuai permintaan soal
is.na(NaN)
```

    ## [1] TRUE

``` r
is.nan(NA)
```

    ## [1] FALSE

Menghitung Jumlah Missing Values dari satu Vector

``` r
#Masukkan code di bawah ini sesuai permintaan soal
isi.vector <- c(1,2,NA,4,5,NaN,6)
sum(is.na(isi.vector)==TRUE)
```

    ## [1] 2

Membuat Factor di R

``` r
#Buatlah factor dengan isi nilai teks "Jan", "Feb", dan "Mar"
factor(c("Jan","Feb","Mar"))
```

    ## [1] Jan Feb Mar
    ## Levels: Feb Jan Mar

Atribut levels dan class pada Factor

``` r
#Variable factor bernama faktor.bulan dengan nilai teks "Jan", "Feb", dan "Mar"
faktor.bulan <- factor(c("Jan","Feb","Mar"))
attributes(faktor.bulan)
```

    ## $levels
    ## [1] "Feb" "Jan" "Mar"
    ## 
    ## $class
    ## [1] "factor"

Function levels dan class pada Factor

``` r
#Variable factor bernama faktor.bulan dengan nilai teks "Jan", "Feb", dan "Mar"
faktor.bulan <- factor(c("Jan","Feb","Mar"))
levels(faktor.bulan)
```

    ## [1] "Feb" "Jan" "Mar"

``` r
class(faktor.bulan)
```

    ## [1] "factor"

Perulangan Nilai pada Factor

``` r
#Buatlah factor dengan teks "Jan", "Feb", "Mar","Jan","Mar", dan "Jan"
factor(c("Jan","Feb","Mar","Jan","Mar","Jan"))
```

    ## [1] Jan Feb Mar Jan Mar Jan
    ## Levels: Feb Jan Mar

Penggunaan as.integer pada Factor

``` r
#Buatlah factor dengan teks "Jan", "Feb", "Mar","Jan","Mar", dan "Jan"
factor.bulan <- factor(c("Jan","Feb","Mar","Jan","Mar","Jan"))
as.integer(factor.bulan)
```

    ## [1] 2 1 3 2 3 2

Mengganti “Jan” menjadi “Januari”

``` r
#Buatlah factor dengan teks "Jan", "Feb", "Mar","Jan","Mar", dan "Jan"
factor.bulan <- factor(c("Jan","Feb","Mar","Jan","Mar","Jan"))
#Mengganti levels 
levels(factor.bulan)[2] <- "Januari"
levels(factor.bulan)[3] <- "Maret"
factor.bulan
```

    ## [1] Januari Feb     Maret   Januari Maret   Januari
    ## Levels: Feb Januari Maret

Angka sebagai Kategori

``` r
#Buatlah factor bernama factor.umur dengan isi c(12, 35, 24, 12, 35, 37)
factor.umur <- factor(c(12, 35, 24, 12, 35, 37))
#Tampilkan variable factor.umur 
factor.umur
```

    ## [1] 12 35 24 12 35 37
    ## Levels: 12 24 35 37

NA, NaN, NULL pada saat pembentukan Factor

``` r
#Buatlah variable factor.lokasi dengan isi berupa vector c("Bandung", "Jakarta", NA, "Jakarta", NaN, "Medan", NULL, NULL, "Bandung") 
factor.lokasi <- factor(c("Bandung", "Jakarta", NA, "Jakarta", NaN, "Medan", NULL, NULL, "Bandung"))
#Tampilkan factor.lokasi
factor.lokasi
```

    ## [1] Bandung Jakarta <NA>    Jakarta NaN     Medan   Bandung
    ## Levels: Bandung Jakarta Medan NaN

Menghitung panjang Factor dengan length

``` r
#Buatlah variable factor.lokasi dengan isi berupa vector c("Bandung", "Jakarta", NA, "Jakarta", NaN, "Medan", NULL, NULL, "Bandung") 
factor.lokasi <- factor(c("Bandung", "Jakarta", NA, "Jakarta", NaN, "Medan", NULL, NULL, "Bandung"))
#Tampilkan panjang dari variable factor.lokasi
length(factor.lokasi)
```

    ## [1] 7

Menyusun levels dari awal

``` r
#Variable factor dengan isi vector c("Jan","Feb","Mar","Jan","Mar") 
factor(c("Jan","Feb","Mar","Jan","Mar"), levels = c("Jan","Feb","Mar"))
```

    ## [1] Jan Feb Mar Jan Mar
    ## Levels: Jan Feb Mar

Membaca Dataset CSV

``` r
#Membaca dataset dengan read.csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
penduduk.dki
```

    ##     TAHUN        NAMA.PROVINSI NAMA.KABUPATEN.KOTA    NAMA.KECAMATAN
    ## 1    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 2    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 3    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 4    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 5    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 6    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 7    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 8    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 9    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 10   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 11   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 12   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 13   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 14   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 15   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 16   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 17   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 18   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 19   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 20   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 21   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 22   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 23   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 24   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 25   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 26   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 27   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 28   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 29   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 30   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 31   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 32   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 33   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 34   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 35   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 36   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 37   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 38   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 39   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 40   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 41   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 42   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 43   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 44   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 45   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 46   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 47   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 48   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 49   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 50   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 51   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 52   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 53   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 54   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 55   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 56   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 57   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 58   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 59   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 60   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 61   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 62   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 63   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 64   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 65   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 66   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 67   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 68   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 69   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 70   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 71   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 72   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 73   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 74   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 75   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 76   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 77   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 78   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 79   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 80   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 81   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 82   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 83   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 84   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 85   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 86   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 87   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 88   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 89   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 90   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 91   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 92   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 93   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 94   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 95   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 96   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 97   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 98   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 99   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 100  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 101  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 102  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 103  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 104  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 105  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 106  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 107  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 108  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 109  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 110  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 111  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 112  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 113  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 114  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 115  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 116  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 117  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 118  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 119  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 120  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 121  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 122  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 123  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 124  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 125  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 126  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 127  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 128  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 129  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 130  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 131  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 132  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 133  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 134  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 135  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 136  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 137  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 138  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 139  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 140  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 141  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 142  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 143  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 144  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 145  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 146  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 147  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 148  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 149  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 150  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 151  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 152  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 153  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 154  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 155  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 156  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 157  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 158  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 159  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 160  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 161  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 162  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 163  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 164  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 165  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 166  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 167  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 168  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 169  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 170  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 171  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 172  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 173  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 174  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 175  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 176  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 177  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 178  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 179  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 180  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 181  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 182  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 183  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 184  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 185  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 186  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 187  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 188  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 189  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 190  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 191  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 192  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 193  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 194  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 195  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 196  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 197  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 198  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 199  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 200  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 201  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 202  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 203  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 204  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 205  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 206  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 207  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 208  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 209  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 210  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 211  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 212  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 213  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 214  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 215  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 216  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 217  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 218  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 219  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 220  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 221  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 222  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 223  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 224  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 225  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 226  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 227  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 228  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 229  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 230  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 231  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 232  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 233  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 234  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 235  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 236  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 237  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 238  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 239  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 240  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 241  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 242  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 243  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 244  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 245  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 246  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 247  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 248  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 249  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 250  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 251  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 252  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 253  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 254  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 255  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 256  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 257  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 258  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 259  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 260  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 261  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 262  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 263  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 264  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 265  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 266  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 267  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ##             NAMA.KELURAHAN LUAS.WILAYAH..KM2. KEPADATAN..JIWA.KM2.  X X.1 X.2
    ## 1              P. PANGGANG               0.91                 6779 NA  NA  NA
    ## 2                P. KELAPA               3.76                 1705 NA  NA  NA
    ## 3               P. HARAPAN               3.59                  628 NA  NA  NA
    ## 4           P. UNTUNG JAWA               0.59                 3625 NA  NA  NA
    ## 5                P. TIDUNG               1.57                 3084 NA  NA  NA
    ## 6                  P. PARI               1.39                 1968 NA  NA  NA
    ## 7                   GAMBIR               2.58                 1350 NA  NA  NA
    ## 8                   CIDENG               1.26                14584 NA  NA  NA
    ## 9             PETOJO UTARA               1.12                18987 NA  NA  NA
    ## 10          PETOJO SELATAN               1.14                14465 NA  NA  NA
    ## 11            KEBON KELAPA               0.78                15890 NA  NA  NA
    ## 12               DURI PULO               0.72                35628 NA  NA  NA
    ## 13              PASAR BARU               1.89                 8041 NA  NA  NA
    ## 14            KARANG ANYAR               0.51                63122 NA  NA  NA
    ## 15                 KARTINI               0.55                49862 NA  NA  NA
    ## 16     GUNUNG SAHARI UTARA               1.98                 9933 NA  NA  NA
    ## 17      MANGGA DUA SELATAN               1.29                26203 NA  NA  NA
    ## 18               KEMAYORAN               0.55                44202 NA  NA  NA
    ## 19            KEBON KOSONG               1.13                28014 NA  NA  NA
    ## 20           HARAPAN MULIA               0.91                29205 NA  NA  NA
    ## 21                 SERDANG               0.82                41837 NA  NA  NA
    ## 22   GUNUNG SAHARI SELATAN               0.53                43858 NA  NA  NA
    ## 23            CEMPAKA BARU               0.99                38088 NA  NA  NA
    ## 24              SUMUR BATU               1.15                23271 NA  NA  NA
    ## 25            UTAN PANJANG               1.05                31889 NA  NA  NA
    ## 26                   SENEN               0.81                10158 NA  NA  NA
    ## 27                  KENARI               0.91                11757 NA  NA  NA
    ## 28                 PASEBAN               0.71                38400 NA  NA  NA
    ## 29                  KRAMAT               0.71                47630 NA  NA  NA
    ## 30                 KWITANG               0.45                40724 NA  NA  NA
    ## 31                  BUNGUR               0.64                34463 NA  NA  NA
    ## 32     CEMPAKA PUTIH TIMUR               2.22                12326 NA  NA  NA
    ## 33     CEMPAKA PUTIH BARAT               1.22                32561 NA  NA  NA
    ## 34                RAWASARI               1.25                19945 NA  NA  NA
    ## 35                 MENTENG               2.44                11968 NA  NA  NA
    ## 36              PEGANGSAAN               0.98                27151 NA  NA  NA
    ## 37                  CIKINI               0.82                11711 NA  NA  NA
    ## 38              GONDANGDIA               1.46                 3194 NA  NA  NA
    ## 39             KEBON SIRIH               0.83                18577 NA  NA  NA
    ## 40                  GELORA               2.59                 1450 NA  NA  NA
    ## 41         BENDUNGAN HILIR               1.58                16018 NA  NA  NA
    ## 42           KARET TENGSIN               1.53                13912 NA  NA  NA
    ## 43              PETAMBURAN               0.90                43262 NA  NA  NA
    ## 44            KEBON MELATI               1.26                30563 NA  NA  NA
    ## 45            KEBON KACANG               0.71                35545 NA  NA  NA
    ## 46            KAMPUNG BALI               0.73                19941 NA  NA  NA
    ## 47              JOHAR BARU               1.19                35270 NA  NA  NA
    ## 48            KAMPUNG RAWA               0.30                86123 NA  NA  NA
    ## 49                   GALUR               0.27                79022 NA  NA  NA
    ## 50            TANAH TINGGI               0.62                71177 NA  NA  NA
    ## 51             PENJARINGAN               3.95                28071 NA  NA  NA
    ## 52             KAMAL MUARA              10.53                 1144 NA  NA  NA
    ## 53             KAPUK MUARA              10.56                 3243 NA  NA  NA
    ## 54               PEJAGALAN               3.23                27856 NA  NA  NA
    ## 55                   PLUIT               7.71                 6344 NA  NA  NA
    ## 56           TANJUNG PRIOK               5.59                 7794 NA  NA  NA
    ## 57             SUNTER JAYA               4.68                14791 NA  NA  NA
    ## 58                PAPANGGO               2.80                16353 NA  NA  NA
    ## 59            SUNGAI BAMBU               2.36                15221 NA  NA  NA
    ## 60            KEBON BAWANG               1.73                35952 NA  NA  NA
    ## 61            SUNTER AGUNG               6.65                12234 NA  NA  NA
    ## 62                 WARAKAS               1.09                49384 NA  NA  NA
    ## 63                    KOJA               3.27                10838 NA  NA  NA
    ## 64              TUGU UTARA               2.37                34123 NA  NA  NA
    ## 65                   LAGOA               1.58                44105 NA  NA  NA
    ## 66        RAWA BADAK UTARA               1.33                31357 NA  NA  NA
    ## 67            TUGU SELATAN               1.86                22869 NA  NA  NA
    ## 68      RAWA BADAK SELATAN               1.33                35441 NA  NA  NA
    ## 69               CILINCING               8.31                 6326 NA  NA  NA
    ## 70                SUKAPURA               5.61                11602 NA  NA  NA
    ## 71                 MARUNDA               7.92                 3105 NA  NA  NA
    ## 72               KALI BARU               2.47                34278 NA  NA  NA
    ## 73            SEMPER TIMUR               3.17                12725 NA  NA  NA
    ## 74                 ROROTAN              10.64                 3859 NA  NA  NA
    ## 75            SEMPER BARAT               4.44                18003 NA  NA  NA
    ## 76        PADEMANGAN TIMUR               2.61                16245 NA  NA  NA
    ## 77        PADEMANGAN BARAT               3.53                24947 NA  NA  NA
    ## 78                   ANCOL               5.77                 4981 NA  NA  NA
    ## 79     KELAPA GADING TIMUR               5.31                 7089 NA  NA  NA
    ## 80          PEGANGSAAN DUA               6.28                 8216 NA  NA  NA
    ## 81     KELAPA GADING BARAT               4.53                 8515 NA  NA  NA
    ## 82        CENGKARENG BARAT               4.26                16409 NA  NA  NA
    ## 83            DURI KOSAMBI               5.03                15866 NA  NA  NA
    ## 84              RAWA BUAYA               4.67                14886 NA  NA  NA
    ## 85      KEDAUNG KALI ANGKE               2.61                14438 NA  NA  NA
    ## 86                   KAPUK               7.18                20919 NA  NA  NA
    ## 87        CENGKARENG TIMUR               4.18                20735 NA  NA  NA
    ## 88                  GROGOL               1.22                16960 NA  NA  NA
    ## 89     TANJUNG DUREN UTARA               1.11                18227 NA  NA  NA
    ## 90                  TOMANG               1.88                18103 NA  NA  NA
    ## 91                JELAMBAR               1.44                24624 NA  NA  NA
    ## 92   TANJUNG DUREN SELATAN               1.76                15915 NA  NA  NA
    ## 93           JELAMBAR BARU               1.44                30778 NA  NA  NA
    ## 94           WIJAYA KUSUMA               2.61                17092 NA  NA  NA
    ## 95              TAMAN SARI               0.68                26441 NA  NA  NA
    ## 96                  KRUKUT               0.55                42111 NA  NA  NA
    ## 97                  MAPHAR               0.59                34693 NA  NA  NA
    ## 98                  TANGKI               0.37                43827 NA  NA  NA
    ## 99            MANGGA BESAR               0.51                17882 NA  NA  NA
    ## 100              KEAGUNGAN               0.32                65800 NA  NA  NA
    ## 101                 GLODOK               0.38                24153 NA  NA  NA
    ## 102              PINANGSIA               0.96                13791 NA  NA  NA
    ## 103                TAMBORA               0.28                45375 NA  NA  NA
    ## 104             KALI ANYAR               0.32                94166 NA  NA  NA
    ## 105             DURI UTARA               0.40                60175 NA  NA  NA
    ## 106           TANAH SEREAL               0.62                49860 NA  NA  NA
    ## 107              KERENDANG               0.32                74109 NA  NA  NA
    ## 108          JEMBATAN BESI               0.55                66447 NA  NA  NA
    ## 109                  ANGKE               0.80                43826 NA  NA  NA
    ## 110          JEMBATAN LIMA               0.46                54543 NA  NA  NA
    ## 111                PEKOJAN               0.78                35333 NA  NA  NA
    ## 112             ROA MALAKA               0.53                 8275 NA  NA  NA
    ## 113           DURI SELATAN               0.42                41460 NA  NA  NA
    ## 114            KEBON JERUK               2.69                20957 NA  NA  NA
    ## 115         SUKABUMI UTARA               1.60                26438 NA  NA  NA
    ## 116       SUKABUMI SELATAN               1.57                26532 NA  NA  NA
    ## 117             KELAPA DUA               1.50                17297 NA  NA  NA
    ## 118              DURI KEPA               3.86                17148 NA  NA  NA
    ## 119           KEDOYA UTARA               3.14                15976 NA  NA  NA
    ## 120         KEDOYA SELATAN               2.28                15519 NA  NA  NA
    ## 121              KALIDERES               5.72                13726 NA  NA  NA
    ## 122                SEMANAN               5.98                13037 NA  NA  NA
    ## 123             TEGAL ALUR               4.00                23429 NA  NA  NA
    ## 124                  KAMAL               4.49                12257 NA  NA  NA
    ## 125             PEGADUNGAN               8.89                 8364 NA  NA  NA
    ## 126               PALMERAH               2.11                33544 NA  NA  NA
    ## 127                  SLIPI               0.97                19980 NA  NA  NA
    ## 128       KOTA BAMBU UTARA               0.63                46608 NA  NA  NA
    ## 129              JATI PULO               0.87                38834 NA  NA  NA
    ## 130            KEMANGGISAN               2.33                16328 NA  NA  NA
    ## 131     KOTA BAMBU SELATAN               0.61                41082 NA  NA  NA
    ## 132        KEMBANGAN UTARA               3.65                15703 NA  NA  NA
    ## 133           MERUYA UTARA               4.76                 9608 NA  NA  NA
    ## 134         MERUYA SELATAN               2.85                11142 NA  NA  NA
    ## 135              SRENGSENG               4.92                 9446 NA  NA  NA
    ## 136                  JOGLO               4.86                 8812 NA  NA  NA
    ## 137      KEMBANGAN SELATAN               3.60                 7866 NA  NA  NA
    ## 138            TEBET TIMUR               1.39                14544 NA  NA  NA
    ## 139            TEBET BARAT               1.72                14080 NA  NA  NA
    ## 140          MENTENG DALAM               2.58                16355 NA  NA  NA
    ## 141             KEBON BARU               1.30                31580 NA  NA  NA
    ## 142             BUKIT DURI               1.08                38906 NA  NA  NA
    ## 143      MANGGARAI SELATAN               0.51                52659 NA  NA  NA
    ## 144              MANGGARAI               0.95                36246 NA  NA  NA
    ## 145             SETIA BUDI               0.94                 3852 NA  NA  NA
    ## 146         KARET SEMANGGI               0.90                 3202 NA  NA  NA
    ## 147         KARET KUNINGAN               1.79                10414 NA  NA  NA
    ## 148                  KARET               0.94                12948 NA  NA  NA
    ## 149           MENTENG ATAS               0.90                35511 NA  NA  NA
    ## 150          PASAR MANGGIS               0.78                40395 NA  NA  NA
    ## 151                 GUNTUR               0.65                 7174 NA  NA  NA
    ## 152         KUNINGAN TIMUR               2.15                 3335 NA  NA  NA
    ## 153       MAMPANG PRAPATAN               0.78                27765 NA  NA  NA
    ## 154                 BANGKA               3.30                 7351 NA  NA  NA
    ## 155           PELA MAMPANG               1.62                30940 NA  NA  NA
    ## 156           TEGAL PARANG               1.06                34830 NA  NA  NA
    ## 157         KUNINGAN BARAT               0.98                15120 NA  NA  NA
    ## 158           PASAR MINGGU               2.79                 9965 NA  NA  NA
    ## 159            JATI PADANG               2.50                16524 NA  NA  NA
    ## 160         CILANDAK TIMUR               3.53                 8075 NA  NA  NA
    ## 161                RAGUNAN               5.05                 8681 NA  NA  NA
    ## 162          PEJATEN TIMUR               2.88                22624 NA  NA  NA
    ## 163          PEJATEN BARAT               2.90                14338 NA  NA  NA
    ## 164              KEBAGUSAN               2.26                20705 NA  NA  NA
    ## 165   KEBAYORAN LAMA UTARA               1.78                27853 NA  NA  NA
    ## 166          PONDOK PINANG               6.84                 8897 NA  NA  NA
    ## 167                CIPULIR               1.94                22494 NA  NA  NA
    ## 168           GROGOL UTARA               3.33                14342 NA  NA  NA
    ## 169         GROGOL SELATAN               2.85                17009 NA  NA  NA
    ## 170 KEBAYORAN LAMA SELATAN               2.57                17598 NA  NA  NA
    ## 171         CILANDAK BARAT               6.05                 9546 NA  NA  NA
    ## 172            LEBAK BULUS               4.41                 8840 NA  NA  NA
    ## 173            PONDOK LABU               3.61                13349 NA  NA  NA
    ## 174       GANDARIA SELATAN               1.76                13816 NA  NA  NA
    ## 175         CIPETE SELATAN               2.37                12751 NA  NA  NA
    ## 176                MELAWAI               1.26                 2528 NA  NA  NA
    ## 177                 GUNUNG               1.32                 8043 NA  NA  NA
    ## 178            KRAMAT PELA               1.23                12872 NA  NA  NA
    ## 179                 SELONG               1.40                 3014 NA  NA  NA
    ## 180             RAWA BARAT               0.69                 9778 NA  NA  NA
    ## 181                SENAYAN               1.53                 2856 NA  NA  NA
    ## 182                   PULO               1.27                 5408 NA  NA  NA
    ## 183              PETOGOGAN               0.86                15895 NA  NA  NA
    ## 184         GANDARIA UTARA               1.52                29247 NA  NA  NA
    ## 185           CIPETE UTARA               1.83                20664 NA  NA  NA
    ## 186               PANCORAN               1.24                17127 NA  NA  NA
    ## 187               KALIBATA               2.20                21353 NA  NA  NA
    ## 188              RAWA JATI               0.67                29915 NA  NA  NA
    ## 189             DUREN TIGA               2.45                12987 NA  NA  NA
    ## 190             PENGADEGAN               0.95                24076 NA  NA  NA
    ## 191                 CIKOKO               0.72                17661 NA  NA  NA
    ## 192              JAGAKARSA               4.85                12940 NA  NA  NA
    ## 193        SRENGSENG SAWAH               6.75                 8912 NA  NA  NA
    ## 194               CIGANJUR               3.61                10334 NA  NA  NA
    ## 195          LENTENG AGUNG               2.28                24703 NA  NA  NA
    ## 196          TANJUNG BARAT               3.65                11460 NA  NA  NA
    ## 197                CIPEDAK               4.24                 8473 NA  NA  NA
    ## 198           PESANGGRAHAN               2.10                13859 NA  NA  NA
    ## 199                BINTARO               4.56                11808 NA  NA  NA
    ## 200       PETUKANGAN UTARA               2.99                19001 NA  NA  NA
    ## 201     PETUKANGAN SELATAN               2.11                18260 NA  NA  NA
    ## 202                ULUJAMI               1.71                26161 NA  NA  NA
    ## 203          PISANGAN BARU               0.68                54913 NA  NA  NA
    ## 204        UTAN KAYU UTARA               1.05                31694 NA  NA  NA
    ## 205             KAYU MANIS               0.57                52740 NA  NA  NA
    ## 206             PAL MERIAM               0.65                36818 NA  NA  NA
    ## 207          KEBON MANGGIS               0.78                25601 NA  NA  NA
    ## 208      UTAN KAYU SELATAN               1.12                34434 NA  NA  NA
    ## 209            PULO GADUNG               1.29                30260 NA  NA  NA
    ## 210         PISANGAN TIMUR               1.80                26931 NA  NA  NA
    ## 211               CIPINANG               1.54                29756 NA  NA  NA
    ## 212        JATINEGARA KAUM               1.23                21792 NA  NA  NA
    ## 213             RAWAMANGUN               2.60                16963 NA  NA  NA
    ## 214             KAYU PUTIH               4.37                11179 NA  NA  NA
    ## 215                   JATI               2.15                17270 NA  NA  NA
    ## 216         KAMPUNG MELAYU               0.48                63973 NA  NA  NA
    ## 217            BIDARA CINA               1.26                35493 NA  NA  NA
    ## 218            BALI MESTER               0.67                17304 NA  NA  NA
    ## 219             RAWA BUNGA               0.88                28478 NA  NA  NA
    ## 220      CIPINANG CEMPEDAK               1.67                22917 NA  NA  NA
    ## 221         CIPINANG MUARA               2.90                21525 NA  NA  NA
    ## 222 CIPINANG BESAR SELATAN               1.63                23417 NA  NA  NA
    ## 223   CIPINANG BESAR UTARA               1.15                48850 NA  NA  NA
    ## 224            KRAMAT JATI               1.52                25801 NA  NA  NA
    ## 225         KAMPUNG TENGAH               2.03                24281 NA  NA  NA
    ## 226                  DUKUH               1.98                13402 NA  NA  NA
    ## 227             BATU AMPAR               2.55                19983 NA  NA  NA
    ## 228           BALE KAMBANG               1.67                18012 NA  NA  NA
    ## 229              CILILITAN               1.80                26094 NA  NA  NA
    ## 230                 CAWANG               1.79                21827 NA  NA  NA
    ## 231                 GEDONG               2.65                14684 NA  NA  NA
    ## 232                   BARU               1.89                14133 NA  NA  NA
    ## 233              CIJANTUNG               2.37                18589 NA  NA  NA
    ## 234               KALISARI               2.89                15517 NA  NA  NA
    ## 235                PEKAYON               3.14                14600 NA  NA  NA
    ## 236             JATINEGARA               6.60                14709 NA  NA  NA
    ## 237            RAWA TERATE               4.10                 7387 NA  NA  NA
    ## 238           PENGGILINGAN               4.48                22483 NA  NA  NA
    ## 239           CAKUNG TIMUR               9.81                 6464 NA  NA  NA
    ## 240            PULO GEBANG               6.86                13716 NA  NA  NA
    ## 241          UJUNG MENTENG               4.43                 6972 NA  NA  NA
    ## 242           CAKUNG BARAT               6.19                10030 NA  NA  NA
    ## 243            DUREN SAWIT               4.58                14100 NA  NA  NA
    ## 244           PONDOK BAMBU               5.00                13285 NA  NA  NA
    ## 245                KLENDER               3.08                25456 NA  NA  NA
    ## 246          PONDOK KELAPA               5.72                12673 NA  NA  NA
    ## 247            MALAKA SARI               1.38                23592 NA  NA  NA
    ## 248            MALAKA JAYA               0.99                36535 NA  NA  NA
    ## 249            PONDOK KOPI               2.06                18136 NA  NA  NA
    ## 250                MAKASAR               1.85                20695 NA  NA  NA
    ## 251           PINANG RANTI               1.89                14793 NA  NA  NA
    ## 252             KEBON PALA               2.30                22647 NA  NA  NA
    ## 253  HALIM PERDANA KUSUMAH              13.07                 2546 NA  NA  NA
    ## 254        CIPINANG MELAYU               2.53                18551 NA  NA  NA
    ## 255                CIRACAS               3.93                17648 NA  NA  NA
    ## 256                CIBUBUR               4.50                15686 NA  NA  NA
    ## 257       KELAPA DUA WETAN               3.37                14203 NA  NA  NA
    ## 258                SUSUKAN               2.19                19019 NA  NA  NA
    ## 259               RAMBUTAN               2.09                19324 NA  NA  NA
    ## 260               CIPAYUNG               3.08                 8441 NA  NA  NA
    ## 261              CILANGKAP               6.03                 4396 NA  NA  NA
    ## 262         PONDOK RANGGON               3.66                 6772 NA  NA  NA
    ## 263                 MUNJUL               1.90                12734 NA  NA  NA
    ## 264                   SETU               3.25                 6028 NA  NA  NA
    ## 265             BAMBU APUS               3.17                 8400 NA  NA  NA
    ## 266           LUBANG BUAYA               3.72                18055 NA  NA  NA
    ## 267                  CEGER               3.63                 5492 NA  NA  NA
    ##     X.3 X.4 X.5 X.6 X.7 X.8 X.9 X.10 X.11 X35.39.Laki.Laki X35.39.Perempuan
    ## 1    NA  NA  NA  NA  NA  NA  NA   NA   NA              231              235
    ## 2    NA  NA  NA  NA  NA  NA  NA   NA   NA               84               88
    ## 3    NA  NA  NA  NA  NA  NA  NA   NA   NA              255              238
    ## 4    NA  NA  NA  NA  NA  NA  NA   NA   NA              199              185
    ## 5    NA  NA  NA  NA  NA  NA  NA   NA   NA               98               75
    ## 6    NA  NA  NA  NA  NA  NA  NA   NA   NA              113              112
    ## 7    NA  NA  NA  NA  NA  NA  NA   NA   NA              166              174
    ## 8    NA  NA  NA  NA  NA  NA  NA   NA   NA              850              748
    ## 9    NA  NA  NA  NA  NA  NA  NA   NA   NA              954              920
    ## 10   NA  NA  NA  NA  NA  NA  NA   NA   NA              752              675
    ## 11   NA  NA  NA  NA  NA  NA  NA   NA   NA              592              491
    ## 12   NA  NA  NA  NA  NA  NA  NA   NA   NA             1213             1106
    ## 13   NA  NA  NA  NA  NA  NA  NA   NA   NA              714              611
    ## 14   NA  NA  NA  NA  NA  NA  NA   NA   NA             1575             1485
    ## 15   NA  NA  NA  NA  NA  NA  NA   NA   NA             1307             1177
    ## 16   NA  NA  NA  NA  NA  NA  NA   NA   NA              817              835
    ## 17   NA  NA  NA  NA  NA  NA  NA   NA   NA             1683             1662
    ## 18   NA  NA  NA  NA  NA  NA  NA   NA   NA             1164             1063
    ## 19   NA  NA  NA  NA  NA  NA  NA   NA   NA             1644             1542
    ## 20   NA  NA  NA  NA  NA  NA  NA   NA   NA             1256             1213
    ## 21   NA  NA  NA  NA  NA  NA  NA   NA   NA             1603             1559
    ## 22   NA  NA  NA  NA  NA  NA  NA   NA   NA             1071              979
    ## 23   NA  NA  NA  NA  NA  NA  NA   NA   NA             1750             1710
    ## 24   NA  NA  NA  NA  NA  NA  NA   NA   NA             1452             1372
    ## 25   NA  NA  NA  NA  NA  NA  NA   NA   NA             1610             1549
    ## 26   NA  NA  NA  NA  NA  NA  NA   NA   NA              398              428
    ## 27   NA  NA  NA  NA  NA  NA  NA   NA   NA              456              447
    ## 28   NA  NA  NA  NA  NA  NA  NA   NA   NA             1266             1232
    ## 29   NA  NA  NA  NA  NA  NA  NA   NA   NA             1552             1479
    ## 30   NA  NA  NA  NA  NA  NA  NA   NA   NA              908              793
    ## 31   NA  NA  NA  NA  NA  NA  NA   NA   NA             1046              993
    ## 32   NA  NA  NA  NA  NA  NA  NA   NA   NA             1264             1267
    ## 33   NA  NA  NA  NA  NA  NA  NA   NA   NA             1858             1811
    ## 34   NA  NA  NA  NA  NA  NA  NA   NA   NA             1200             1160
    ## 35   NA  NA  NA  NA  NA  NA  NA   NA   NA             1349             1194
    ## 36   NA  NA  NA  NA  NA  NA  NA   NA   NA             1172             1096
    ## 37   NA  NA  NA  NA  NA  NA  NA   NA   NA              424              428
    ## 38   NA  NA  NA  NA  NA  NA  NA   NA   NA              192              165
    ## 39   NA  NA  NA  NA  NA  NA  NA   NA   NA              733              717
    ## 40   NA  NA  NA  NA  NA  NA  NA   NA   NA              185              178
    ## 41   NA  NA  NA  NA  NA  NA  NA   NA   NA             1124             1138
    ## 42   NA  NA  NA  NA  NA  NA  NA   NA   NA             1118             1078
    ## 43   NA  NA  NA  NA  NA  NA  NA   NA   NA             1851             1780
    ## 44   NA  NA  NA  NA  NA  NA  NA   NA   NA             1862             1721
    ## 45   NA  NA  NA  NA  NA  NA  NA   NA   NA             1150             1041
    ## 46   NA  NA  NA  NA  NA  NA  NA   NA   NA              612              613
    ## 47   NA  NA  NA  NA  NA  NA  NA   NA   NA             2036             1878
    ## 48   NA  NA  NA  NA  NA  NA  NA   NA   NA             1210             1255
    ## 49   NA  NA  NA  NA  NA  NA  NA   NA   NA              999             1060
    ## 50   NA  NA  NA  NA  NA  NA  NA   NA   NA             2118             2013
    ## 51   NA  NA  NA  NA  NA  NA  NA   NA   NA             9225             5535
    ## 52   NA  NA  NA  NA  NA  NA  NA   NA   NA             1045              517
    ## 53   NA  NA  NA  NA  NA  NA  NA   NA   NA             2763             1631
    ## 54   NA  NA  NA  NA  NA  NA  NA   NA   NA             7137             4468
    ## 55   NA  NA  NA  NA  NA  NA  NA   NA   NA             3656             2264
    ## 56   NA  NA  NA  NA  NA  NA  NA   NA   NA             3374             2025
    ## 57   NA  NA  NA  NA  NA  NA  NA   NA   NA             5374             3427
    ## 58   NA  NA  NA  NA  NA  NA  NA   NA   NA             3667             2290
    ## 59   NA  NA  NA  NA  NA  NA  NA   NA   NA             2807             1749
    ## 60   NA  NA  NA  NA  NA  NA  NA   NA   NA             4677             3009
    ## 61   NA  NA  NA  NA  NA  NA  NA   NA   NA             6094             3710
    ## 62   NA  NA  NA  NA  NA  NA  NA   NA   NA             4224             2608
    ## 63   NA  NA  NA  NA  NA  NA  NA   NA   NA             3088             1767
    ## 64   NA  NA  NA  NA  NA  NA  NA   NA   NA             6608             3954
    ## 65   NA  NA  NA  NA  NA  NA  NA   NA   NA             5931             3342
    ## 66   NA  NA  NA  NA  NA  NA  NA   NA   NA             3260             2064
    ## 67   NA  NA  NA  NA  NA  NA  NA   NA   NA             3744             2235
    ## 68   NA  NA  NA  NA  NA  NA  NA   NA   NA             3910             2420
    ## 69   NA  NA  NA  NA  NA  NA  NA   NA   NA             4654             2614
    ## 70   NA  NA  NA  NA  NA  NA  NA   NA   NA             5221             3376
    ## 71   NA  NA  NA  NA  NA  NA  NA   NA   NA             2187             1207
    ## 72   NA  NA  NA  NA  NA  NA  NA   NA   NA             7616             4096
    ## 73   NA  NA  NA  NA  NA  NA  NA   NA   NA             3230             1683
    ## 74   NA  NA  NA  NA  NA  NA  NA   NA   NA             3442             1876
    ## 75   NA  NA  NA  NA  NA  NA  NA   NA   NA             6419             3579
    ## 76   NA  NA  NA  NA  NA  NA  NA   NA   NA             3005             1935
    ## 77   NA  NA  NA  NA  NA  NA  NA   NA   NA             7178             4264
    ## 78   NA  NA  NA  NA  NA  NA  NA   NA   NA             2259             1380
    ## 79   NA  NA  NA  NA  NA  NA  NA   NA   NA             2539             1744
    ## 80   NA  NA  NA  NA  NA  NA  NA   NA   NA             4170             2259
    ## 81   NA  NA  NA  NA  NA  NA  NA   NA   NA             2628             1433
    ## 82   NA  NA  NA  NA  NA  NA  NA   NA   NA             5316             3221
    ## 83   NA  NA  NA  NA  NA  NA  NA   NA   NA             6922             3764
    ## 84   NA  NA  NA  NA  NA  NA  NA   NA   NA             5632             3396
    ## 85   NA  NA  NA  NA  NA  NA  NA   NA   NA             2951             1756
    ## 86   NA  NA  NA  NA  NA  NA  NA   NA   NA            13011             7488
    ## 87   NA  NA  NA  NA  NA  NA  NA   NA   NA             7146             4147
    ## 88   NA  NA  NA  NA  NA  NA  NA   NA   NA             1530              903
    ## 89   NA  NA  NA  NA  NA  NA  NA   NA   NA             1277              812
    ## 90   NA  NA  NA  NA  NA  NA  NA   NA   NA             2404             1449
    ## 91   NA  NA  NA  NA  NA  NA  NA   NA   NA             2358             1581
    ## 92   NA  NA  NA  NA  NA  NA  NA   NA   NA             1857             1220
    ## 93   NA  NA  NA  NA  NA  NA  NA   NA   NA             3165             2116
    ## 94   NA  NA  NA  NA  NA  NA  NA   NA   NA             3523             2301
    ## 95   NA  NA  NA  NA  NA  NA  NA   NA   NA             1365              729
    ## 96   NA  NA  NA  NA  NA  NA  NA   NA   NA             1848             1107
    ## 97   NA  NA  NA  NA  NA  NA  NA   NA   NA             1555              919
    ## 98   NA  NA  NA  NA  NA  NA  NA   NA   NA             1248              691
    ## 99   NA  NA  NA  NA  NA  NA  NA   NA   NA              675              386
    ## 100  NA  NA  NA  NA  NA  NA  NA   NA   NA             1673              975
    ## 101  NA  NA  NA  NA  NA  NA  NA   NA   NA              650              359
    ## 102  NA  NA  NA  NA  NA  NA  NA   NA   NA              991              600
    ## 103  NA  NA  NA  NA  NA  NA  NA   NA   NA              968              588
    ## 104  NA  NA  NA  NA  NA  NA  NA   NA   NA             2532             1567
    ## 105  NA  NA  NA  NA  NA  NA  NA   NA   NA             1919             1120
    ## 106  NA  NA  NA  NA  NA  NA  NA   NA   NA             2485             1386
    ## 107  NA  NA  NA  NA  NA  NA  NA   NA   NA             2057             1212
    ## 108  NA  NA  NA  NA  NA  NA  NA   NA   NA             3124             2075
    ## 109  NA  NA  NA  NA  NA  NA  NA   NA   NA             2767             1721
    ## 110  NA  NA  NA  NA  NA  NA  NA   NA   NA             2104             1277
    ## 111  NA  NA  NA  NA  NA  NA  NA   NA   NA             2061             1197
    ## 112  NA  NA  NA  NA  NA  NA  NA   NA   NA              257              180
    ## 113  NA  NA  NA  NA  NA  NA  NA   NA   NA             1319              769
    ## 114  NA  NA  NA  NA  NA  NA  NA   NA   NA             4362             2563
    ## 115  NA  NA  NA  NA  NA  NA  NA   NA   NA             3197             2005
    ## 116  NA  NA  NA  NA  NA  NA  NA   NA   NA             3396             2049
    ## 117  NA  NA  NA  NA  NA  NA  NA   NA   NA             1962             1161
    ## 118  NA  NA  NA  NA  NA  NA  NA   NA   NA             5160             3164
    ## 119  NA  NA  NA  NA  NA  NA  NA   NA   NA             3914             2355
    ## 120  NA  NA  NA  NA  NA  NA  NA   NA   NA             2709             1675
    ## 121  NA  NA  NA  NA  NA  NA  NA   NA   NA             6660             3659
    ## 122  NA  NA  NA  NA  NA  NA  NA   NA   NA             6508             3687
    ## 123  NA  NA  NA  NA  NA  NA  NA   NA   NA             8053             4591
    ## 124  NA  NA  NA  NA  NA  NA  NA   NA   NA             4847             2640
    ## 125  NA  NA  NA  NA  NA  NA  NA   NA   NA             5990             3120
    ## 126  NA  NA  NA  NA  NA  NA  NA   NA   NA             5308             3083
    ## 127  NA  NA  NA  NA  NA  NA  NA   NA   NA             1445              856
    ## 128  NA  NA  NA  NA  NA  NA  NA   NA   NA             2268             1359
    ## 129  NA  NA  NA  NA  NA  NA  NA   NA   NA             2575             1451
    ## 130  NA  NA  NA  NA  NA  NA  NA   NA   NA             2642             1596
    ## 131  NA  NA  NA  NA  NA  NA  NA   NA   NA             1967             1141
    ## 132  NA  NA  NA  NA  NA  NA  NA   NA   NA             4531             2734
    ## 133  NA  NA  NA  NA  NA  NA  NA   NA   NA             3545             2226
    ## 134  NA  NA  NA  NA  NA  NA  NA   NA   NA             2471             1427
    ## 135  NA  NA  NA  NA  NA  NA  NA   NA   NA             3761             2109
    ## 136  NA  NA  NA  NA  NA  NA  NA   NA   NA             3226             1840
    ## 137  NA  NA  NA  NA  NA  NA  NA   NA   NA             2439             1360
    ## 138  NA  NA  NA  NA  NA  NA  NA   NA   NA              838              890
    ## 139  NA  NA  NA  NA  NA  NA  NA   NA   NA             1060             1058
    ## 140  NA  NA  NA  NA  NA  NA  NA   NA   NA             2029             1913
    ## 141  NA  NA  NA  NA  NA  NA  NA   NA   NA             2004             1988
    ## 142  NA  NA  NA  NA  NA  NA  NA   NA   NA             1880             1801
    ## 143  NA  NA  NA  NA  NA  NA  NA   NA   NA             1239             1289
    ## 144  NA  NA  NA  NA  NA  NA  NA   NA   NA             1545             1479
    ## 145  NA  NA  NA  NA  NA  NA  NA   NA   NA              168              179
    ## 146  NA  NA  NA  NA  NA  NA  NA   NA   NA              126              134
    ## 147  NA  NA  NA  NA  NA  NA  NA   NA   NA              879              883
    ## 148  NA  NA  NA  NA  NA  NA  NA   NA   NA              603              557
    ## 149  NA  NA  NA  NA  NA  NA  NA   NA   NA             1504             1523
    ## 150  NA  NA  NA  NA  NA  NA  NA   NA   NA             1445             1437
    ## 151  NA  NA  NA  NA  NA  NA  NA   NA   NA              208              206
    ## 152  NA  NA  NA  NA  NA  NA  NA   NA   NA              328              304
    ## 153  NA  NA  NA  NA  NA  NA  NA   NA   NA             1101              976
    ## 154  NA  NA  NA  NA  NA  NA  NA   NA   NA             1119             1098
    ## 155  NA  NA  NA  NA  NA  NA  NA   NA   NA             2458             2321
    ## 156  NA  NA  NA  NA  NA  NA  NA   NA   NA             1826             1683
    ## 157  NA  NA  NA  NA  NA  NA  NA   NA   NA              727              656
    ## 158  NA  NA  NA  NA  NA  NA  NA   NA   NA             1296             1288
    ## 159  NA  NA  NA  NA  NA  NA  NA   NA   NA             2023             1910
    ## 160  NA  NA  NA  NA  NA  NA  NA   NA   NA             1398             1389
    ## 161  NA  NA  NA  NA  NA  NA  NA   NA   NA             2284             2160
    ## 162  NA  NA  NA  NA  NA  NA  NA   NA   NA             3168             2919
    ## 163  NA  NA  NA  NA  NA  NA  NA   NA   NA             1963             1894
    ## 164  NA  NA  NA  NA  NA  NA  NA   NA   NA             2300             2193
    ## 165  NA  NA  NA  NA  NA  NA  NA   NA   NA             2638             2396
    ## 166  NA  NA  NA  NA  NA  NA  NA   NA   NA             2770             2765
    ## 167  NA  NA  NA  NA  NA  NA  NA   NA   NA             2191             2109
    ## 168  NA  NA  NA  NA  NA  NA  NA   NA   NA             2266             2227
    ## 169  NA  NA  NA  NA  NA  NA  NA   NA   NA             2309             2266
    ## 170  NA  NA  NA  NA  NA  NA  NA   NA   NA             2316             2252
    ## 171  NA  NA  NA  NA  NA  NA  NA   NA   NA             2700             2678
    ## 172  NA  NA  NA  NA  NA  NA  NA   NA   NA             1823             1852
    ## 173  NA  NA  NA  NA  NA  NA  NA   NA   NA             2261             2436
    ## 174  NA  NA  NA  NA  NA  NA  NA   NA   NA             1145             1165
    ## 175  NA  NA  NA  NA  NA  NA  NA   NA   NA             1387             1331
    ## 176  NA  NA  NA  NA  NA  NA  NA   NA   NA              116              127
    ## 177  NA  NA  NA  NA  NA  NA  NA   NA   NA              423              442
    ## 178  NA  NA  NA  NA  NA  NA  NA   NA   NA              706              660
    ## 179  NA  NA  NA  NA  NA  NA  NA   NA   NA              178              188
    ## 180  NA  NA  NA  NA  NA  NA  NA   NA   NA              274              272
    ## 181  NA  NA  NA  NA  NA  NA  NA   NA   NA              176              192
    ## 182  NA  NA  NA  NA  NA  NA  NA   NA   NA              256              295
    ## 183  NA  NA  NA  NA  NA  NA  NA   NA   NA              621              562
    ## 184  NA  NA  NA  NA  NA  NA  NA   NA   NA             2056             2108
    ## 185  NA  NA  NA  NA  NA  NA  NA   NA   NA             1907             1758
    ## 186  NA  NA  NA  NA  NA  NA  NA   NA   NA             1026             1049
    ## 187  NA  NA  NA  NA  NA  NA  NA   NA   NA             2300             2242
    ## 188  NA  NA  NA  NA  NA  NA  NA   NA   NA              990              985
    ## 189  NA  NA  NA  NA  NA  NA  NA   NA   NA             1540             1460
    ## 190  NA  NA  NA  NA  NA  NA  NA   NA   NA             1140             1041
    ## 191  NA  NA  NA  NA  NA  NA  NA   NA   NA              698              595
    ## 192  NA  NA  NA  NA  NA  NA  NA   NA   NA             3050             2964
    ## 193  NA  NA  NA  NA  NA  NA  NA   NA   NA             2783             2874
    ## 194  NA  NA  NA  NA  NA  NA  NA   NA   NA             1859             1817
    ## 195  NA  NA  NA  NA  NA  NA  NA   NA   NA             2617             2596
    ## 196  NA  NA  NA  NA  NA  NA  NA   NA   NA             2017             2022
    ## 197  NA  NA  NA  NA  NA  NA  NA   NA   NA             1708             1774
    ## 198  NA  NA  NA  NA  NA  NA  NA   NA   NA             1499             1484
    ## 199  NA  NA  NA  NA  NA  NA  NA   NA   NA             2675             2616
    ## 200  NA  NA  NA  NA  NA  NA  NA   NA   NA             2787             2791
    ## 201  NA  NA  NA  NA  NA  NA  NA   NA   NA             1836             1727
    ## 202  NA  NA  NA  NA  NA  NA  NA   NA   NA             2304             2186
    ## 203  NA  NA  NA  NA  NA  NA  NA   NA   NA             1759             1638
    ## 204  NA  NA  NA  NA  NA  NA  NA   NA   NA             1606             1542
    ## 205  NA  NA  NA  NA  NA  NA  NA   NA   NA             1377             1336
    ## 206  NA  NA  NA  NA  NA  NA  NA   NA   NA             1101             1061
    ## 207  NA  NA  NA  NA  NA  NA  NA   NA   NA              840              873
    ## 208  NA  NA  NA  NA  NA  NA  NA   NA   NA             1820             1810
    ## 209  NA  NA  NA  NA  NA  NA  NA   NA   NA             1998             1836
    ## 210  NA  NA  NA  NA  NA  NA  NA   NA   NA             2249             2200
    ## 211  NA  NA  NA  NA  NA  NA  NA   NA   NA             2192             2124
    ## 212  NA  NA  NA  NA  NA  NA  NA   NA   NA             1278             1190
    ## 213  NA  NA  NA  NA  NA  NA  NA   NA   NA             2054             2057
    ## 214  NA  NA  NA  NA  NA  NA  NA   NA   NA             2361             2418
    ## 215  NA  NA  NA  NA  NA  NA  NA   NA   NA             1764             1797
    ## 216  NA  NA  NA  NA  NA  NA  NA   NA   NA             1361             1154
    ## 217  NA  NA  NA  NA  NA  NA  NA   NA   NA             2105             2064
    ## 218  NA  NA  NA  NA  NA  NA  NA   NA   NA              444              466
    ## 219  NA  NA  NA  NA  NA  NA  NA   NA   NA             1131             1008
    ## 220  NA  NA  NA  NA  NA  NA  NA   NA   NA             1614             1758
    ## 221  NA  NA  NA  NA  NA  NA  NA   NA   NA             3063             2953
    ## 222  NA  NA  NA  NA  NA  NA  NA   NA   NA             1875             1682
    ## 223  NA  NA  NA  NA  NA  NA  NA   NA   NA             2704             2409
    ## 224  NA  NA  NA  NA  NA  NA  NA   NA   NA             1946             1799
    ## 225  NA  NA  NA  NA  NA  NA  NA   NA   NA             2224             2135
    ## 226  NA  NA  NA  NA  NA  NA  NA   NA   NA             1277             1210
    ## 227  NA  NA  NA  NA  NA  NA  NA   NA   NA             2480             2417
    ## 228  NA  NA  NA  NA  NA  NA  NA   NA   NA             1413             1425
    ## 229  NA  NA  NA  NA  NA  NA  NA   NA   NA             2265             2141
    ## 230  NA  NA  NA  NA  NA  NA  NA   NA   NA             1942             1800
    ## 231  NA  NA  NA  NA  NA  NA  NA   NA   NA             1823             1804
    ## 232  NA  NA  NA  NA  NA  NA  NA   NA   NA             1678             1341
    ## 233  NA  NA  NA  NA  NA  NA  NA   NA   NA             2107             1998
    ## 234  NA  NA  NA  NA  NA  NA  NA   NA   NA             2006             1951
    ## 235  NA  NA  NA  NA  NA  NA  NA   NA   NA             2139             2060
    ## 236  NA  NA  NA  NA  NA  NA  NA   NA   NA             5035             4775
    ## 237  NA  NA  NA  NA  NA  NA  NA   NA   NA             1565             1417
    ## 238  NA  NA  NA  NA  NA  NA  NA   NA   NA             4651             4385
    ## 239  NA  NA  NA  NA  NA  NA  NA   NA   NA             3053             2953
    ## 240  NA  NA  NA  NA  NA  NA  NA   NA   NA             4162             4030
    ## 241  NA  NA  NA  NA  NA  NA  NA   NA   NA             1420             1441
    ## 242  NA  NA  NA  NA  NA  NA  NA   NA   NA             3285             3275
    ## 243  NA  NA  NA  NA  NA  NA  NA   NA   NA             3210             3055
    ## 244  NA  NA  NA  NA  NA  NA  NA   NA   NA             3427             3122
    ## 245  NA  NA  NA  NA  NA  NA  NA   NA   NA             3896             3569
    ## 246  NA  NA  NA  NA  NA  NA  NA   NA   NA             3467             3356
    ## 247  NA  NA  NA  NA  NA  NA  NA   NA   NA             1682             1703
    ## 248  NA  NA  NA  NA  NA  NA  NA   NA   NA             1949             1984
    ## 249  NA  NA  NA  NA  NA  NA  NA   NA   NA             1611             1604
    ## 250  NA  NA  NA  NA  NA  NA  NA   NA   NA             1888             1815
    ## 251  NA  NA  NA  NA  NA  NA  NA   NA   NA             1299             1284
    ## 252  NA  NA  NA  NA  NA  NA  NA   NA   NA             2689             2502
    ## 253  NA  NA  NA  NA  NA  NA  NA   NA   NA             1479             1576
    ## 254  NA  NA  NA  NA  NA  NA  NA   NA   NA             2208             2104
    ## 255  NA  NA  NA  NA  NA  NA  NA   NA   NA             3179             3085
    ## 256  NA  NA  NA  NA  NA  NA  NA   NA   NA             3311             3175
    ## 257  NA  NA  NA  NA  NA  NA  NA   NA   NA             2185             2177
    ## 258  NA  NA  NA  NA  NA  NA  NA   NA   NA             1988             1846
    ## 259  NA  NA  NA  NA  NA  NA  NA   NA   NA             1857             1849
    ## 260  NA  NA  NA  NA  NA  NA  NA   NA   NA             1241             1172
    ## 261  NA  NA  NA  NA  NA  NA  NA   NA   NA             1237             1276
    ## 262  NA  NA  NA  NA  NA  NA  NA   NA   NA             1088             1064
    ## 263  NA  NA  NA  NA  NA  NA  NA   NA   NA             1167             1112
    ## 264  NA  NA  NA  NA  NA  NA  NA   NA   NA              937              928
    ## 265  NA  NA  NA  NA  NA  NA  NA   NA   NA             1242             1187
    ## 266  NA  NA  NA  NA  NA  NA  NA   NA   NA             3258             2988
    ## 267  NA  NA  NA  NA  NA  NA  NA   NA   NA             1007              930
    ##     X40.44.Laki.Laki X40.44.Perempuan X45.49.Laki.Laki X45.49.Perempuan
    ## 1                233              210              171              158
    ## 2                 99               88               72               63
    ## 3                232              234              212              193
    ## 4                178              176              162              139
    ## 5                 73               94               67               69
    ## 6                108               80               66               62
    ## 7                130              165              176              162
    ## 8                749              798              779              766
    ## 9                914              943              871              823
    ## 10               691              691              659              631
    ## 11               447              522              463              487
    ## 12              1105             1083             1007              967
    ## 13               595              606              607              580
    ## 14              1371             1381             1236             1160
    ## 15              1172             1153             1089             1011
    ## 16               854              847              900              808
    ## 17              1481             1459             1257             1284
    ## 18              1013             1026              921              956
    ## 19              1397             1415             1331             1168
    ## 20              1204             1222             1144              989
    ## 21              1605             1721             1640             1460
    ## 22               973             1016              954              903
    ## 23              1838             1881             1694             1435
    ## 24              1305             1226             1202              940
    ## 25              1462             1442             1299             1276
    ## 26               362              315              302              278
    ## 27               442              446              449              413
    ## 28              1089             1146             1088             1087
    ## 29              1391             1437             1270             1280
    ## 30               790              727              648              667
    ## 31               903              937              860              825
    ## 32              1364             1280             1287             1189
    ## 33              1879             1891             1815             1609
    ## 34              1207             1085             1149             1037
    ## 35              1215             1153             1164             1048
    ## 36              1099             1139             1095             1051
    ## 37               408              367              409              376
    ## 38               212              180              187              179
    ## 39               657              701              618              560
    ## 40               178              190              185              158
    ## 41              1088             1198             1200             1104
    ## 42              1020             1027              916              839
    ## 43              1660             1626             1446             1404
    ## 44              1588             1673             1462             1433
    ## 45               998             1064             1040              987
    ## 46               600              589              563              566
    ## 47              1949             1952             1847             1569
    ## 48              1139             1181              972              892
    ## 49               925              982              820              795
    ## 50              1776             1841             1680             1594
    ## 51              5124            10659             6563             5925
    ## 52               572             1089              655              666
    ## 53              1635             3266             1860             1851
    ## 54              4453             8921             5122             4877
    ## 55              2303             4567             2542             2581
    ## 56              1872             3897             2391             2325
    ## 57              3355             6782             3967             3810
    ## 58              2036             4326             2502             2417
    ## 59              1561             3310             1924             1805
    ## 60              2661             5670             3519             3270
    ## 61              3810             7520             4177             4217
    ## 62              2342             4950             2968             2790
    ## 63              1635             3402             1995             1784
    ## 64              3748             7702             4373             4297
    ## 65              3123             6465             3553             3456
    ## 66              1867             3931             2296             2231
    ## 67              2093             4328             2494             2393
    ## 68              2294             4714             2626             2681
    ## 69              2523             5137             2976             2968
    ## 70              3696             7072             4293             5339
    ## 71              1121             2328             1312             1288
    ## 72              3833             7929             4572             4522
    ## 73              1668             3351             1992             2151
    ## 74              1934             3810             2204             2307
    ## 75              3703             7282             4317             4495
    ## 76              1948             3883             2238             2238
    ## 77              4133             8397             5086             4635
    ## 78              1354             2734             1674             1475
    ## 79              1743             3487             1893             2144
    ## 80              2338             4597             2608             2622
    ## 81              1605             3038             1821             1946
    ## 82              3137             6358             3675             3768
    ## 83              3746             7510             4224             4231
    ## 84              3459             6855             3950             3971
    ## 85              1683             3439             2104             1995
    ## 86              7243            14731             8822             8352
    ## 87              4130             8277             5010             4952
    ## 88               845             1748             1002              989
    ## 89               859             1671             1074             1199
    ## 90              1365             2814             1662             1633
    ## 91              1524             3105             1854             1883
    ## 92              1210             2430             1638             1637
    ## 93              2065             4181             2552             2503
    ## 94              2116             4417             2704             2529
    ## 95               775             1504              853              810
    ## 96               990             2097             1150             1063
    ## 97               891             1810              979              973
    ## 98               798             1489              806              809
    ## 99               404              790              409              434
    ## 100              932             1907             1117             1017
    ## 101              368              727              407              392
    ## 102              612             1212              773              672
    ## 103              544             1132              646              593
    ## 104             1530             3097             1775             1554
    ## 105             1095             2215             1220             1193
    ## 106             1388             2774             1536             1382
    ## 107             1161             2373             1307             1186
    ## 108             1879             3954             2275             1907
    ## 109             1579             3300             1936             1707
    ## 110             1129             2406             1371             1257
    ## 111             1167             2364             1258             1315
    ## 112              150              330              199              194
    ## 113              780             1549              850              863
    ## 114             2466             5029             2878             3001
    ## 115             1899             3904             2223             2242
    ## 116             2002             4051             2340             2242
    ## 117             1124             2285             1337             1357
    ## 118             3253             6417             3809             3580
    ## 119             2363             4718             2776             2721
    ## 120             1697             3372             1962             1961
    ## 121             3562             7221             4222             4118
    ## 122             3587             7274             4380             4400
    ## 123             4553             9144             5652             5470
    ## 124             2571             5211             3018             2971
    ## 125             3271             6391             3847             3916
    ## 126             3081             6164             3752             3624
    ## 127              852             1708             1043              951
    ## 128             1372             2731             1592             1523
    ## 129             1438             2889             1767             1695
    ## 130             1580             3176             1790             1845
    ## 131             1067             2208             1337             1282
    ## 132             2793             5527             3092             2903
    ## 133             2193             4419             2633             2619
    ## 134             1501             2928             1605             1701
    ## 135             2109             4218             2364             2404
    ## 136             1955             3795             2308             2369
    ## 137             1418             2778             1401             1509
    ## 138              948             1004              911              943
    ## 139             1086             1159             1093             1024
    ## 140             1958             1841             1623             1572
    ## 141             1901             1774             1470             1347
    ## 142             1805             1712             1598             1553
    ## 143             1238             1198             1080             1007
    ## 144             1483             1402             1346             1267
    ## 145              147              170              156              153
    ## 146              144              132              103              100
    ## 147              794              751              688              654
    ## 148              599              593              555              467
    ## 149             1505             1442             1206             1160
    ## 150             1354             1246             1168             1088
    ## 151              186              192              181              205
    ## 152              337              326              272              231
    ## 153              979              935              814              692
    ## 154             1068             1020              951              905
    ## 155             2366             2152             1935             1795
    ## 156             1614             1449             1333             1161
    ## 157              713              611              622              479
    ## 158             1198             1269             1087             1026
    ## 159             1770             1715             1393             1392
    ## 160             1261             1142             1011              879
    ## 161             2011             1854             1614             1556
    ## 162             2848             2685             2317             2103
    ## 163             1825             1711             1575             1479
    ## 164             1928             1808             1576             1454
    ## 165             2289             2012             1782             1574
    ## 166             2649             2499             2134             2134
    ## 167             2020             1873             1630             1455
    ## 168             2187             2071             1837             1727
    ## 169             2229             2124             1886             1692
    ## 170             2193             2004             1726             1529
    ## 171             2716             2641             2300             2156
    ## 172             1719             1632             1404             1307
    ## 173             2254             2130             1888             1657
    ## 174             1105             1070              963              880
    ## 175             1334             1333             1205             1145
    ## 176              120              133              148              139
    ## 177              441              470              498              445
    ## 178              616              672              670              603
    ## 179              181              195              193              189
    ## 180              261              273              291              317
    ## 181              224              195              173              164
    ## 182              289              305              267              322
    ## 183              655              560              561              494
    ## 184             2081             2038             1812             1699
    ## 185             1732             1607             1476             1257
    ## 186              959              856              730              672
    ## 187             2234             1934             1647             1554
    ## 188              970              902              786              683
    ## 189             1497             1434             1265             1120
    ## 190             1046             1020              880              842
    ## 191              578              544              450              427
    ## 192             2724             2626             2218             2013
    ## 193             2710             2587             2227             2034
    ## 194             1690             1528             1353             1171
    ## 195             2339             2219             1885             1849
    ## 196             1826             1683             1433             1315
    ## 197             1567             1468             1302             1123
    ## 198             1270             1232             1032              941
    ## 199             2525             2311             2078             1792
    ## 200             2451             2240             1926             1783
    ## 201             1584             1526             1297             1244
    ## 202             2047             1826             1533             1377
    ## 203             1662             1583             1434             1393
    ## 204             1572             1418             1290             1185
    ## 205             1271             1337             1173             1144
    ## 206             1061             1001              934              879
    ## 207              928              862              822              836
    ## 208             1727             1699             1523             1475
    ## 209             1788             1596             1477             1338
    ## 210             2193             2063             1834             1771
    ## 211             2129             2151             1745             1747
    ## 212             1205             1141              970              859
    ## 213             2049             1984             1746             1660
    ## 214             2245             2253             1810             1760
    ## 215             1826             1725             1375             1436
    ## 216             1236             1050             1016             1029
    ## 217             1952             1824             1727             1629
    ## 218              462              458              486              480
    ## 219             1034             1021              903              842
    ## 220             1704             1670             1567             1559
    ## 221             2693             2469             1999             1951
    ## 222             1649             1556             1303             1218
    ## 223             2344             2180             1856             1784
    ## 224             1742             1601             1411             1435
    ## 225             1986             1780             1718             1673
    ## 226             1109             1036              891              861
    ## 227             2223             2125             1760             1657
    ## 228             1292             1260             1036              974
    ## 229             2053             1910             1658             1658
    ## 230             1760             1586             1415             1289
    ## 231             1648             1652             1440             1248
    ## 232             1200             1042              738              860
    ## 233             1826             1835             1566             1525
    ## 234             1859             1767             1512             1583
    ## 235             1854             1753             1538             1465
    ## 236             4480             3883             3304             2804
    ## 237             1394             1136             1021              857
    ## 238             4106             3805             3289             2953
    ## 239             2637             2422             2014             1851
    ## 240             3755             3600             3011             2968
    ## 241             1345             1289             1084             1000
    ## 242             2790             2455             1908             1592
    ## 243             2723             2620             2119             2138
    ## 244             2932             2734             2276             2074
    ## 245             3349             2950             2538             2463
    ## 246             3037             2894             2376             2331
    ## 247             1542             1493             1124             1074
    ## 248             1854             1714             1270             1162
    ## 249             1461             1433             1220             1255
    ## 250             1576             1522             1286             1276
    ## 251             1168             1141              974              901
    ## 252             2296             2192             1870             1659
    ## 253             1705             1630             1327             1312
    ## 254             2035             1876             1652             1693
    ## 255             2851             2785             2423             2358
    ## 256             2982             2861             2471             2424
    ## 257             1927             1818             1586             1559
    ## 258             1807             1564             1493             1286
    ## 259             1729             1567             1369             1277
    ## 260             1029             1037              961              894
    ## 261             1195             1114              978              900
    ## 262              969              945              920              846
    ## 263             1026              977              839              800
    ## 264              857              824              705              640
    ## 265             1062             1063              984              917
    ## 266             2732             2660             2311             2222
    ## 267              874              804              701              652
    ##     X50.54.Laki.Laki X50.54.Perempuan X55.59.Laki.Laki X55.59.Perempuan
    ## 1                137              126               98              106
    ## 2                 34               29               30               39
    ## 3                150              161              139              101
    ## 4                100              119               97               83
    ## 5                 60               40               37               32
    ## 6                 61               63               37               36
    ## 7                129               97              108               90
    ## 8                715              662              614              537
    ## 9                736              679              680              510
    ## 10               611              514              539              466
    ## 11               432              426              432              329
    ## 12               901              781              742              616
    ## 13               588              522              495              435
    ## 14              1078              995              935              749
    ## 15               993              905              877              688
    ## 16               804              691              648              525
    ## 17              1120             1033              969              799
    ## 18               845              787              696              601
    ## 19              1049              857              837              650
    ## 20               871              743              737              584
    ## 21              1301              922              901              627
    ## 22               855              726              717              602
    ## 23              1349             1021              983              755
    ## 24               860              710              689              549
    ## 25              1163              920              912              731
    ## 26               274              254              224              207
    ## 27               446              360              339              288
    ## 28              1074              831              914              697
    ## 29              1193              957              949              777
    ## 30               641              513              587              459
    ## 31               810              667              661              517
    ## 32              1064              791              798              565
    ## 33              1445             1108             1168              857
    ## 34               984              746              765              551
    ## 35              1103              973             1011              786
    ## 36              1043              843              858              681
    ## 37               375              315              335              264
    ## 38               194              175              180              134
    ## 39               508              493              451              394
    ## 40               143              113              111               85
    ## 41              1084              883              841              593
    ## 42               660              573              554              484
    ## 43              1289             1148             1012              811
    ## 44              1289             1017              985              864
    ## 45               903              806              836              627
    ## 46               536              465              448              380
    ## 47              1528             1179             1175              922
    ## 48               830              663              663              547
    ## 49               727              621              535              436
    ## 50              1437             1263             1200              954
    ## 51             12488             5758             4842            10600
    ## 52              1321              533              541             1074
    ## 53              3711             1545             1453             2998
    ## 54              9999             4333             4018             8351
    ## 55              5123             2169             2132             4301
    ## 56              4716             2238             2324             4562
    ## 57              7777             3329             3023             6352
    ## 58              4919             2270             2230             4500
    ## 59              3729             1694             1628             3322
    ## 60              6789             3264             2955             6219
    ## 61              8394             3982             3799             7781
    ## 62              5758             2738             2664             5402
    ## 63              3779             1744             1476             3220
    ## 64              8670             3892             3740             7632
    ## 65              7009             3205             2994             6199
    ## 66              4527             2095             1898             3993
    ## 67              4887             1992             1989             3981
    ## 68              5307             2239             2110             4349
    ## 69              5944             2464             2316             4780
    ## 70              9632             3595             3572             7167
    ## 71              2600             1024              977             2001
    ## 72              9094             3847             3734             7581
    ## 73              4143             1894             1964             3858
    ## 74              4511             1866             1887             3753
    ## 75              8812             3826             3776             7602
    ## 76              4476             2045             2014             4059
    ## 77              9721             4374             3828             8202
    ## 78              3149             1442             1248             2690
    ## 79              4037             1657             1707             3364
    ## 80              5230             2281             2347             4628
    ## 81              3767             1788             1828             3616
    ## 82              7443             3431             3430             6861
    ## 83              8455             3698             3448             7146
    ## 84              7921             3496             3128             6624
    ## 85              4099             1956             1795             3751
    ## 86             17174             7480             6846            14326
    ## 87              9962             4345             3961             8306
    ## 88              1991              936              875             1811
    ## 89              2273             1030              997             2027
    ## 90              3295             1583             1589             3172
    ## 91              3737             1706             1696             3402
    ## 92              3275             1413             1447             2860
    ## 93              5055             2188             2123             4311
    ## 94              5233             2242             2004             4246
    ## 95              1663              737              740             1477
    ## 96              2213             1008              924             1932
    ## 97              1952              875              873             1748
    ## 98              1615              718              734             1452
    ## 99               843              386              373              759
    ## 100             2134             1030              910             1940
    ## 101              799              335              342              677
    ## 102             1445              626              586             1212
    ## 103             1239              598              522             1120
    ## 104             3329             1549             1275             2824
    ## 105             2413             1125             1016             2141
    ## 106             2918             1344             1271             2615
    ## 107             2493             1210              940             2150
    ## 108             4182             1966             1496             3462
    ## 109             3643             1651             1460             3111
    ## 110             2628             1211             1053             2264
    ## 111             2573             1221             1140             2361
    ## 112              393              179              191              370
    ## 113             1713              770              724             1494
    ## 114             5879             2739             2662             5401
    ## 115             4465             2026             1978             4004
    ## 116             4582             2094             1884             3978
    ## 117             2694             1256             1232             2488
    ## 118             7389             3204             3040             6244
    ## 119             5497             2372             2247             4619
    ## 120             3923             1696             1660             3356
    ## 121             8340             3733             3684             7417
    ## 122             8780             3925             3656             7581
    ## 123            11122             4531             4325             8856
    ## 124             5989             2585             2455             5040
    ## 125             7763             3372             3369             6741
    ## 126             7376             3447             3319             6766
    ## 127             1994              875              840             1715
    ## 128             3115             1361             1221             2582
    ## 129             3462             1531             1428             2959
    ## 130             3635             1766             1721             3487
    ## 131             2619             1188             1135             2323
    ## 132             5995             2763             2693             5456
    ## 133             5252             2156             2142             4298
    ## 134             3306             1535             1484             3019
    ## 135             4768             2270             2224             4494
    ## 136             4677             1988             1951             3939
    ## 137             2910             1306             1165             2471
    ## 138              713              728              532              514
    ## 139              837              851              536              610
    ## 140             1216             1205              884              853
    ## 141             1087             1134              839              935
    ## 142             1305             1258              982             1002
    ## 143              790              757              607              634
    ## 144              999             1039              823              828
    ## 145              115              117               84               74
    ## 146               83               94               79               65
    ## 147              548              567              444              427
    ## 148              364              346              288              262
    ## 149              967              948              664              728
    ## 150              921              893              682              725
    ## 151              168              152              140              157
    ## 152              212              190              161              133
    ## 153              582              589              420              396
    ## 154              719              713              566              469
    ## 155             1440             1422             1089             1042
    ## 156              984              897              694              677
    ## 157              426              390              318              286
    ## 158              791              783              542              548
    ## 159             1135             1168              819              852
    ## 160              716              696              516              461
    ## 161             1111             1195              882              902
    ## 162             1687             1686             1213             1250
    ## 163             1150             1141              829              888
    ## 164             1186             1242              914              899
    ## 165             1355             1299              957              979
    ## 166             1699             1756             1296             1445
    ## 167             1211             1197              909              821
    ## 168             1416             1293             1018              889
    ## 169             1471             1313             1056             1013
    ## 170             1254             1303              941              942
    ## 171             1706             1631             1230             1256
    ## 172             1108             1211              872              855
    ## 173             1286             1266              935              943
    ## 174              775              686              495              470
    ## 175              986              913              612              589
    ## 176              134              119              100              106
    ## 177              360              324              288              283
    ## 178              523              476              391              375
    ## 179              162              154              104              120
    ## 180              249              265              181              196
    ## 181              156              128              109              104
    ## 182              272              291              220              214
    ## 183              448              411              342              324
    ## 184             1344             1192             1012             1042
    ## 185             1075              995              754              683
    ## 186              519              546              450              470
    ## 187             1152             1188              893              954
    ## 188              517              527              400              439
    ## 189              926              862              646              563
    ## 190              661              659              478              484
    ## 191              346              372              259              272
    ## 192             1675             1695             1273             1249
    ## 193             1515             1460             1107             1139
    ## 194              967              919              730              647
    ## 195             1452             1478             1127             1191
    ## 196             1072             1107              802              824
    ## 197              966              927              750              656
    ## 198              684              672              540              611
    ## 199             1516             1440             1094             1135
    ## 200             1405             1436             1151             1267
    ## 201             1055             1048              844              858
    ## 202             1181             1146              840              848
    ## 203             1149             1074              837              848
    ## 204              981              938              717              711
    ## 205              868              899              676              690
    ## 206              790              722              577              563
    ## 207              676              661              471              498
    ## 208             1192             1185              864              870
    ## 209             1143             1019              748              703
    ## 210             1467             1357             1032             1066
    ## 211             1384             1321              948              929
    ## 212              780              712              522              503
    ## 213             1231             1250              941              946
    ## 214             1273             1270              923             1015
    ## 215             1112             1045              789              860
    ## 216              864              848              694              601
    ## 217             1328             1325              974             1048
    ## 218              446              374              333              347
    ## 219              716              730              619              604
    ## 220             1200             1253              934              963
    ## 221             1642             1721             1362             1454
    ## 222              988              952              782              780
    ## 223             1480             1463             1170             1126
    ## 224             1146             1105              848              811
    ## 225             1303             1267              922              957
    ## 226              720              682              518              576
    ## 227             1284             1295             1019             1041
    ## 228              766              763              677              609
    ## 229             1273             1265              983             1026
    ## 230             1085             1146              858              794
    ## 231             1085             1068              761              810
    ## 232              769              582              443              389
    ## 233             1226             1190              947              967
    ## 234             1295             1311             1075              811
    ## 235             1213             1204             1017              916
    ## 236             2324             2110             1561             1288
    ## 237              776              680              595              438
    ## 238             2397             2565             2063             1920
    ## 239             1485             1504             1252             1129
    ## 240             2454             2595             2134             1992
    ## 241              842              804              631              586
    ## 242             1242             1142              917              821
    ## 243             1718             1726             1383             1480
    ## 244             1757             1711             1338             1560
    ## 245             1946             1965             1636             1620
    ## 246             1867             2106             1690             1783
    ## 247              747              874              647              847
    ## 248              784              899              611              840
    ## 249              976             1021              868              907
    ## 250             1036             1109              866              879
    ## 251              698              713              588              530
    ## 252             1396             1373             1017             1108
    ## 253             1088              872              642              461
    ## 254             1323             1423             1106             1095
    ## 255             1934             1939             1468             1511
    ## 256             1915             1947             1497             1564
    ## 257             1216             1408             1149             1152
    ## 258             1074             1067              828              816
    ## 259             1087              989              782              807
    ## 260              696              702              539              469
    ## 261              676              587              452              397
    ## 262              713              607              453              391
    ## 263              668              622              482              482
    ## 264              512              471              392              354
    ## 265              731              841              596              476
    ## 266             1766             1788             1376             1308
    ## 267              493              503              416              390
    ##     X60.64.Laki.Laki X60.64.Perempuan X65.69.Laki.Laki X65.69.Perempuan
    ## 1                 72               65               36               33
    ## 2                 29               24               12               21
    ## 3                 73               56               18               35
    ## 4                 58               56               40               54
    ## 5                 22               13               18               15
    ## 6                 32               26               21               14
    ## 7                 88               42               68               34
    ## 8                555              343              413              215
    ## 9                544              421              398              235
    ## 10               428              279              328              160
    ## 11               353              263              246              140
    ## 12               597              404              409              215
    ## 13               486              401              407              265
    ## 14               793              487              567              308
    ## 15               743              515              542              272
    ## 16               539              388              458              240
    ## 17               729              528              498              310
    ## 18               608              410              414              191
    ## 19               685              448              448              271
    ## 20               619              346              365              218
    ## 21               650              418              521              279
    ## 22               585              396              460              282
    ## 23               770              498              571              318
    ## 24               636              383              465              279
    ## 25               719              424              395              197
    ## 26               184              152              126               84
    ## 27               271              191              200               96
    ## 28               666              436              428              203
    ## 29               760              483              479              272
    ## 30               459              310              371              157
    ## 31               572              382              357              210
    ## 32               638              457              474              254
    ## 33               874              569              592              294
    ## 34               552              376              373              216
    ## 35               749              448              453              268
    ## 36               657              457              419              220
    ## 37               256              167              185               85
    ## 38               163               82              125               79
    ## 39               383              251              253              136
    ## 40                88               63               49               33
    ## 41               559              358              385              198
    ## 42               410              286              281              175
    ## 43               736              420              425              242
    ## 44               761              493              467              260
    ## 45               647              450              485              256
    ## 46               376              245              274              140
    ## 47               939              590              670              318
    ## 48               495              300              339              176
    ## 49               421              259              257              139
    ## 50               955              646              627              309
    ## 51              4938             4051             8989             3967
    ## 52               482              474              956              354
    ## 53              1359             1273             2632             1102
    ## 54              3647             3306             6953             3023
    ## 55              1712             1746             3458             1380
    ## 56              1957             1832             3789             1508
    ## 57              2702             2408             5110             2213
    ## 58              1944             1704             3648             1467
    ## 59              1592             1401             2993             1267
    ## 60              2815             2607             5422             2193
    ## 61              3272             3124             6396             2722
    ## 62              2338             2234             4572             1858
    ## 63              1424             1329             2753             1256
    ## 64              3301             3007             6308             2420
    ## 65              2869             2667             5536             2410
    ## 66              1829             1643             3472             1398
    ## 67              1681             1538             3219             1289
    ## 68              1925             1641             3566             1423
    ## 69              2021             1793             3814             1515
    ## 70              2693             2184             4877             1606
    ## 71               926              891             1817              703
    ## 72              3196             2750             5946             2398
    ## 73              1786             1685             3471             1383
    ## 74              1623             1482             3105             1206
    ## 75              3344             3201             6545             2439
    ## 76              1806             1687             3493             1549
    ## 77              3702             3195             6897             2906
    ## 78              1286             1048             2334             1034
    ## 79              1307             1458             2765             1122
    ## 80              2052             1973             4025             1873
    ## 81              1810             1807             3617             1428
    ## 82              3040             2816             5856             2320
    ## 83              3221             2989             6210             2630
    ## 84              3004             2691             5695             2235
    ## 85              1719             1553             3272             1411
    ## 86              6333             5476            11809             4758
    ## 87              3736             3428             7164             2806
    ## 88               983              842             1825              837
    ## 89               843              806             1649              609
    ## 90              1594             1456             3050             1367
    ## 91              1570             1484             3054             1280
    ## 92              1268             1244             2512             1012
    ## 93              1860             1671             3531             1438
    ## 94              1908             1611             3519             1537
    ## 95               729              699             1428              633
    ## 96               914              871             1785              836
    ## 97               861              738             1599              785
    ## 98               651              682             1333              605
    ## 99               335              335              670              322
    ## 100              941              778             1719              817
    ## 101              318              344              662              335
    ## 102              601              494             1095              489
    ## 103              544              451              995              460
    ## 104             1251             1022             2273             1035
    ## 105              995              910             1905              903
    ## 106             1270             1189             2459             1126
    ## 107             1103              802             1905              856
    ## 108             1675             1248             2923             1265
    ## 109             1505             1371             2876             1332
    ## 110             1103              906             2009              887
    ## 111             1118             1088             2206              998
    ## 112              170              169              339              162
    ## 113              744              688             1432              630
    ## 114             2435             2345             4780             1923
    ## 115             1932             1647             3579             1370
    ## 116             1798             1596             3394             1370
    ## 117             1107             1055             2162              962
    ## 118             2616             2510             5126             2114
    ## 119             2021             1903             3924             1653
    ## 120             1459             1296             2755             1086
    ## 121             3432             3175             6607             2636
    ## 122             3374             3051             6425             2513
    ## 123             3806             3460             7266             2946
    ## 124             2384             2098             4482             1732
    ## 125             3229             3207             6436             2735
    ## 126             3187             2912             6099             2571
    ## 127              825              743             1568              677
    ## 128             1228             1076             2304              974
    ## 129             1442             1366             2808             1247
    ## 130             1783             1694             3477             1539
    ## 131             1095              974             2069              917
    ## 132             2440             2192             4632             1919
    ## 133             2010             1730             3740             1496
    ## 134             1380             1270             2650             1056
    ## 135             1946             1782             3728             1576
    ## 136             1772             1646             3418             1427
    ## 137             1098             1028             2126              940
    ## 138              342              367              198              301
    ## 139              431              453              230              312
    ## 140              614              629              314              378
    ## 141              619              648              375              441
    ## 142              670              654              348              421
    ## 143              361              414              212              288
    ## 144              538              508              297              298
    ## 145               59               54               23               43
    ## 146               46               59               34               34
    ## 147              295              238              119              137
    ## 148              145              199              107              130
    ## 149              440              470              247              331
    ## 150              479              444              236              248
    ## 151              114              115               62               78
    ## 152               98               98               58               71
    ## 153              276              241              157              193
    ## 154              288              250              151              178
    ## 155              694              676              408              422
    ## 156              448              439              232              275
    ## 157              212              211              126              102
    ## 158              375              467              279              365
    ## 159              609              588              317              352
    ## 160              290              333              189              201
    ## 161              597              613              381              383
    ## 162              883              783              453              512
    ## 163              562              548              357              373
    ## 164              588              492              318              272
    ## 165              720              662              423              399
    ## 166              989             1023              667              655
    ## 167              565              587              357              395
    ## 168              655              630              372              427
    ## 169              641              638              361              418
    ## 170              697              717              437              509
    ## 171              825              843              498              528
    ## 172              657              580              360              330
    ## 173              668              613              395              517
    ## 174              310              309              180              216
    ## 175              403              365              240              277
    ## 176               74               64               37               43
    ## 177              175              173              120              121
    ## 178              246              227              133              137
    ## 179               82               91               45               51
    ## 180              120              149               83               87
    ## 181               68               77               43               33
    ## 182              141              140               67               88
    ## 183              233              225              108              162
    ## 184              644              710              416              477
    ## 185              506              477              270              292
    ## 186              307              287              189              170
    ## 187              625              608              410              457
    ## 188              294              309              174              200
    ## 189              386              438              261              323
    ## 190              368              319              203              214
    ## 191              207              192              121              123
    ## 192              811              683              431              425
    ## 193              780              762              417              556
    ## 194              478              380              236              233
    ## 195              875              729              418              387
    ## 196              599              502              281              327
    ## 197              422              343              211              190
    ## 198              413              467              281              290
    ## 199              808              749              433              454
    ## 200              862              807              490              425
    ## 201              555              516              314              303
    ## 202              631              542              371              333
    ## 203              575              556              280              378
    ## 204              479              500              266              333
    ## 205              450              450              249              276
    ## 206              351              398              181              240
    ## 207              307              341              183              251
    ## 208              576              641              369              434
    ## 209              519              506              303              335
    ## 210              705              709              362              421
    ## 211              549              661              417              563
    ## 212              317              324              197              169
    ## 213              588              639              409              540
    ## 214              714              831              539              637
    ## 215              584              675              422              572
    ## 216              436              409              205              294
    ## 217              628              697              332              420
    ## 218              247              228              139              142
    ## 219              387              380              193              257
    ## 220              662              683              366              495
    ## 221             1056             1046              700              653
    ## 222              533              503              307              337
    ## 223              742              765              403              441
    ## 224              473              483              257              336
    ## 225              645              585              338              331
    ## 226              356              305              189              174
    ## 227              793              632              394              363
    ## 228              418              381              221              187
    ## 229              687              711              376              449
    ## 230              557              517              282              361
    ## 231              593              590              302              284
    ## 232              228              228              138              142
    ## 233              688              512              328              286
    ## 234              590              505              267              271
    ## 235              574              476              269              243
    ## 236              955              639              384              375
    ## 237              322              214              122               86
    ## 238             1365              991              606              446
    ## 239              832              558              339              269
    ## 240             1476             1170              645              507
    ## 241              388              300              194              181
    ## 242              543              406              253              218
    ## 243             1077             1069              646              625
    ## 244             1145              997              675              625
    ## 245             1127             1050              657              561
    ## 246             1363             1157              735              605
    ## 247              527              755              495              471
    ## 248              496              818              531              583
    ## 249              629              592              329              270
    ## 250              632              574              337              284
    ## 251              383              316              170              164
    ## 252              812              723              427              377
    ## 253              275              284              156              177
    ## 254              750              701              424              392
    ## 255             1033              714              413              330
    ## 256             1033              972              560              522
    ## 257              787              606              328              315
    ## 258              606              481              258              263
    ## 259              539              493              301              233
    ## 260              374              278              164              177
    ## 261              267              235              161              133
    ## 262              271              227              131              109
    ## 263              302              291              173              137
    ## 264              254              211              124              115
    ## 265              377              250              169              179
    ## 266              959              739              393              385
    ## 267              279              214              110              153
    ##     X70.74.Laki.Laki X70.74.Perempuan X.75.Laki.Laki X.75..Perempuan
    ## 1                 33               20             13              27
    ## 2                 13                5              5               8
    ## 3                 24               25             18              26
    ## 4                 26               27             16              13
    ## 5                 10               18             11              17
    ## 6                 17               11              8               7
    ## 7                 37               32             34              23
    ## 8                259              142            214             165
    ## 9                241              132            215             159
    ## 10               215              116            150             121
    ## 11               152              100            136              72
    ## 12               255              156            196             138
    ## 13               243              147            203             136
    ## 14               344              199            258             156
    ## 15               360              187            284             180
    ## 16               289              184            203             168
    ## 17               316              188            252             157
    ## 18               262              163            199             140
    ## 19               259              186            179              98
    ## 20               267              147            171             100
    ## 21               358              289            294             180
    ## 22               273              169            192             130
    ## 23               462              306            284             180
    ## 24               309              227            205             113
    ## 25               295              179            209             133
    ## 26                73               40             50              31
    ## 27               122               76             88              61
    ## 28               264              142            169             121
    ## 29               344              193            234             156
    ## 30               192              105            153              95
    ## 31               238              146            173             112
    ## 32               396              267            276             217
    ## 33               440              285            322             235
    ## 34               261              166            199             140
    ## 35               278              149            210             166
    ## 36               261              144            195             106
    ## 37               100               57             70              56
    ## 38                97               63             60              68
    ## 39               171               85            121              61
    ## 40                47               28             29              27
    ## 41               296              161            239             213
    ## 42               185              111            130              67
    ## 43               310              170            215             121
    ## 44               284              172            204             124
    ## 45               310              170            203             122
    ## 46               149               90            123              71
    ## 47               450              285            320             201
    ## 48               189              144            175              92
    ## 49               169              124            130              64
    ## 50               363              221            281             156
    ## 51              3072             7039           2941            2426
    ## 52               301              655            277             273
    ## 53              1083             2185            979             943
    ## 54              2790             5813           2574            2520
    ## 55              1493             2873           1337            1583
    ## 56              1410             2918           1127            1027
    ## 57              2180             4393           1832            2082
    ## 58              1405             2872           1067            1107
    ## 59              1197             2464            998             954
    ## 60              1932             4125           1483            1405
    ## 61              2820             5542           2219            2525
    ## 62              1749             3607           1347            1235
    ## 63              1114             2370           1007             876
    ## 64              2257             4677           1853            1897
    ## 65              2310             4720           1719            1688
    ## 66              1246             2644            996            1023
    ## 67              1173             2462            936             943
    ## 68              1339             2762           1036            1121
    ## 69              1441             2956           1188            1210
    ## 70              1399             3005           1075            1086
    ## 71               694             1397            588             549
    ## 72              2127             4525           1870            1844
    ## 73              1282             2665           1002             939
    ## 74              1118             2324            846             884
    ## 75              2297             4736           1855            1816
    ## 76              1401             2950           1205            1211
    ## 77              2583             5489           2322            2104
    ## 78               886             1920            787             676
    ## 79              1204             2326            985            1358
    ## 80              1865             3738           1708            1774
    ## 81              1369             2797           1000             999
    ## 82              2195             4515           1663            1761
    ## 83              2544             5174           2042            2001
    ## 84              2089             4324           1790            1604
    ## 85              1259             2670           1041             903
    ## 86              4475             9233           3959            3526
    ## 87              2614             5420           2078            1973
    ## 88               816             1653            661             629
    ## 89               658             1267            523             546
    ## 90              1263             2630            961             953
    ## 91              1232             2512            958             947
    ## 92               951             1963            662             722
    ## 93              1323             2761           1181            1170
    ## 94              1320             2857           1204            1131
    ## 95               664             1297            580             569
    ## 96               832             1668            717             685
    ## 97               698             1483            672             622
    ## 98               552             1157            475             479
    ## 99               313              635            297             299
    ## 100              725             1542            662             578
    ## 101              344              679            325             330
    ## 102              405              894            402             362
    ## 103              425              885            385             368
    ## 104              841             1876            808             746
    ## 105              742             1645            732             624
    ## 106             1042             2168            954             955
    ## 107              704             1560            683             579
    ## 108              994             2259            898             827
    ## 109             1130             2462           1019             922
    ## 110              793             1680            715             675
    ## 111              939             1937            930             914
    ## 112              162              324            156             142
    ## 113              577             1207            528             518
    ## 114             1881             3804           1551            1538
    ## 115             1381             2751           1047            1082
    ## 116             1306             2676           1078             964
    ## 117              909             1871            683             674
    ## 118             2023             4137           1706            1839
    ## 119             1570             3223           1303            1378
    ## 120             1138             2224            954             947
    ## 121             2634             5270           2047            1888
    ## 122             2261             4774           1821            1510
    ## 123             2632             5578           2048            2046
    ## 124             1518             3250           1241            1084
    ## 125             2602             5337           2005            1668
    ## 126             2325             4896           1903            1921
    ## 127              672             1349            579             593
    ## 128              986             1960            796             769
    ## 129             1117             2364            901             956
    ## 130             1381             2920           1093            1057
    ## 131              780             1697            672             618
    ## 132             1859             3778           1517            1385
    ## 133             1339             2835           1087            1153
    ## 134              966             2022            790             840
    ## 135             1435             3011           1198            1181
    ## 136             1331             2758           1026            1124
    ## 137              936             1876            811             852
    ## 138              184              259            189             288
    ## 139              211              265            209             268
    ## 140              241              300            206             216
    ## 141              259              330            204             270
    ## 142              254              335            223             322
    ## 143              218              229            127             178
    ## 144              175              274            188             244
    ## 145               24               29             38              32
    ## 146               29               27             18              32
    ## 147               86              153             92             105
    ## 148               81              115             64              96
    ## 149              212              249            151             191
    ## 150              136              217            107             157
    ## 151               55               45             37              84
    ## 152               53               45             56              47
    ## 153              125              137             84              75
    ## 154              101              115             98             110
    ## 155              291              277            197             238
    ## 156              168              133             99             119
    ## 157               63               72             49              31
    ## 158              283              249            201             208
    ## 159              253              253            183             219
    ## 160              137              103             78              81
    ## 161              294              273            169             189
    ## 162              339              330            191             245
    ## 163              272              258            182             194
    ## 164              183              176            122             114
    ## 165              259              252            161             190
    ## 166              461              410            382             427
    ## 167              265              217            158             157
    ## 168              274              320            209             226
    ## 169              294              263            182             214
    ## 170              356              260            179             179
    ## 171              372              412            353             386
    ## 172              233              262            235             253
    ## 173              381              329            242             230
    ## 174              144              184            132             176
    ## 175              162              192            163             199
    ## 176               26               33             49              79
    ## 177               81               98            106             150
    ## 178               93              112             97             129
    ## 179               38               49             72              94
    ## 180               48               70             60             125
    ## 181               30               38             37              49
    ## 182               49               66             45             102
    ## 183               82              112             95             131
    ## 184              301              325            236             274
    ## 185              222              210            132             157
    ## 186              109               96             77              78
    ## 187              305              269            196             209
    ## 188              154              126             69              80
    ## 189              215              231            157             170
    ## 190              131              146            105             122
    ## 191               72               68             44              65
    ## 192              275              240            169             201
    ## 193              431              289            213             231
    ## 194              155              129            100              98
    ## 195              268              223            140             200
    ## 196              237              213            127             135
    ## 197              139              131            103             123
    ## 198              216              146            100             108
    ## 199              324              316            207             266
    ## 200              290              233            159             173
    ## 201              188              188            106             162
    ## 202              241              213            138             136
    ## 203              231              270            161             257
    ## 204              197              214            143             202
    ## 205              172              219            111             185
    ## 206              151              169            131             204
    ## 207              155              175             92             180
    ## 208              280              332            230             252
    ## 209              205              203            172             182
    ## 210              285              312            196             340
    ## 211              357              351            246             273
    ## 212              116              101             75              91
    ## 213              335              364            289             362
    ## 214              423              420            299             319
    ## 215              363              364            288             334
    ## 216              151              173            121             159
    ## 217              262              324            204             320
    ## 218               88              109             95             138
    ## 219              143              201            135             161
    ## 220              285              376            277             418
    ## 221              486              423            319             299
    ## 222              225              220            138             172
    ## 223              307              350            228             247
    ## 224              224              218            136             243
    ## 225              228              197            127             184
    ## 226              138              115             72             112
    ## 227              238              242            143             166
    ## 228              123              119             72             111
    ## 229              279              265            174             244
    ## 230              211              228            154             204
    ## 231              230              212            136             206
    ## 232              104               70             44              59
    ## 233              184              161            120             136
    ## 234              193              154             98             128
    ## 235              168              132             91             139
    ## 236              248              245            159             181
    ## 237               71               86             61              67
    ## 238              339              260            192             208
    ## 239              183              168            102              97
    ## 240              423              280            195             232
    ## 241              114               91             63              70
    ## 242              139              138             98              97
    ## 243              428              352            235             268
    ## 244              414              327            234             245
    ## 245              443              401            200             278
    ## 246              458              344            221             299
    ## 247              370              280            178             161
    ## 248              441              326            197             213
    ## 249              184              167            102             123
    ## 250              211              176            111             146
    ## 251              116               95             55              66
    ## 252              264              217            160             156
    ## 253              115               89             55              63
    ## 254              306              267            216             227
    ## 255              203              207            117             147
    ## 256              453              294            185             250
    ## 257              221              163            116             153
    ## 258              178              128             83             104
    ## 259              164              119            103             120
    ## 260              112              101             61             110
    ## 261               77               90             52              62
    ## 262               80              105             42              82
    ## 263              118               94             52              51
    ## 264               64               83             59              64
    ## 265              108               96             70              84
    ## 266              293              291            160             165
    ## 267              101               53             45              44

Profile Dataset dengan Function str

``` r
#Membaca dataset dengan read.csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
str(penduduk.dki)
```

    ## 'data.frame':    267 obs. of  37 variables:
    ##  $ TAHUN               : int  2013 2013 2013 2013 2013 2013 2013 2013 2013 2013 ...
    ##  $ NAMA.PROVINSI       : chr  "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" ...
    ##  $ NAMA.KABUPATEN.KOTA : chr  "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" ...
    ##  $ NAMA.KECAMATAN      : chr  "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU SLT" ...
    ##  $ NAMA.KELURAHAN      : chr  "P. PANGGANG" "P. KELAPA" "P. HARAPAN" "P. UNTUNG JAWA" ...
    ##  $ LUAS.WILAYAH..KM2.  : num  0.91 3.76 3.59 0.59 1.57 1.39 2.58 1.26 1.12 1.14 ...
    ##  $ KEPADATAN..JIWA.KM2.: int  6779 1705 628 3625 3084 1968 1350 14584 18987 14465 ...
    ##  $ X                   : logi  NA NA NA NA NA NA ...
    ##  $ X.1                 : logi  NA NA NA NA NA NA ...
    ##  $ X.2                 : logi  NA NA NA NA NA NA ...
    ##  $ X.3                 : logi  NA NA NA NA NA NA ...
    ##  $ X.4                 : logi  NA NA NA NA NA NA ...
    ##  $ X.5                 : logi  NA NA NA NA NA NA ...
    ##  $ X.6                 : logi  NA NA NA NA NA NA ...
    ##  $ X.7                 : logi  NA NA NA NA NA NA ...
    ##  $ X.8                 : logi  NA NA NA NA NA NA ...
    ##  $ X.9                 : logi  NA NA NA NA NA NA ...
    ##  $ X.10                : logi  NA NA NA NA NA NA ...
    ##  $ X.11                : logi  NA NA NA NA NA NA ...
    ##  $ X35.39.Laki.Laki    : int  231 84 255 199 98 113 166 850 954 752 ...
    ##  $ X35.39.Perempuan    : int  235 88 238 185 75 112 174 748 920 675 ...
    ##  $ X40.44.Laki.Laki    : int  233 99 232 178 73 108 130 749 914 691 ...
    ##  $ X40.44.Perempuan    : int  210 88 234 176 94 80 165 798 943 691 ...
    ##  $ X45.49.Laki.Laki    : int  171 72 212 162 67 66 176 779 871 659 ...
    ##  $ X45.49.Perempuan    : int  158 63 193 139 69 62 162 766 823 631 ...
    ##  $ X50.54.Laki.Laki    : int  137 34 150 100 60 61 129 715 736 611 ...
    ##  $ X50.54.Perempuan    : int  126 29 161 119 40 63 97 662 679 514 ...
    ##  $ X55.59.Laki.Laki    : int  98 30 139 97 37 37 108 614 680 539 ...
    ##  $ X55.59.Perempuan    : int  106 39 101 83 32 36 90 537 510 466 ...
    ##  $ X60.64.Laki.Laki    : int  72 29 73 58 22 32 88 555 544 428 ...
    ##  $ X60.64.Perempuan    : int  65 24 56 56 13 26 42 343 421 279 ...
    ##  $ X65.69.Laki.Laki    : int  36 12 18 40 18 21 68 413 398 328 ...
    ##  $ X65.69.Perempuan    : int  33 21 35 54 15 14 34 215 235 160 ...
    ##  $ X70.74.Laki.Laki    : int  33 13 24 26 10 17 37 259 241 215 ...
    ##  $ X70.74.Perempuan    : int  20 5 25 27 18 11 32 142 132 116 ...
    ##  $ X.75.Laki.Laki      : int  13 5 18 16 11 8 34 214 215 150 ...
    ##  $ X.75..Perempuan     : int  27 8 26 13 17 7 23 165 159 121 ...

Profile Dataset dengan Function summary

``` r
#Membaca dataset dengan read.csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
summary(penduduk.dki)
```

    ##      TAHUN      NAMA.PROVINSI      NAMA.KABUPATEN.KOTA NAMA.KECAMATAN    
    ##  Min.   :2013   Length:267         Length:267          Length:267        
    ##  1st Qu.:2013   Class :character   Class :character    Class :character  
    ##  Median :2013   Mode  :character   Mode  :character    Mode  :character  
    ##  Mean   :2013                                                            
    ##  3rd Qu.:2013                                                            
    ##  Max.   :2013                                                            
    ##  NAMA.KELURAHAN     LUAS.WILAYAH..KM2. KEPADATAN..JIWA.KM2.    X          
    ##  Length:267         Min.   : 0.270     Min.   :  628        Mode:logical  
    ##  Class :character   1st Qu.: 0.965     1st Qu.:11734        NA's:267      
    ##  Mode  :character   Median : 1.800     Median :17304                      
    ##                     Mean   : 2.487     Mean   :21974                      
    ##                     3rd Qu.: 3.315     3rd Qu.:29226                      
    ##                     Max.   :13.070     Max.   :94166                      
    ##    X.1            X.2            X.3            X.4            X.5         
    ##  Mode:logical   Mode:logical   Mode:logical   Mode:logical   Mode:logical  
    ##  NA's:267       NA's:267       NA's:267       NA's:267       NA's:267      
    ##                                                                            
    ##                                                                            
    ##                                                                            
    ##                                                                            
    ##    X.6            X.7            X.8            X.9            X.10        
    ##  Mode:logical   Mode:logical   Mode:logical   Mode:logical   Mode:logical  
    ##  NA's:267       NA's:267       NA's:267       NA's:267       NA's:267      
    ##                                                                            
    ##                                                                            
    ##                                                                            
    ##                                                                            
    ##    X.11         X35.39.Laki.Laki X35.39.Perempuan X40.44.Laki.Laki
    ##  Mode:logical   Min.   :   84    Min.   :  75     Min.   :  73    
    ##  NA's:267       1st Qu.: 1186    1st Qu.:1062     1st Qu.:1023    
    ##                 Median : 1880    Median :1631     Median :1576    
    ##                 Mean   : 2264    Mean   :1741     Mean   :1676    
    ##                 3rd Qu.: 2768    3rd Qu.:2213     3rd Qu.:2112    
    ##                 Max.   :13011    Max.   :7488     Max.   :7243    
    ##  X40.44.Perempuan X45.49.Laki.Laki X45.49.Perempuan X50.54.Laki.Laki
    ##  Min.   :   80    Min.   :  66.0   Min.   :  62     Min.   :   34   
    ##  1st Qu.: 1084    1st Qu.: 957.5   1st Qu.: 886     1st Qu.:  790   
    ##  Median : 1714    Median :1404.0   Median :1315     Median : 1216   
    ##  Mean   : 2332    Mean   :1643.7   Mean   :1577     Mean   : 2259   
    ##  3rd Qu.: 2782    3rd Qu.:1949.0   3rd Qu.:1867     3rd Qu.: 2624   
    ##  Max.   :14731    Max.   :8822.0   Max.   :8352     Max.   :17174   
    ##  X50.54.Perempuan X55.59.Laki.Laki X55.59.Perempuan X60.64.Laki.Laki
    ##  Min.   :  29.0   Min.   :  30.0   Min.   :   32    Min.   :  22.0  
    ##  1st Qu.: 712.5   1st Qu.: 595.5   1st Qu.:  557    1st Qu.: 419.5  
    ##  Median :1107.0   Median : 909.0   Median :  889    Median : 650.0  
    ##  Mean   :1336.1   Mean   :1178.6   Mean   : 1867    Mean   : 981.7  
    ##  3rd Qu.:1671.5   3rd Qu.:1405.5   3rd Qu.: 2342    3rd Qu.:1186.5  
    ##  Max.   :7480.0   Max.   :6846.0   Max.   :14326    Max.   :6333.0  
    ##  X60.64.Perempuan X65.69.Laki.Laki X65.69.Perempuan X70.74.Laki.Laki
    ##  Min.   :  13.0   Min.   :   12    Min.   :  14.0   Min.   :  10.0  
    ##  1st Qu.: 366.0   1st Qu.:  253    1st Qu.: 215.5   1st Qu.: 170.0  
    ##  Median : 587.0   Median :  413    Median : 354.0   Median : 285.0  
    ##  Mean   : 876.7   Mean   : 1403    Mean   : 683.6   Mean   : 607.0  
    ##  3rd Qu.:1052.5   3rd Qu.: 2098    3rd Qu.: 928.5   3rd Qu.: 836.5  
    ##  Max.   :5476.0   Max.   :11809    Max.   :4758.0   Max.   :4475.0  
    ##  X70.74.Perempuan X.75.Laki.Laki   X.75..Perempuan 
    ##  Min.   :   5     Min.   :   5.0   Min.   :   7.0  
    ##  1st Qu.: 145     1st Qu.: 116.5   1st Qu.: 121.5  
    ##  Median : 260     Median : 200.0   Median : 204.0  
    ##  Mean   :1083     Mean   : 484.6   Mean   : 480.3  
    ##  3rd Qu.:1784     3rd Qu.: 716.0   3rd Qu.: 675.5  
    ##  Max.   :9233     Max.   :3959.0   Max.   :3526.0

Menggunakan argumen check.names = FALSE

``` r
#Membaca dataset dengan read.csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",", check.names = FALSE)
str(penduduk.dki)
```

    ## 'data.frame':    267 obs. of  37 variables:
    ##  $ TAHUN               : int  2013 2013 2013 2013 2013 2013 2013 2013 2013 2013 ...
    ##  $ NAMA PROVINSI       : chr  "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" ...
    ##  $ NAMA KABUPATEN/KOTA : chr  "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" ...
    ##  $ NAMA KECAMATAN      : chr  "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU SLT" ...
    ##  $ NAMA KELURAHAN      : chr  "P. PANGGANG" "P. KELAPA" "P. HARAPAN" "P. UNTUNG JAWA" ...
    ##  $ LUAS WILAYAH (KM2)  : num  0.91 3.76 3.59 0.59 1.57 1.39 2.58 1.26 1.12 1.14 ...
    ##  $ KEPADATAN (JIWA/KM2): int  6779 1705 628 3625 3084 1968 1350 14584 18987 14465 ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $                     : logi  NA NA NA NA NA NA ...
    ##  $ 35-39 Laki-Laki     : int  231 84 255 199 98 113 166 850 954 752 ...
    ##  $ 35-39 Perempuan     : int  235 88 238 185 75 112 174 748 920 675 ...
    ##  $ 40-44 Laki-Laki     : int  233 99 232 178 73 108 130 749 914 691 ...
    ##  $ 40-44 Perempuan     : int  210 88 234 176 94 80 165 798 943 691 ...
    ##  $ 45-49 Laki-Laki     : int  171 72 212 162 67 66 176 779 871 659 ...
    ##  $ 45-49 Perempuan     : int  158 63 193 139 69 62 162 766 823 631 ...
    ##  $ 50-54 Laki-Laki     : int  137 34 150 100 60 61 129 715 736 611 ...
    ##  $ 50-54 Perempuan     : int  126 29 161 119 40 63 97 662 679 514 ...
    ##  $ 55-59 Laki-Laki     : int  98 30 139 97 37 37 108 614 680 539 ...
    ##  $ 55-59 Perempuan     : int  106 39 101 83 32 36 90 537 510 466 ...
    ##  $ 60-64 Laki-Laki     : int  72 29 73 58 22 32 88 555 544 428 ...
    ##  $ 60-64 Perempuan     : int  65 24 56 56 13 26 42 343 421 279 ...
    ##  $ 65-69 Laki-Laki     : int  36 12 18 40 18 21 68 413 398 328 ...
    ##  $ 65-69 Perempuan     : int  33 21 35 54 15 14 34 215 235 160 ...
    ##  $ 70-74 Laki-Laki     : int  33 13 24 26 10 17 37 259 241 215 ...
    ##  $ 70-74 Perempuan     : int  20 5 25 27 18 11 32 142 132 116 ...
    ##  $ >75 Laki-Laki       : int  13 5 18 16 11 8 34 214 215 150 ...
    ##  $ >75  Perempuan      : int  27 8 26 13 17 7 23 165 159 121 ...

Membaca Tab Separated Value (TSV)

``` r
#Membaca dataset dengan read.csv dan dimasukkan ke variable penduduk.dki
penduduk.dki <- read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.tsv", sep="\t")
penduduk.dki
```

    ##     TAHUN        NAMA.PROVINSI NAMA.KABUPATEN.KOTA    NAMA.KECAMATAN
    ## 1    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 2    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 3    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU UTR
    ## 4    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 5    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 6    2013 PROVINSI DKI JAKARTA  KAB.ADM.KEP.SERIBU   KEP. SERIBU SLT
    ## 7    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 8    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 9    2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 10   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 11   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 12   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT            GAMBIR
    ## 13   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 14   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 15   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 16   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 17   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       SAWAH BESAR
    ## 18   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 19   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 20   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 21   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 22   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 23   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 24   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 25   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT         KEMAYORAN
    ## 26   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 27   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 28   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 29   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 30   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 31   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT             SENEN
    ## 32   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 33   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 34   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT     CEMPAKA PUTIH
    ## 35   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 36   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 37   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 38   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 39   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT           MENTENG
    ## 40   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 41   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 42   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 43   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 44   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 45   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 46   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT       TANAH ABANG
    ## 47   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 48   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 49   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 50   2013 PROVINSI DKI JAKARTA       JAKARTA PUSAT        JOHAR BARU
    ## 51   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 52   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 53   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 54   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 55   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA       PENJARINGAN
    ## 56   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 57   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 58   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 59   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 60   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 61   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 62   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     TANJUNG PRIOK
    ## 63   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 64   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 65   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 66   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 67   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 68   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA              KOJA
    ## 69   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 70   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 71   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 72   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 73   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 74   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 75   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA         CILINCING
    ## 76   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 77   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 78   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA        PADEMANGAN
    ## 79   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 80   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 81   2013 PROVINSI DKI JAKARTA       JAKARTA UTARA     KELAPA GADING
    ## 82   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 83   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 84   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 85   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 86   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 87   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        CENGKARENG
    ## 88   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 89   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 90   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 91   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 92   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 93   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 94   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT GROGOL PETAMBURAN
    ## 95   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 96   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 97   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 98   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 99   2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 100  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 101  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 102  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        TAMAN SARI
    ## 103  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 104  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 105  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 106  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 107  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 108  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 109  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 110  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 111  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 112  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 113  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT           TAMBORA
    ## 114  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 115  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 116  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 117  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 118  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 119  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 120  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT       KEBON JERUK
    ## 121  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 122  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 123  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 124  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 125  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT        KALI DERES
    ## 126  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 127  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 128  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 129  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 130  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 131  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT          PALMERAH
    ## 132  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 133  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 134  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 135  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 136  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 137  2013 PROVINSI DKI JAKARTA       JAKARTA BARAT         KEMBANGAN
    ## 138  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 139  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 140  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 141  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 142  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 143  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 144  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN             TEBET
    ## 145  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 146  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 147  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 148  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 149  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 150  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 151  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 152  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN        SETIA BUDI
    ## 153  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 154  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 155  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 156  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 157  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN  MAMPANG PRAPATAN
    ## 158  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 159  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 160  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 161  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 162  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 163  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 164  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PASAR MINGGU
    ## 165  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 166  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 167  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 168  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 169  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 170  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN LAMA
    ## 171  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 172  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 173  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 174  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 175  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          CILANDAK
    ## 176  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 177  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 178  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 179  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 180  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 181  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 182  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 183  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 184  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 185  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN    KEBAYORAN BARU
    ## 186  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 187  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 188  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 189  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 190  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 191  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN          PANCORAN
    ## 192  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 193  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 194  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 195  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 196  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 197  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN         JAGAKARSA
    ## 198  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 199  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 200  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 201  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 202  2013 PROVINSI DKI JAKARTA     JAKARTA SELATAN      PESANGGRAHAN
    ## 203  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 204  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 205  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 206  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 207  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 208  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          MATRAMAN
    ## 209  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 210  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 211  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 212  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 213  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 214  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 215  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       PULO GADUNG
    ## 216  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 217  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 218  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 219  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 220  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 221  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 222  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 223  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        JATINEGARA
    ## 224  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 225  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 226  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 227  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 228  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 229  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 230  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       KRAMAT JATI
    ## 231  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 232  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 233  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 234  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 235  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR        PASAR REBO
    ## 236  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 237  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 238  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 239  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 240  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 241  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 242  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR            CAKUNG
    ## 243  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 244  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 245  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 246  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 247  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 248  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 249  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR       DUREN SAWIT
    ## 250  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 251  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 252  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 253  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 254  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           MAKASAR
    ## 255  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 256  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 257  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 258  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 259  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR           CIRACAS
    ## 260  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 261  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 262  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 263  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 264  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 265  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 266  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ## 267  2013 PROVINSI DKI JAKARTA       JAKARTA TIMUR          CIPAYUNG
    ##             NAMA.KELURAHAN LUAS.WILAYAH..KM2. KEPADATAN..JIWA.KM2.  X X.1 X.2
    ## 1              P. PANGGANG               0.91                 6779 NA  NA  NA
    ## 2                P. KELAPA               3.76                 1705 NA  NA  NA
    ## 3               P. HARAPAN               3.59                  628 NA  NA  NA
    ## 4           P. UNTUNG JAWA               0.59                 3625 NA  NA  NA
    ## 5                P. TIDUNG               1.57                 3084 NA  NA  NA
    ## 6                  P. PARI               1.39                 1968 NA  NA  NA
    ## 7                   GAMBIR               2.58                 1350 NA  NA  NA
    ## 8                   CIDENG               1.26                14584 NA  NA  NA
    ## 9             PETOJO UTARA               1.12                18987 NA  NA  NA
    ## 10          PETOJO SELATAN               1.14                14465 NA  NA  NA
    ## 11            KEBON KELAPA               0.78                15890 NA  NA  NA
    ## 12               DURI PULO               0.72                35628 NA  NA  NA
    ## 13              PASAR BARU               1.89                 8041 NA  NA  NA
    ## 14            KARANG ANYAR               0.51                63122 NA  NA  NA
    ## 15                 KARTINI               0.55                49862 NA  NA  NA
    ## 16     GUNUNG SAHARI UTARA               1.98                 9933 NA  NA  NA
    ## 17      MANGGA DUA SELATAN               1.29                26203 NA  NA  NA
    ## 18               KEMAYORAN               0.55                44202 NA  NA  NA
    ## 19            KEBON KOSONG               1.13                28014 NA  NA  NA
    ## 20           HARAPAN MULIA               0.91                29205 NA  NA  NA
    ## 21                 SERDANG               0.82                41837 NA  NA  NA
    ## 22   GUNUNG SAHARI SELATAN               0.53                43858 NA  NA  NA
    ## 23            CEMPAKA BARU               0.99                38088 NA  NA  NA
    ## 24              SUMUR BATU               1.15                23271 NA  NA  NA
    ## 25            UTAN PANJANG               1.05                31889 NA  NA  NA
    ## 26                   SENEN               0.81                10158 NA  NA  NA
    ## 27                  KENARI               0.91                11757 NA  NA  NA
    ## 28                 PASEBAN               0.71                38400 NA  NA  NA
    ## 29                  KRAMAT               0.71                47630 NA  NA  NA
    ## 30                 KWITANG               0.45                40724 NA  NA  NA
    ## 31                  BUNGUR               0.64                34463 NA  NA  NA
    ## 32     CEMPAKA PUTIH TIMUR               2.22                12326 NA  NA  NA
    ## 33     CEMPAKA PUTIH BARAT               1.22                32561 NA  NA  NA
    ## 34                RAWASARI               1.25                19945 NA  NA  NA
    ## 35                 MENTENG               2.44                11968 NA  NA  NA
    ## 36              PEGANGSAAN               0.98                27151 NA  NA  NA
    ## 37                  CIKINI               0.82                11711 NA  NA  NA
    ## 38              GONDANGDIA               1.46                 3194 NA  NA  NA
    ## 39             KEBON SIRIH               0.83                18577 NA  NA  NA
    ## 40                  GELORA               2.59                 1450 NA  NA  NA
    ## 41         BENDUNGAN HILIR               1.58                16018 NA  NA  NA
    ## 42           KARET TENGSIN               1.53                13912 NA  NA  NA
    ## 43              PETAMBURAN               0.90                43262 NA  NA  NA
    ## 44            KEBON MELATI               1.26                30563 NA  NA  NA
    ## 45            KEBON KACANG               0.71                35545 NA  NA  NA
    ## 46            KAMPUNG BALI               0.73                19941 NA  NA  NA
    ## 47              JOHAR BARU               1.19                35270 NA  NA  NA
    ## 48            KAMPUNG RAWA               0.30                86123 NA  NA  NA
    ## 49                   GALUR               0.27                79022 NA  NA  NA
    ## 50            TANAH TINGGI               0.62                71177 NA  NA  NA
    ## 51             PENJARINGAN               3.95                28071 NA  NA  NA
    ## 52             KAMAL MUARA              10.53                 1144 NA  NA  NA
    ## 53             KAPUK MUARA              10.56                 3243 NA  NA  NA
    ## 54               PEJAGALAN               3.23                27856 NA  NA  NA
    ## 55                   PLUIT               7.71                 6344 NA  NA  NA
    ## 56           TANJUNG PRIOK               5.59                 7794 NA  NA  NA
    ## 57             SUNTER JAYA               4.68                14791 NA  NA  NA
    ## 58                PAPANGGO               2.80                16353 NA  NA  NA
    ## 59            SUNGAI BAMBU               2.36                15221 NA  NA  NA
    ## 60            KEBON BAWANG               1.73                35952 NA  NA  NA
    ## 61            SUNTER AGUNG               6.65                12234 NA  NA  NA
    ## 62                 WARAKAS               1.09                49384 NA  NA  NA
    ## 63                    KOJA               3.27                10838 NA  NA  NA
    ## 64              TUGU UTARA               2.37                34123 NA  NA  NA
    ## 65                   LAGOA               1.58                44105 NA  NA  NA
    ## 66        RAWA BADAK UTARA               1.33                31357 NA  NA  NA
    ## 67            TUGU SELATAN               1.86                22869 NA  NA  NA
    ## 68      RAWA BADAK SELATAN               1.33                35441 NA  NA  NA
    ## 69               CILINCING               8.31                 6326 NA  NA  NA
    ## 70                SUKAPURA               5.61                11602 NA  NA  NA
    ## 71                 MARUNDA               7.92                 3105 NA  NA  NA
    ## 72               KALI BARU               2.47                34278 NA  NA  NA
    ## 73            SEMPER TIMUR               3.17                12725 NA  NA  NA
    ## 74                 ROROTAN              10.64                 3859 NA  NA  NA
    ## 75            SEMPER BARAT               4.44                18003 NA  NA  NA
    ## 76        PADEMANGAN TIMUR               2.61                16245 NA  NA  NA
    ## 77        PADEMANGAN BARAT               3.53                24947 NA  NA  NA
    ## 78                   ANCOL               5.77                 4981 NA  NA  NA
    ## 79     KELAPA GADING TIMUR               5.31                 7089 NA  NA  NA
    ## 80          PEGANGSAAN DUA               6.28                 8216 NA  NA  NA
    ## 81     KELAPA GADING BARAT               4.53                 8515 NA  NA  NA
    ## 82        CENGKARENG BARAT               4.26                16409 NA  NA  NA
    ## 83            DURI KOSAMBI               5.03                15866 NA  NA  NA
    ## 84              RAWA BUAYA               4.67                14886 NA  NA  NA
    ## 85      KEDAUNG KALI ANGKE               2.61                14438 NA  NA  NA
    ## 86                   KAPUK               7.18                20919 NA  NA  NA
    ## 87        CENGKARENG TIMUR               4.18                20735 NA  NA  NA
    ## 88                  GROGOL               1.22                16960 NA  NA  NA
    ## 89     TANJUNG DUREN UTARA               1.11                18227 NA  NA  NA
    ## 90                  TOMANG               1.88                18103 NA  NA  NA
    ## 91                JELAMBAR               1.44                24624 NA  NA  NA
    ## 92   TANJUNG DUREN SELATAN               1.76                15915 NA  NA  NA
    ## 93           JELAMBAR BARU               1.44                30778 NA  NA  NA
    ## 94           WIJAYA KUSUMA               2.61                17092 NA  NA  NA
    ## 95              TAMAN SARI               0.68                26441 NA  NA  NA
    ## 96                  KRUKUT               0.55                42111 NA  NA  NA
    ## 97                  MAPHAR               0.59                34693 NA  NA  NA
    ## 98                  TANGKI               0.37                43827 NA  NA  NA
    ## 99            MANGGA BESAR               0.51                17882 NA  NA  NA
    ## 100              KEAGUNGAN               0.32                65800 NA  NA  NA
    ## 101                 GLODOK               0.38                24153 NA  NA  NA
    ## 102              PINANGSIA               0.96                13791 NA  NA  NA
    ## 103                TAMBORA               0.28                45375 NA  NA  NA
    ## 104             KALI ANYAR               0.32                94166 NA  NA  NA
    ## 105             DURI UTARA               0.40                60175 NA  NA  NA
    ## 106           TANAH SEREAL               0.62                49860 NA  NA  NA
    ## 107              KERENDANG               0.32                74109 NA  NA  NA
    ## 108          JEMBATAN BESI               0.55                66447 NA  NA  NA
    ## 109                  ANGKE               0.80                43826 NA  NA  NA
    ## 110          JEMBATAN LIMA               0.46                54543 NA  NA  NA
    ## 111                PEKOJAN               0.78                35333 NA  NA  NA
    ## 112             ROA MALAKA               0.53                 8275 NA  NA  NA
    ## 113           DURI SELATAN               0.42                41460 NA  NA  NA
    ## 114            KEBON JERUK               2.69                20957 NA  NA  NA
    ## 115         SUKABUMI UTARA               1.60                26438 NA  NA  NA
    ## 116       SUKABUMI SELATAN               1.57                26532 NA  NA  NA
    ## 117             KELAPA DUA               1.50                17297 NA  NA  NA
    ## 118              DURI KEPA               3.86                17148 NA  NA  NA
    ## 119           KEDOYA UTARA               3.14                15976 NA  NA  NA
    ## 120         KEDOYA SELATAN               2.28                15519 NA  NA  NA
    ## 121              KALIDERES               5.72                13726 NA  NA  NA
    ## 122                SEMANAN               5.98                13037 NA  NA  NA
    ## 123             TEGAL ALUR               4.00                23429 NA  NA  NA
    ## 124                  KAMAL               4.49                12257 NA  NA  NA
    ## 125             PEGADUNGAN               8.89                 8364 NA  NA  NA
    ## 126               PALMERAH               2.11                33544 NA  NA  NA
    ## 127                  SLIPI               0.97                19980 NA  NA  NA
    ## 128       KOTA BAMBU UTARA               0.63                46608 NA  NA  NA
    ## 129              JATI PULO               0.87                38834 NA  NA  NA
    ## 130            KEMANGGISAN               2.33                16328 NA  NA  NA
    ## 131     KOTA BAMBU SELATAN               0.61                41082 NA  NA  NA
    ## 132        KEMBANGAN UTARA               3.65                15703 NA  NA  NA
    ## 133           MERUYA UTARA               4.76                 9608 NA  NA  NA
    ## 134         MERUYA SELATAN               2.85                11142 NA  NA  NA
    ## 135              SRENGSENG               4.92                 9446 NA  NA  NA
    ## 136                  JOGLO               4.86                 8812 NA  NA  NA
    ## 137      KEMBANGAN SELATAN               3.60                 7866 NA  NA  NA
    ## 138            TEBET TIMUR               1.39                14544 NA  NA  NA
    ## 139            TEBET BARAT               1.72                14080 NA  NA  NA
    ## 140          MENTENG DALAM               2.58                16355 NA  NA  NA
    ## 141             KEBON BARU               1.30                31580 NA  NA  NA
    ## 142             BUKIT DURI               1.08                38906 NA  NA  NA
    ## 143      MANGGARAI SELATAN               0.51                52659 NA  NA  NA
    ## 144              MANGGARAI               0.95                36246 NA  NA  NA
    ## 145             SETIA BUDI               0.94                 3852 NA  NA  NA
    ## 146         KARET SEMANGGI               0.90                 3202 NA  NA  NA
    ## 147         KARET KUNINGAN               1.79                10414 NA  NA  NA
    ## 148                  KARET               0.94                12948 NA  NA  NA
    ## 149           MENTENG ATAS               0.90                35511 NA  NA  NA
    ## 150          PASAR MANGGIS               0.78                40395 NA  NA  NA
    ## 151                 GUNTUR               0.65                 7174 NA  NA  NA
    ## 152         KUNINGAN TIMUR               2.15                 3335 NA  NA  NA
    ## 153       MAMPANG PRAPATAN               0.78                27765 NA  NA  NA
    ## 154                 BANGKA               3.30                 7351 NA  NA  NA
    ## 155           PELA MAMPANG               1.62                30940 NA  NA  NA
    ## 156           TEGAL PARANG               1.06                34830 NA  NA  NA
    ## 157         KUNINGAN BARAT               0.98                15120 NA  NA  NA
    ## 158           PASAR MINGGU               2.79                 9965 NA  NA  NA
    ## 159            JATI PADANG               2.50                16524 NA  NA  NA
    ## 160         CILANDAK TIMUR               3.53                 8075 NA  NA  NA
    ## 161                RAGUNAN               5.05                 8681 NA  NA  NA
    ## 162          PEJATEN TIMUR               2.88                22624 NA  NA  NA
    ## 163          PEJATEN BARAT               2.90                14338 NA  NA  NA
    ## 164              KEBAGUSAN               2.26                20705 NA  NA  NA
    ## 165   KEBAYORAN LAMA UTARA               1.78                27853 NA  NA  NA
    ## 166          PONDOK PINANG               6.84                 8897 NA  NA  NA
    ## 167                CIPULIR               1.94                22494 NA  NA  NA
    ## 168           GROGOL UTARA               3.33                14342 NA  NA  NA
    ## 169         GROGOL SELATAN               2.85                17009 NA  NA  NA
    ## 170 KEBAYORAN LAMA SELATAN               2.57                17598 NA  NA  NA
    ## 171         CILANDAK BARAT               6.05                 9546 NA  NA  NA
    ## 172            LEBAK BULUS               4.41                 8840 NA  NA  NA
    ## 173            PONDOK LABU               3.61                13349 NA  NA  NA
    ## 174       GANDARIA SELATAN               1.76                13816 NA  NA  NA
    ## 175         CIPETE SELATAN               2.37                12751 NA  NA  NA
    ## 176                MELAWAI               1.26                 2528 NA  NA  NA
    ## 177                 GUNUNG               1.32                 8043 NA  NA  NA
    ## 178            KRAMAT PELA               1.23                12872 NA  NA  NA
    ## 179                 SELONG               1.40                 3014 NA  NA  NA
    ## 180             RAWA BARAT               0.69                 9778 NA  NA  NA
    ## 181                SENAYAN               1.53                 2856 NA  NA  NA
    ## 182                   PULO               1.27                 5408 NA  NA  NA
    ## 183              PETOGOGAN               0.86                15895 NA  NA  NA
    ## 184         GANDARIA UTARA               1.52                29247 NA  NA  NA
    ## 185           CIPETE UTARA               1.83                20664 NA  NA  NA
    ## 186               PANCORAN               1.24                17127 NA  NA  NA
    ## 187               KALIBATA               2.20                21353 NA  NA  NA
    ## 188              RAWA JATI               0.67                29915 NA  NA  NA
    ## 189             DUREN TIGA               2.45                12987 NA  NA  NA
    ## 190             PENGADEGAN               0.95                24076 NA  NA  NA
    ## 191                 CIKOKO               0.72                17661 NA  NA  NA
    ## 192              JAGAKARSA               4.85                12940 NA  NA  NA
    ## 193        SRENGSENG SAWAH               6.75                 8912 NA  NA  NA
    ## 194               CIGANJUR               3.61                10334 NA  NA  NA
    ## 195          LENTENG AGUNG               2.28                24703 NA  NA  NA
    ## 196          TANJUNG BARAT               3.65                11460 NA  NA  NA
    ## 197                CIPEDAK               4.24                 8473 NA  NA  NA
    ## 198           PESANGGRAHAN               2.10                13859 NA  NA  NA
    ## 199                BINTARO               4.56                11808 NA  NA  NA
    ## 200       PETUKANGAN UTARA               2.99                19001 NA  NA  NA
    ## 201     PETUKANGAN SELATAN               2.11                18260 NA  NA  NA
    ## 202                ULUJAMI               1.71                26161 NA  NA  NA
    ## 203          PISANGAN BARU               0.68                54913 NA  NA  NA
    ## 204        UTAN KAYU UTARA               1.05                31694 NA  NA  NA
    ## 205             KAYU MANIS               0.57                52740 NA  NA  NA
    ## 206             PAL MERIAM               0.65                36818 NA  NA  NA
    ## 207          KEBON MANGGIS               0.78                25601 NA  NA  NA
    ## 208      UTAN KAYU SELATAN               1.12                34434 NA  NA  NA
    ## 209            PULO GADUNG               1.29                30260 NA  NA  NA
    ## 210         PISANGAN TIMUR               1.80                26931 NA  NA  NA
    ## 211               CIPINANG               1.54                29756 NA  NA  NA
    ## 212        JATINEGARA KAUM               1.23                21792 NA  NA  NA
    ## 213             RAWAMANGUN               2.60                16963 NA  NA  NA
    ## 214             KAYU PUTIH               4.37                11179 NA  NA  NA
    ## 215                   JATI               2.15                17270 NA  NA  NA
    ## 216         KAMPUNG MELAYU               0.48                63973 NA  NA  NA
    ## 217            BIDARA CINA               1.26                35493 NA  NA  NA
    ## 218            BALI MESTER               0.67                17304 NA  NA  NA
    ## 219             RAWA BUNGA               0.88                28478 NA  NA  NA
    ## 220      CIPINANG CEMPEDAK               1.67                22917 NA  NA  NA
    ## 221         CIPINANG MUARA               2.90                21525 NA  NA  NA
    ## 222 CIPINANG BESAR SELATAN               1.63                23417 NA  NA  NA
    ## 223   CIPINANG BESAR UTARA               1.15                48850 NA  NA  NA
    ## 224            KRAMAT JATI               1.52                25801 NA  NA  NA
    ## 225         KAMPUNG TENGAH               2.03                24281 NA  NA  NA
    ## 226                  DUKUH               1.98                13402 NA  NA  NA
    ## 227             BATU AMPAR               2.55                19983 NA  NA  NA
    ## 228           BALE KAMBANG               1.67                18012 NA  NA  NA
    ## 229              CILILITAN               1.80                26094 NA  NA  NA
    ## 230                 CAWANG               1.79                21827 NA  NA  NA
    ## 231                 GEDONG               2.65                14684 NA  NA  NA
    ## 232                   BARU               1.89                14133 NA  NA  NA
    ## 233              CIJANTUNG               2.37                18589 NA  NA  NA
    ## 234               KALISARI               2.89                15517 NA  NA  NA
    ## 235                PEKAYON               3.14                14600 NA  NA  NA
    ## 236             JATINEGARA               6.60                14709 NA  NA  NA
    ## 237            RAWA TERATE               4.10                 7387 NA  NA  NA
    ## 238           PENGGILINGAN               4.48                22483 NA  NA  NA
    ## 239           CAKUNG TIMUR               9.81                 6464 NA  NA  NA
    ## 240            PULO GEBANG               6.86                13716 NA  NA  NA
    ## 241          UJUNG MENTENG               4.43                 6972 NA  NA  NA
    ## 242           CAKUNG BARAT               6.19                10030 NA  NA  NA
    ## 243            DUREN SAWIT               4.58                14100 NA  NA  NA
    ## 244           PONDOK BAMBU               5.00                13285 NA  NA  NA
    ## 245                KLENDER               3.08                25456 NA  NA  NA
    ## 246          PONDOK KELAPA               5.72                12673 NA  NA  NA
    ## 247            MALAKA SARI               1.38                23592 NA  NA  NA
    ## 248            MALAKA JAYA               0.99                36535 NA  NA  NA
    ## 249            PONDOK KOPI               2.06                18136 NA  NA  NA
    ## 250                MAKASAR               1.85                20695 NA  NA  NA
    ## 251           PINANG RANTI               1.89                14793 NA  NA  NA
    ## 252             KEBON PALA               2.30                22647 NA  NA  NA
    ## 253  HALIM PERDANA KUSUMAH              13.07                 2546 NA  NA  NA
    ## 254        CIPINANG MELAYU               2.53                18551 NA  NA  NA
    ## 255                CIRACAS               3.93                17648 NA  NA  NA
    ## 256                CIBUBUR               4.50                15686 NA  NA  NA
    ## 257       KELAPA DUA WETAN               3.37                14203 NA  NA  NA
    ## 258                SUSUKAN               2.19                19019 NA  NA  NA
    ## 259               RAMBUTAN               2.09                19324 NA  NA  NA
    ## 260               CIPAYUNG               3.08                 8441 NA  NA  NA
    ## 261              CILANGKAP               6.03                 4396 NA  NA  NA
    ## 262         PONDOK RANGGON               3.66                 6772 NA  NA  NA
    ## 263                 MUNJUL               1.90                12734 NA  NA  NA
    ## 264                   SETU               3.25                 6028 NA  NA  NA
    ## 265             BAMBU APUS               3.17                 8400 NA  NA  NA
    ## 266           LUBANG BUAYA               3.72                18055 NA  NA  NA
    ## 267                  CEGER               3.63                 5492 NA  NA  NA
    ##     X.3 X.4 X.5 X.6 X.7 X.8 X.9 X.10 X.11 X35.39.Laki.Laki X35.39.Perempuan
    ## 1    NA  NA  NA  NA  NA  NA  NA   NA   NA              231              235
    ## 2    NA  NA  NA  NA  NA  NA  NA   NA   NA               84               88
    ## 3    NA  NA  NA  NA  NA  NA  NA   NA   NA              255              238
    ## 4    NA  NA  NA  NA  NA  NA  NA   NA   NA              199              185
    ## 5    NA  NA  NA  NA  NA  NA  NA   NA   NA               98               75
    ## 6    NA  NA  NA  NA  NA  NA  NA   NA   NA              113              112
    ## 7    NA  NA  NA  NA  NA  NA  NA   NA   NA              166              174
    ## 8    NA  NA  NA  NA  NA  NA  NA   NA   NA              850              748
    ## 9    NA  NA  NA  NA  NA  NA  NA   NA   NA              954              920
    ## 10   NA  NA  NA  NA  NA  NA  NA   NA   NA              752              675
    ## 11   NA  NA  NA  NA  NA  NA  NA   NA   NA              592              491
    ## 12   NA  NA  NA  NA  NA  NA  NA   NA   NA             1213             1106
    ## 13   NA  NA  NA  NA  NA  NA  NA   NA   NA              714              611
    ## 14   NA  NA  NA  NA  NA  NA  NA   NA   NA             1575             1485
    ## 15   NA  NA  NA  NA  NA  NA  NA   NA   NA             1307             1177
    ## 16   NA  NA  NA  NA  NA  NA  NA   NA   NA              817              835
    ## 17   NA  NA  NA  NA  NA  NA  NA   NA   NA             1683             1662
    ## 18   NA  NA  NA  NA  NA  NA  NA   NA   NA             1164             1063
    ## 19   NA  NA  NA  NA  NA  NA  NA   NA   NA             1644             1542
    ## 20   NA  NA  NA  NA  NA  NA  NA   NA   NA             1256             1213
    ## 21   NA  NA  NA  NA  NA  NA  NA   NA   NA             1603             1559
    ## 22   NA  NA  NA  NA  NA  NA  NA   NA   NA             1071              979
    ## 23   NA  NA  NA  NA  NA  NA  NA   NA   NA             1750             1710
    ## 24   NA  NA  NA  NA  NA  NA  NA   NA   NA             1452             1372
    ## 25   NA  NA  NA  NA  NA  NA  NA   NA   NA             1610             1549
    ## 26   NA  NA  NA  NA  NA  NA  NA   NA   NA              398              428
    ## 27   NA  NA  NA  NA  NA  NA  NA   NA   NA              456              447
    ## 28   NA  NA  NA  NA  NA  NA  NA   NA   NA             1266             1232
    ## 29   NA  NA  NA  NA  NA  NA  NA   NA   NA             1552             1479
    ## 30   NA  NA  NA  NA  NA  NA  NA   NA   NA              908              793
    ## 31   NA  NA  NA  NA  NA  NA  NA   NA   NA             1046              993
    ## 32   NA  NA  NA  NA  NA  NA  NA   NA   NA             1264             1267
    ## 33   NA  NA  NA  NA  NA  NA  NA   NA   NA             1858             1811
    ## 34   NA  NA  NA  NA  NA  NA  NA   NA   NA             1200             1160
    ## 35   NA  NA  NA  NA  NA  NA  NA   NA   NA             1349             1194
    ## 36   NA  NA  NA  NA  NA  NA  NA   NA   NA             1172             1096
    ## 37   NA  NA  NA  NA  NA  NA  NA   NA   NA              424              428
    ## 38   NA  NA  NA  NA  NA  NA  NA   NA   NA              192              165
    ## 39   NA  NA  NA  NA  NA  NA  NA   NA   NA              733              717
    ## 40   NA  NA  NA  NA  NA  NA  NA   NA   NA              185              178
    ## 41   NA  NA  NA  NA  NA  NA  NA   NA   NA             1124             1138
    ## 42   NA  NA  NA  NA  NA  NA  NA   NA   NA             1118             1078
    ## 43   NA  NA  NA  NA  NA  NA  NA   NA   NA             1851             1780
    ## 44   NA  NA  NA  NA  NA  NA  NA   NA   NA             1862             1721
    ## 45   NA  NA  NA  NA  NA  NA  NA   NA   NA             1150             1041
    ## 46   NA  NA  NA  NA  NA  NA  NA   NA   NA              612              613
    ## 47   NA  NA  NA  NA  NA  NA  NA   NA   NA             2036             1878
    ## 48   NA  NA  NA  NA  NA  NA  NA   NA   NA             1210             1255
    ## 49   NA  NA  NA  NA  NA  NA  NA   NA   NA              999             1060
    ## 50   NA  NA  NA  NA  NA  NA  NA   NA   NA             2118             2013
    ## 51   NA  NA  NA  NA  NA  NA  NA   NA   NA             9225             5535
    ## 52   NA  NA  NA  NA  NA  NA  NA   NA   NA             1045              517
    ## 53   NA  NA  NA  NA  NA  NA  NA   NA   NA             2763             1631
    ## 54   NA  NA  NA  NA  NA  NA  NA   NA   NA             7137             4468
    ## 55   NA  NA  NA  NA  NA  NA  NA   NA   NA             3656             2264
    ## 56   NA  NA  NA  NA  NA  NA  NA   NA   NA             3374             2025
    ## 57   NA  NA  NA  NA  NA  NA  NA   NA   NA             5374             3427
    ## 58   NA  NA  NA  NA  NA  NA  NA   NA   NA             3667             2290
    ## 59   NA  NA  NA  NA  NA  NA  NA   NA   NA             2807             1749
    ## 60   NA  NA  NA  NA  NA  NA  NA   NA   NA             4677             3009
    ## 61   NA  NA  NA  NA  NA  NA  NA   NA   NA             6094             3710
    ## 62   NA  NA  NA  NA  NA  NA  NA   NA   NA             4224             2608
    ## 63   NA  NA  NA  NA  NA  NA  NA   NA   NA             3088             1767
    ## 64   NA  NA  NA  NA  NA  NA  NA   NA   NA             6608             3954
    ## 65   NA  NA  NA  NA  NA  NA  NA   NA   NA             5931             3342
    ## 66   NA  NA  NA  NA  NA  NA  NA   NA   NA             3260             2064
    ## 67   NA  NA  NA  NA  NA  NA  NA   NA   NA             3744             2235
    ## 68   NA  NA  NA  NA  NA  NA  NA   NA   NA             3910             2420
    ## 69   NA  NA  NA  NA  NA  NA  NA   NA   NA             4654             2614
    ## 70   NA  NA  NA  NA  NA  NA  NA   NA   NA             5221             3376
    ## 71   NA  NA  NA  NA  NA  NA  NA   NA   NA             2187             1207
    ## 72   NA  NA  NA  NA  NA  NA  NA   NA   NA             7616             4096
    ## 73   NA  NA  NA  NA  NA  NA  NA   NA   NA             3230             1683
    ## 74   NA  NA  NA  NA  NA  NA  NA   NA   NA             3442             1876
    ## 75   NA  NA  NA  NA  NA  NA  NA   NA   NA             6419             3579
    ## 76   NA  NA  NA  NA  NA  NA  NA   NA   NA             3005             1935
    ## 77   NA  NA  NA  NA  NA  NA  NA   NA   NA             7178             4264
    ## 78   NA  NA  NA  NA  NA  NA  NA   NA   NA             2259             1380
    ## 79   NA  NA  NA  NA  NA  NA  NA   NA   NA             2539             1744
    ## 80   NA  NA  NA  NA  NA  NA  NA   NA   NA             4170             2259
    ## 81   NA  NA  NA  NA  NA  NA  NA   NA   NA             2628             1433
    ## 82   NA  NA  NA  NA  NA  NA  NA   NA   NA             5316             3221
    ## 83   NA  NA  NA  NA  NA  NA  NA   NA   NA             6922             3764
    ## 84   NA  NA  NA  NA  NA  NA  NA   NA   NA             5632             3396
    ## 85   NA  NA  NA  NA  NA  NA  NA   NA   NA             2951             1756
    ## 86   NA  NA  NA  NA  NA  NA  NA   NA   NA            13011             7488
    ## 87   NA  NA  NA  NA  NA  NA  NA   NA   NA             7146             4147
    ## 88   NA  NA  NA  NA  NA  NA  NA   NA   NA             1530              903
    ## 89   NA  NA  NA  NA  NA  NA  NA   NA   NA             1277              812
    ## 90   NA  NA  NA  NA  NA  NA  NA   NA   NA             2404             1449
    ## 91   NA  NA  NA  NA  NA  NA  NA   NA   NA             2358             1581
    ## 92   NA  NA  NA  NA  NA  NA  NA   NA   NA             1857             1220
    ## 93   NA  NA  NA  NA  NA  NA  NA   NA   NA             3165             2116
    ## 94   NA  NA  NA  NA  NA  NA  NA   NA   NA             3523             2301
    ## 95   NA  NA  NA  NA  NA  NA  NA   NA   NA             1365              729
    ## 96   NA  NA  NA  NA  NA  NA  NA   NA   NA             1848             1107
    ## 97   NA  NA  NA  NA  NA  NA  NA   NA   NA             1555              919
    ## 98   NA  NA  NA  NA  NA  NA  NA   NA   NA             1248              691
    ## 99   NA  NA  NA  NA  NA  NA  NA   NA   NA              675              386
    ## 100  NA  NA  NA  NA  NA  NA  NA   NA   NA             1673              975
    ## 101  NA  NA  NA  NA  NA  NA  NA   NA   NA              650              359
    ## 102  NA  NA  NA  NA  NA  NA  NA   NA   NA              991              600
    ## 103  NA  NA  NA  NA  NA  NA  NA   NA   NA              968              588
    ## 104  NA  NA  NA  NA  NA  NA  NA   NA   NA             2532             1567
    ## 105  NA  NA  NA  NA  NA  NA  NA   NA   NA             1919             1120
    ## 106  NA  NA  NA  NA  NA  NA  NA   NA   NA             2485             1386
    ## 107  NA  NA  NA  NA  NA  NA  NA   NA   NA             2057             1212
    ## 108  NA  NA  NA  NA  NA  NA  NA   NA   NA             3124             2075
    ## 109  NA  NA  NA  NA  NA  NA  NA   NA   NA             2767             1721
    ## 110  NA  NA  NA  NA  NA  NA  NA   NA   NA             2104             1277
    ## 111  NA  NA  NA  NA  NA  NA  NA   NA   NA             2061             1197
    ## 112  NA  NA  NA  NA  NA  NA  NA   NA   NA              257              180
    ## 113  NA  NA  NA  NA  NA  NA  NA   NA   NA             1319              769
    ## 114  NA  NA  NA  NA  NA  NA  NA   NA   NA             4362             2563
    ## 115  NA  NA  NA  NA  NA  NA  NA   NA   NA             3197             2005
    ## 116  NA  NA  NA  NA  NA  NA  NA   NA   NA             3396             2049
    ## 117  NA  NA  NA  NA  NA  NA  NA   NA   NA             1962             1161
    ## 118  NA  NA  NA  NA  NA  NA  NA   NA   NA             5160             3164
    ## 119  NA  NA  NA  NA  NA  NA  NA   NA   NA             3914             2355
    ## 120  NA  NA  NA  NA  NA  NA  NA   NA   NA             2709             1675
    ## 121  NA  NA  NA  NA  NA  NA  NA   NA   NA             6660             3659
    ## 122  NA  NA  NA  NA  NA  NA  NA   NA   NA             6508             3687
    ## 123  NA  NA  NA  NA  NA  NA  NA   NA   NA             8053             4591
    ## 124  NA  NA  NA  NA  NA  NA  NA   NA   NA             4847             2640
    ## 125  NA  NA  NA  NA  NA  NA  NA   NA   NA             5990             3120
    ## 126  NA  NA  NA  NA  NA  NA  NA   NA   NA             5308             3083
    ## 127  NA  NA  NA  NA  NA  NA  NA   NA   NA             1445              856
    ## 128  NA  NA  NA  NA  NA  NA  NA   NA   NA             2268             1359
    ## 129  NA  NA  NA  NA  NA  NA  NA   NA   NA             2575             1451
    ## 130  NA  NA  NA  NA  NA  NA  NA   NA   NA             2642             1596
    ## 131  NA  NA  NA  NA  NA  NA  NA   NA   NA             1967             1141
    ## 132  NA  NA  NA  NA  NA  NA  NA   NA   NA             4531             2734
    ## 133  NA  NA  NA  NA  NA  NA  NA   NA   NA             3545             2226
    ## 134  NA  NA  NA  NA  NA  NA  NA   NA   NA             2471             1427
    ## 135  NA  NA  NA  NA  NA  NA  NA   NA   NA             3761             2109
    ## 136  NA  NA  NA  NA  NA  NA  NA   NA   NA             3226             1840
    ## 137  NA  NA  NA  NA  NA  NA  NA   NA   NA             2439             1360
    ## 138  NA  NA  NA  NA  NA  NA  NA   NA   NA              838              890
    ## 139  NA  NA  NA  NA  NA  NA  NA   NA   NA             1060             1058
    ## 140  NA  NA  NA  NA  NA  NA  NA   NA   NA             2029             1913
    ## 141  NA  NA  NA  NA  NA  NA  NA   NA   NA             2004             1988
    ## 142  NA  NA  NA  NA  NA  NA  NA   NA   NA             1880             1801
    ## 143  NA  NA  NA  NA  NA  NA  NA   NA   NA             1239             1289
    ## 144  NA  NA  NA  NA  NA  NA  NA   NA   NA             1545             1479
    ## 145  NA  NA  NA  NA  NA  NA  NA   NA   NA              168              179
    ## 146  NA  NA  NA  NA  NA  NA  NA   NA   NA              126              134
    ## 147  NA  NA  NA  NA  NA  NA  NA   NA   NA              879              883
    ## 148  NA  NA  NA  NA  NA  NA  NA   NA   NA              603              557
    ## 149  NA  NA  NA  NA  NA  NA  NA   NA   NA             1504             1523
    ## 150  NA  NA  NA  NA  NA  NA  NA   NA   NA             1445             1437
    ## 151  NA  NA  NA  NA  NA  NA  NA   NA   NA              208              206
    ## 152  NA  NA  NA  NA  NA  NA  NA   NA   NA              328              304
    ## 153  NA  NA  NA  NA  NA  NA  NA   NA   NA             1101              976
    ## 154  NA  NA  NA  NA  NA  NA  NA   NA   NA             1119             1098
    ## 155  NA  NA  NA  NA  NA  NA  NA   NA   NA             2458             2321
    ## 156  NA  NA  NA  NA  NA  NA  NA   NA   NA             1826             1683
    ## 157  NA  NA  NA  NA  NA  NA  NA   NA   NA              727              656
    ## 158  NA  NA  NA  NA  NA  NA  NA   NA   NA             1296             1288
    ## 159  NA  NA  NA  NA  NA  NA  NA   NA   NA             2023             1910
    ## 160  NA  NA  NA  NA  NA  NA  NA   NA   NA             1398             1389
    ## 161  NA  NA  NA  NA  NA  NA  NA   NA   NA             2284             2160
    ## 162  NA  NA  NA  NA  NA  NA  NA   NA   NA             3168             2919
    ## 163  NA  NA  NA  NA  NA  NA  NA   NA   NA             1963             1894
    ## 164  NA  NA  NA  NA  NA  NA  NA   NA   NA             2300             2193
    ## 165  NA  NA  NA  NA  NA  NA  NA   NA   NA             2638             2396
    ## 166  NA  NA  NA  NA  NA  NA  NA   NA   NA             2770             2765
    ## 167  NA  NA  NA  NA  NA  NA  NA   NA   NA             2191             2109
    ## 168  NA  NA  NA  NA  NA  NA  NA   NA   NA             2266             2227
    ## 169  NA  NA  NA  NA  NA  NA  NA   NA   NA             2309             2266
    ## 170  NA  NA  NA  NA  NA  NA  NA   NA   NA             2316             2252
    ## 171  NA  NA  NA  NA  NA  NA  NA   NA   NA             2700             2678
    ## 172  NA  NA  NA  NA  NA  NA  NA   NA   NA             1823             1852
    ## 173  NA  NA  NA  NA  NA  NA  NA   NA   NA             2261             2436
    ## 174  NA  NA  NA  NA  NA  NA  NA   NA   NA             1145             1165
    ## 175  NA  NA  NA  NA  NA  NA  NA   NA   NA             1387             1331
    ## 176  NA  NA  NA  NA  NA  NA  NA   NA   NA              116              127
    ## 177  NA  NA  NA  NA  NA  NA  NA   NA   NA              423              442
    ## 178  NA  NA  NA  NA  NA  NA  NA   NA   NA              706              660
    ## 179  NA  NA  NA  NA  NA  NA  NA   NA   NA              178              188
    ## 180  NA  NA  NA  NA  NA  NA  NA   NA   NA              274              272
    ## 181  NA  NA  NA  NA  NA  NA  NA   NA   NA              176              192
    ## 182  NA  NA  NA  NA  NA  NA  NA   NA   NA              256              295
    ## 183  NA  NA  NA  NA  NA  NA  NA   NA   NA              621              562
    ## 184  NA  NA  NA  NA  NA  NA  NA   NA   NA             2056             2108
    ## 185  NA  NA  NA  NA  NA  NA  NA   NA   NA             1907             1758
    ## 186  NA  NA  NA  NA  NA  NA  NA   NA   NA             1026             1049
    ## 187  NA  NA  NA  NA  NA  NA  NA   NA   NA             2300             2242
    ## 188  NA  NA  NA  NA  NA  NA  NA   NA   NA              990              985
    ## 189  NA  NA  NA  NA  NA  NA  NA   NA   NA             1540             1460
    ## 190  NA  NA  NA  NA  NA  NA  NA   NA   NA             1140             1041
    ## 191  NA  NA  NA  NA  NA  NA  NA   NA   NA              698              595
    ## 192  NA  NA  NA  NA  NA  NA  NA   NA   NA             3050             2964
    ## 193  NA  NA  NA  NA  NA  NA  NA   NA   NA             2783             2874
    ## 194  NA  NA  NA  NA  NA  NA  NA   NA   NA             1859             1817
    ## 195  NA  NA  NA  NA  NA  NA  NA   NA   NA             2617             2596
    ## 196  NA  NA  NA  NA  NA  NA  NA   NA   NA             2017             2022
    ## 197  NA  NA  NA  NA  NA  NA  NA   NA   NA             1708             1774
    ## 198  NA  NA  NA  NA  NA  NA  NA   NA   NA             1499             1484
    ## 199  NA  NA  NA  NA  NA  NA  NA   NA   NA             2675             2616
    ## 200  NA  NA  NA  NA  NA  NA  NA   NA   NA             2787             2791
    ## 201  NA  NA  NA  NA  NA  NA  NA   NA   NA             1836             1727
    ## 202  NA  NA  NA  NA  NA  NA  NA   NA   NA             2304             2186
    ## 203  NA  NA  NA  NA  NA  NA  NA   NA   NA             1759             1638
    ## 204  NA  NA  NA  NA  NA  NA  NA   NA   NA             1606             1542
    ## 205  NA  NA  NA  NA  NA  NA  NA   NA   NA             1377             1336
    ## 206  NA  NA  NA  NA  NA  NA  NA   NA   NA             1101             1061
    ## 207  NA  NA  NA  NA  NA  NA  NA   NA   NA              840              873
    ## 208  NA  NA  NA  NA  NA  NA  NA   NA   NA             1820             1810
    ## 209  NA  NA  NA  NA  NA  NA  NA   NA   NA             1998             1836
    ## 210  NA  NA  NA  NA  NA  NA  NA   NA   NA             2249             2200
    ## 211  NA  NA  NA  NA  NA  NA  NA   NA   NA             2192             2124
    ## 212  NA  NA  NA  NA  NA  NA  NA   NA   NA             1278             1190
    ## 213  NA  NA  NA  NA  NA  NA  NA   NA   NA             2054             2057
    ## 214  NA  NA  NA  NA  NA  NA  NA   NA   NA             2361             2418
    ## 215  NA  NA  NA  NA  NA  NA  NA   NA   NA             1764             1797
    ## 216  NA  NA  NA  NA  NA  NA  NA   NA   NA             1361             1154
    ## 217  NA  NA  NA  NA  NA  NA  NA   NA   NA             2105             2064
    ## 218  NA  NA  NA  NA  NA  NA  NA   NA   NA              444              466
    ## 219  NA  NA  NA  NA  NA  NA  NA   NA   NA             1131             1008
    ## 220  NA  NA  NA  NA  NA  NA  NA   NA   NA             1614             1758
    ## 221  NA  NA  NA  NA  NA  NA  NA   NA   NA             3063             2953
    ## 222  NA  NA  NA  NA  NA  NA  NA   NA   NA             1875             1682
    ## 223  NA  NA  NA  NA  NA  NA  NA   NA   NA             2704             2409
    ## 224  NA  NA  NA  NA  NA  NA  NA   NA   NA             1946             1799
    ## 225  NA  NA  NA  NA  NA  NA  NA   NA   NA             2224             2135
    ## 226  NA  NA  NA  NA  NA  NA  NA   NA   NA             1277             1210
    ## 227  NA  NA  NA  NA  NA  NA  NA   NA   NA             2480             2417
    ## 228  NA  NA  NA  NA  NA  NA  NA   NA   NA             1413             1425
    ## 229  NA  NA  NA  NA  NA  NA  NA   NA   NA             2265             2141
    ## 230  NA  NA  NA  NA  NA  NA  NA   NA   NA             1942             1800
    ## 231  NA  NA  NA  NA  NA  NA  NA   NA   NA             1823             1804
    ## 232  NA  NA  NA  NA  NA  NA  NA   NA   NA             1678             1341
    ## 233  NA  NA  NA  NA  NA  NA  NA   NA   NA             2107             1998
    ## 234  NA  NA  NA  NA  NA  NA  NA   NA   NA             2006             1951
    ## 235  NA  NA  NA  NA  NA  NA  NA   NA   NA             2139             2060
    ## 236  NA  NA  NA  NA  NA  NA  NA   NA   NA             5035             4775
    ## 237  NA  NA  NA  NA  NA  NA  NA   NA   NA             1565             1417
    ## 238  NA  NA  NA  NA  NA  NA  NA   NA   NA             4651             4385
    ## 239  NA  NA  NA  NA  NA  NA  NA   NA   NA             3053             2953
    ## 240  NA  NA  NA  NA  NA  NA  NA   NA   NA             4162             4030
    ## 241  NA  NA  NA  NA  NA  NA  NA   NA   NA             1420             1441
    ## 242  NA  NA  NA  NA  NA  NA  NA   NA   NA             3285             3275
    ## 243  NA  NA  NA  NA  NA  NA  NA   NA   NA             3210             3055
    ## 244  NA  NA  NA  NA  NA  NA  NA   NA   NA             3427             3122
    ## 245  NA  NA  NA  NA  NA  NA  NA   NA   NA             3896             3569
    ## 246  NA  NA  NA  NA  NA  NA  NA   NA   NA             3467             3356
    ## 247  NA  NA  NA  NA  NA  NA  NA   NA   NA             1682             1703
    ## 248  NA  NA  NA  NA  NA  NA  NA   NA   NA             1949             1984
    ## 249  NA  NA  NA  NA  NA  NA  NA   NA   NA             1611             1604
    ## 250  NA  NA  NA  NA  NA  NA  NA   NA   NA             1888             1815
    ## 251  NA  NA  NA  NA  NA  NA  NA   NA   NA             1299             1284
    ## 252  NA  NA  NA  NA  NA  NA  NA   NA   NA             2689             2502
    ## 253  NA  NA  NA  NA  NA  NA  NA   NA   NA             1479             1576
    ## 254  NA  NA  NA  NA  NA  NA  NA   NA   NA             2208             2104
    ## 255  NA  NA  NA  NA  NA  NA  NA   NA   NA             3179             3085
    ## 256  NA  NA  NA  NA  NA  NA  NA   NA   NA             3311             3175
    ## 257  NA  NA  NA  NA  NA  NA  NA   NA   NA             2185             2177
    ## 258  NA  NA  NA  NA  NA  NA  NA   NA   NA             1988             1846
    ## 259  NA  NA  NA  NA  NA  NA  NA   NA   NA             1857             1849
    ## 260  NA  NA  NA  NA  NA  NA  NA   NA   NA             1241             1172
    ## 261  NA  NA  NA  NA  NA  NA  NA   NA   NA             1237             1276
    ## 262  NA  NA  NA  NA  NA  NA  NA   NA   NA             1088             1064
    ## 263  NA  NA  NA  NA  NA  NA  NA   NA   NA             1167             1112
    ## 264  NA  NA  NA  NA  NA  NA  NA   NA   NA              937              928
    ## 265  NA  NA  NA  NA  NA  NA  NA   NA   NA             1242             1187
    ## 266  NA  NA  NA  NA  NA  NA  NA   NA   NA             3258             2988
    ## 267  NA  NA  NA  NA  NA  NA  NA   NA   NA             1007              930
    ##     X40.44.Laki.Laki X40.44.Perempuan X45.49.Laki.Laki X45.49.Perempuan
    ## 1                233              210              171              158
    ## 2                 99               88               72               63
    ## 3                232              234              212              193
    ## 4                178              176              162              139
    ## 5                 73               94               67               69
    ## 6                108               80               66               62
    ## 7                130              165              176              162
    ## 8                749              798              779              766
    ## 9                914              943              871              823
    ## 10               691              691              659              631
    ## 11               447              522              463              487
    ## 12              1105             1083             1007              967
    ## 13               595              606              607              580
    ## 14              1371             1381             1236             1160
    ## 15              1172             1153             1089             1011
    ## 16               854              847              900              808
    ## 17              1481             1459             1257             1284
    ## 18              1013             1026              921              956
    ## 19              1397             1415             1331             1168
    ## 20              1204             1222             1144              989
    ## 21              1605             1721             1640             1460
    ## 22               973             1016              954              903
    ## 23              1838             1881             1694             1435
    ## 24              1305             1226             1202              940
    ## 25              1462             1442             1299             1276
    ## 26               362              315              302              278
    ## 27               442              446              449              413
    ## 28              1089             1146             1088             1087
    ## 29              1391             1437             1270             1280
    ## 30               790              727              648              667
    ## 31               903              937              860              825
    ## 32              1364             1280             1287             1189
    ## 33              1879             1891             1815             1609
    ## 34              1207             1085             1149             1037
    ## 35              1215             1153             1164             1048
    ## 36              1099             1139             1095             1051
    ## 37               408              367              409              376
    ## 38               212              180              187              179
    ## 39               657              701              618              560
    ## 40               178              190              185              158
    ## 41              1088             1198             1200             1104
    ## 42              1020             1027              916              839
    ## 43              1660             1626             1446             1404
    ## 44              1588             1673             1462             1433
    ## 45               998             1064             1040              987
    ## 46               600              589              563              566
    ## 47              1949             1952             1847             1569
    ## 48              1139             1181              972              892
    ## 49               925              982              820              795
    ## 50              1776             1841             1680             1594
    ## 51              5124            10659             6563             5925
    ## 52               572             1089              655              666
    ## 53              1635             3266             1860             1851
    ## 54              4453             8921             5122             4877
    ## 55              2303             4567             2542             2581
    ## 56              1872             3897             2391             2325
    ## 57              3355             6782             3967             3810
    ## 58              2036             4326             2502             2417
    ## 59              1561             3310             1924             1805
    ## 60              2661             5670             3519             3270
    ## 61              3810             7520             4177             4217
    ## 62              2342             4950             2968             2790
    ## 63              1635             3402             1995             1784
    ## 64              3748             7702             4373             4297
    ## 65              3123             6465             3553             3456
    ## 66              1867             3931             2296             2231
    ## 67              2093             4328             2494             2393
    ## 68              2294             4714             2626             2681
    ## 69              2523             5137             2976             2968
    ## 70              3696             7072             4293             5339
    ## 71              1121             2328             1312             1288
    ## 72              3833             7929             4572             4522
    ## 73              1668             3351             1992             2151
    ## 74              1934             3810             2204             2307
    ## 75              3703             7282             4317             4495
    ## 76              1948             3883             2238             2238
    ## 77              4133             8397             5086             4635
    ## 78              1354             2734             1674             1475
    ## 79              1743             3487             1893             2144
    ## 80              2338             4597             2608             2622
    ## 81              1605             3038             1821             1946
    ## 82              3137             6358             3675             3768
    ## 83              3746             7510             4224             4231
    ## 84              3459             6855             3950             3971
    ## 85              1683             3439             2104             1995
    ## 86              7243            14731             8822             8352
    ## 87              4130             8277             5010             4952
    ## 88               845             1748             1002              989
    ## 89               859             1671             1074             1199
    ## 90              1365             2814             1662             1633
    ## 91              1524             3105             1854             1883
    ## 92              1210             2430             1638             1637
    ## 93              2065             4181             2552             2503
    ## 94              2116             4417             2704             2529
    ## 95               775             1504              853              810
    ## 96               990             2097             1150             1063
    ## 97               891             1810              979              973
    ## 98               798             1489              806              809
    ## 99               404              790              409              434
    ## 100              932             1907             1117             1017
    ## 101              368              727              407              392
    ## 102              612             1212              773              672
    ## 103              544             1132              646              593
    ## 104             1530             3097             1775             1554
    ## 105             1095             2215             1220             1193
    ## 106             1388             2774             1536             1382
    ## 107             1161             2373             1307             1186
    ## 108             1879             3954             2275             1907
    ## 109             1579             3300             1936             1707
    ## 110             1129             2406             1371             1257
    ## 111             1167             2364             1258             1315
    ## 112              150              330              199              194
    ## 113              780             1549              850              863
    ## 114             2466             5029             2878             3001
    ## 115             1899             3904             2223             2242
    ## 116             2002             4051             2340             2242
    ## 117             1124             2285             1337             1357
    ## 118             3253             6417             3809             3580
    ## 119             2363             4718             2776             2721
    ## 120             1697             3372             1962             1961
    ## 121             3562             7221             4222             4118
    ## 122             3587             7274             4380             4400
    ## 123             4553             9144             5652             5470
    ## 124             2571             5211             3018             2971
    ## 125             3271             6391             3847             3916
    ## 126             3081             6164             3752             3624
    ## 127              852             1708             1043              951
    ## 128             1372             2731             1592             1523
    ## 129             1438             2889             1767             1695
    ## 130             1580             3176             1790             1845
    ## 131             1067             2208             1337             1282
    ## 132             2793             5527             3092             2903
    ## 133             2193             4419             2633             2619
    ## 134             1501             2928             1605             1701
    ## 135             2109             4218             2364             2404
    ## 136             1955             3795             2308             2369
    ## 137             1418             2778             1401             1509
    ## 138              948             1004              911              943
    ## 139             1086             1159             1093             1024
    ## 140             1958             1841             1623             1572
    ## 141             1901             1774             1470             1347
    ## 142             1805             1712             1598             1553
    ## 143             1238             1198             1080             1007
    ## 144             1483             1402             1346             1267
    ## 145              147              170              156              153
    ## 146              144              132              103              100
    ## 147              794              751              688              654
    ## 148              599              593              555              467
    ## 149             1505             1442             1206             1160
    ## 150             1354             1246             1168             1088
    ## 151              186              192              181              205
    ## 152              337              326              272              231
    ## 153              979              935              814              692
    ## 154             1068             1020              951              905
    ## 155             2366             2152             1935             1795
    ## 156             1614             1449             1333             1161
    ## 157              713              611              622              479
    ## 158             1198             1269             1087             1026
    ## 159             1770             1715             1393             1392
    ## 160             1261             1142             1011              879
    ## 161             2011             1854             1614             1556
    ## 162             2848             2685             2317             2103
    ## 163             1825             1711             1575             1479
    ## 164             1928             1808             1576             1454
    ## 165             2289             2012             1782             1574
    ## 166             2649             2499             2134             2134
    ## 167             2020             1873             1630             1455
    ## 168             2187             2071             1837             1727
    ## 169             2229             2124             1886             1692
    ## 170             2193             2004             1726             1529
    ## 171             2716             2641             2300             2156
    ## 172             1719             1632             1404             1307
    ## 173             2254             2130             1888             1657
    ## 174             1105             1070              963              880
    ## 175             1334             1333             1205             1145
    ## 176              120              133              148              139
    ## 177              441              470              498              445
    ## 178              616              672              670              603
    ## 179              181              195              193              189
    ## 180              261              273              291              317
    ## 181              224              195              173              164
    ## 182              289              305              267              322
    ## 183              655              560              561              494
    ## 184             2081             2038             1812             1699
    ## 185             1732             1607             1476             1257
    ## 186              959              856              730              672
    ## 187             2234             1934             1647             1554
    ## 188              970              902              786              683
    ## 189             1497             1434             1265             1120
    ## 190             1046             1020              880              842
    ## 191              578              544              450              427
    ## 192             2724             2626             2218             2013
    ## 193             2710             2587             2227             2034
    ## 194             1690             1528             1353             1171
    ## 195             2339             2219             1885             1849
    ## 196             1826             1683             1433             1315
    ## 197             1567             1468             1302             1123
    ## 198             1270             1232             1032              941
    ## 199             2525             2311             2078             1792
    ## 200             2451             2240             1926             1783
    ## 201             1584             1526             1297             1244
    ## 202             2047             1826             1533             1377
    ## 203             1662             1583             1434             1393
    ## 204             1572             1418             1290             1185
    ## 205             1271             1337             1173             1144
    ## 206             1061             1001              934              879
    ## 207              928              862              822              836
    ## 208             1727             1699             1523             1475
    ## 209             1788             1596             1477             1338
    ## 210             2193             2063             1834             1771
    ## 211             2129             2151             1745             1747
    ## 212             1205             1141              970              859
    ## 213             2049             1984             1746             1660
    ## 214             2245             2253             1810             1760
    ## 215             1826             1725             1375             1436
    ## 216             1236             1050             1016             1029
    ## 217             1952             1824             1727             1629
    ## 218              462              458              486              480
    ## 219             1034             1021              903              842
    ## 220             1704             1670             1567             1559
    ## 221             2693             2469             1999             1951
    ## 222             1649             1556             1303             1218
    ## 223             2344             2180             1856             1784
    ## 224             1742             1601             1411             1435
    ## 225             1986             1780             1718             1673
    ## 226             1109             1036              891              861
    ## 227             2223             2125             1760             1657
    ## 228             1292             1260             1036              974
    ## 229             2053             1910             1658             1658
    ## 230             1760             1586             1415             1289
    ## 231             1648             1652             1440             1248
    ## 232             1200             1042              738              860
    ## 233             1826             1835             1566             1525
    ## 234             1859             1767             1512             1583
    ## 235             1854             1753             1538             1465
    ## 236             4480             3883             3304             2804
    ## 237             1394             1136             1021              857
    ## 238             4106             3805             3289             2953
    ## 239             2637             2422             2014             1851
    ## 240             3755             3600             3011             2968
    ## 241             1345             1289             1084             1000
    ## 242             2790             2455             1908             1592
    ## 243             2723             2620             2119             2138
    ## 244             2932             2734             2276             2074
    ## 245             3349             2950             2538             2463
    ## 246             3037             2894             2376             2331
    ## 247             1542             1493             1124             1074
    ## 248             1854             1714             1270             1162
    ## 249             1461             1433             1220             1255
    ## 250             1576             1522             1286             1276
    ## 251             1168             1141              974              901
    ## 252             2296             2192             1870             1659
    ## 253             1705             1630             1327             1312
    ## 254             2035             1876             1652             1693
    ## 255             2851             2785             2423             2358
    ## 256             2982             2861             2471             2424
    ## 257             1927             1818             1586             1559
    ## 258             1807             1564             1493             1286
    ## 259             1729             1567             1369             1277
    ## 260             1029             1037              961              894
    ## 261             1195             1114              978              900
    ## 262              969              945              920              846
    ## 263             1026              977              839              800
    ## 264              857              824              705              640
    ## 265             1062             1063              984              917
    ## 266             2732             2660             2311             2222
    ## 267              874              804              701              652
    ##     X50.54.Laki.Laki X50.54.Perempuan X55.59.Laki.Laki X55.59.Perempuan
    ## 1                137              126               98              106
    ## 2                 34               29               30               39
    ## 3                150              161              139              101
    ## 4                100              119               97               83
    ## 5                 60               40               37               32
    ## 6                 61               63               37               36
    ## 7                129               97              108               90
    ## 8                715              662              614              537
    ## 9                736              679              680              510
    ## 10               611              514              539              466
    ## 11               432              426              432              329
    ## 12               901              781              742              616
    ## 13               588              522              495              435
    ## 14              1078              995              935              749
    ## 15               993              905              877              688
    ## 16               804              691              648              525
    ## 17              1120             1033              969              799
    ## 18               845              787              696              601
    ## 19              1049              857              837              650
    ## 20               871              743              737              584
    ## 21              1301              922              901              627
    ## 22               855              726              717              602
    ## 23              1349             1021              983              755
    ## 24               860              710              689              549
    ## 25              1163              920              912              731
    ## 26               274              254              224              207
    ## 27               446              360              339              288
    ## 28              1074              831              914              697
    ## 29              1193              957              949              777
    ## 30               641              513              587              459
    ## 31               810              667              661              517
    ## 32              1064              791              798              565
    ## 33              1445             1108             1168              857
    ## 34               984              746              765              551
    ## 35              1103              973             1011              786
    ## 36              1043              843              858              681
    ## 37               375              315              335              264
    ## 38               194              175              180              134
    ## 39               508              493              451              394
    ## 40               143              113              111               85
    ## 41              1084              883              841              593
    ## 42               660              573              554              484
    ## 43              1289             1148             1012              811
    ## 44              1289             1017              985              864
    ## 45               903              806              836              627
    ## 46               536              465              448              380
    ## 47              1528             1179             1175              922
    ## 48               830              663              663              547
    ## 49               727              621              535              436
    ## 50              1437             1263             1200              954
    ## 51             12488             5758             4842            10600
    ## 52              1321              533              541             1074
    ## 53              3711             1545             1453             2998
    ## 54              9999             4333             4018             8351
    ## 55              5123             2169             2132             4301
    ## 56              4716             2238             2324             4562
    ## 57              7777             3329             3023             6352
    ## 58              4919             2270             2230             4500
    ## 59              3729             1694             1628             3322
    ## 60              6789             3264             2955             6219
    ## 61              8394             3982             3799             7781
    ## 62              5758             2738             2664             5402
    ## 63              3779             1744             1476             3220
    ## 64              8670             3892             3740             7632
    ## 65              7009             3205             2994             6199
    ## 66              4527             2095             1898             3993
    ## 67              4887             1992             1989             3981
    ## 68              5307             2239             2110             4349
    ## 69              5944             2464             2316             4780
    ## 70              9632             3595             3572             7167
    ## 71              2600             1024              977             2001
    ## 72              9094             3847             3734             7581
    ## 73              4143             1894             1964             3858
    ## 74              4511             1866             1887             3753
    ## 75              8812             3826             3776             7602
    ## 76              4476             2045             2014             4059
    ## 77              9721             4374             3828             8202
    ## 78              3149             1442             1248             2690
    ## 79              4037             1657             1707             3364
    ## 80              5230             2281             2347             4628
    ## 81              3767             1788             1828             3616
    ## 82              7443             3431             3430             6861
    ## 83              8455             3698             3448             7146
    ## 84              7921             3496             3128             6624
    ## 85              4099             1956             1795             3751
    ## 86             17174             7480             6846            14326
    ## 87              9962             4345             3961             8306
    ## 88              1991              936              875             1811
    ## 89              2273             1030              997             2027
    ## 90              3295             1583             1589             3172
    ## 91              3737             1706             1696             3402
    ## 92              3275             1413             1447             2860
    ## 93              5055             2188             2123             4311
    ## 94              5233             2242             2004             4246
    ## 95              1663              737              740             1477
    ## 96              2213             1008              924             1932
    ## 97              1952              875              873             1748
    ## 98              1615              718              734             1452
    ## 99               843              386              373              759
    ## 100             2134             1030              910             1940
    ## 101              799              335              342              677
    ## 102             1445              626              586             1212
    ## 103             1239              598              522             1120
    ## 104             3329             1549             1275             2824
    ## 105             2413             1125             1016             2141
    ## 106             2918             1344             1271             2615
    ## 107             2493             1210              940             2150
    ## 108             4182             1966             1496             3462
    ## 109             3643             1651             1460             3111
    ## 110             2628             1211             1053             2264
    ## 111             2573             1221             1140             2361
    ## 112              393              179              191              370
    ## 113             1713              770              724             1494
    ## 114             5879             2739             2662             5401
    ## 115             4465             2026             1978             4004
    ## 116             4582             2094             1884             3978
    ## 117             2694             1256             1232             2488
    ## 118             7389             3204             3040             6244
    ## 119             5497             2372             2247             4619
    ## 120             3923             1696             1660             3356
    ## 121             8340             3733             3684             7417
    ## 122             8780             3925             3656             7581
    ## 123            11122             4531             4325             8856
    ## 124             5989             2585             2455             5040
    ## 125             7763             3372             3369             6741
    ## 126             7376             3447             3319             6766
    ## 127             1994              875              840             1715
    ## 128             3115             1361             1221             2582
    ## 129             3462             1531             1428             2959
    ## 130             3635             1766             1721             3487
    ## 131             2619             1188             1135             2323
    ## 132             5995             2763             2693             5456
    ## 133             5252             2156             2142             4298
    ## 134             3306             1535             1484             3019
    ## 135             4768             2270             2224             4494
    ## 136             4677             1988             1951             3939
    ## 137             2910             1306             1165             2471
    ## 138              713              728              532              514
    ## 139              837              851              536              610
    ## 140             1216             1205              884              853
    ## 141             1087             1134              839              935
    ## 142             1305             1258              982             1002
    ## 143              790              757              607              634
    ## 144              999             1039              823              828
    ## 145              115              117               84               74
    ## 146               83               94               79               65
    ## 147              548              567              444              427
    ## 148              364              346              288              262
    ## 149              967              948              664              728
    ## 150              921              893              682              725
    ## 151              168              152              140              157
    ## 152              212              190              161              133
    ## 153              582              589              420              396
    ## 154              719              713              566              469
    ## 155             1440             1422             1089             1042
    ## 156              984              897              694              677
    ## 157              426              390              318              286
    ## 158              791              783              542              548
    ## 159             1135             1168              819              852
    ## 160              716              696              516              461
    ## 161             1111             1195              882              902
    ## 162             1687             1686             1213             1250
    ## 163             1150             1141              829              888
    ## 164             1186             1242              914              899
    ## 165             1355             1299              957              979
    ## 166             1699             1756             1296             1445
    ## 167             1211             1197              909              821
    ## 168             1416             1293             1018              889
    ## 169             1471             1313             1056             1013
    ## 170             1254             1303              941              942
    ## 171             1706             1631             1230             1256
    ## 172             1108             1211              872              855
    ## 173             1286             1266              935              943
    ## 174              775              686              495              470
    ## 175              986              913              612              589
    ## 176              134              119              100              106
    ## 177              360              324              288              283
    ## 178              523              476              391              375
    ## 179              162              154              104              120
    ## 180              249              265              181              196
    ## 181              156              128              109              104
    ## 182              272              291              220              214
    ## 183              448              411              342              324
    ## 184             1344             1192             1012             1042
    ## 185             1075              995              754              683
    ## 186              519              546              450              470
    ## 187             1152             1188              893              954
    ## 188              517              527              400              439
    ## 189              926              862              646              563
    ## 190              661              659              478              484
    ## 191              346              372              259              272
    ## 192             1675             1695             1273             1249
    ## 193             1515             1460             1107             1139
    ## 194              967              919              730              647
    ## 195             1452             1478             1127             1191
    ## 196             1072             1107              802              824
    ## 197              966              927              750              656
    ## 198              684              672              540              611
    ## 199             1516             1440             1094             1135
    ## 200             1405             1436             1151             1267
    ## 201             1055             1048              844              858
    ## 202             1181             1146              840              848
    ## 203             1149             1074              837              848
    ## 204              981              938              717              711
    ## 205              868              899              676              690
    ## 206              790              722              577              563
    ## 207              676              661              471              498
    ## 208             1192             1185              864              870
    ## 209             1143             1019              748              703
    ## 210             1467             1357             1032             1066
    ## 211             1384             1321              948              929
    ## 212              780              712              522              503
    ## 213             1231             1250              941              946
    ## 214             1273             1270              923             1015
    ## 215             1112             1045              789              860
    ## 216              864              848              694              601
    ## 217             1328             1325              974             1048
    ## 218              446              374              333              347
    ## 219              716              730              619              604
    ## 220             1200             1253              934              963
    ## 221             1642             1721             1362             1454
    ## 222              988              952              782              780
    ## 223             1480             1463             1170             1126
    ## 224             1146             1105              848              811
    ## 225             1303             1267              922              957
    ## 226              720              682              518              576
    ## 227             1284             1295             1019             1041
    ## 228              766              763              677              609
    ## 229             1273             1265              983             1026
    ## 230             1085             1146              858              794
    ## 231             1085             1068              761              810
    ## 232              769              582              443              389
    ## 233             1226             1190              947              967
    ## 234             1295             1311             1075              811
    ## 235             1213             1204             1017              916
    ## 236             2324             2110             1561             1288
    ## 237              776              680              595              438
    ## 238             2397             2565             2063             1920
    ## 239             1485             1504             1252             1129
    ## 240             2454             2595             2134             1992
    ## 241              842              804              631              586
    ## 242             1242             1142              917              821
    ## 243             1718             1726             1383             1480
    ## 244             1757             1711             1338             1560
    ## 245             1946             1965             1636             1620
    ## 246             1867             2106             1690             1783
    ## 247              747              874              647              847
    ## 248              784              899              611              840
    ## 249              976             1021              868              907
    ## 250             1036             1109              866              879
    ## 251              698              713              588              530
    ## 252             1396             1373             1017             1108
    ## 253             1088              872              642              461
    ## 254             1323             1423             1106             1095
    ## 255             1934             1939             1468             1511
    ## 256             1915             1947             1497             1564
    ## 257             1216             1408             1149             1152
    ## 258             1074             1067              828              816
    ## 259             1087              989              782              807
    ## 260              696              702              539              469
    ## 261              676              587              452              397
    ## 262              713              607              453              391
    ## 263              668              622              482              482
    ## 264              512              471              392              354
    ## 265              731              841              596              476
    ## 266             1766             1788             1376             1308
    ## 267              493              503              416              390
    ##     X60.64.Laki.Laki X60.64.Perempuan X65.69.Laki.Laki X65.69.Perempuan
    ## 1                 72               65               36               33
    ## 2                 29               24               12               21
    ## 3                 73               56               18               35
    ## 4                 58               56               40               54
    ## 5                 22               13               18               15
    ## 6                 32               26               21               14
    ## 7                 88               42               68               34
    ## 8                555              343              413              215
    ## 9                544              421              398              235
    ## 10               428              279              328              160
    ## 11               353              263              246              140
    ## 12               597              404              409              215
    ## 13               486              401              407              265
    ## 14               793              487              567              308
    ## 15               743              515              542              272
    ## 16               539              388              458              240
    ## 17               729              528              498              310
    ## 18               608              410              414              191
    ## 19               685              448              448              271
    ## 20               619              346              365              218
    ## 21               650              418              521              279
    ## 22               585              396              460              282
    ## 23               770              498              571              318
    ## 24               636              383              465              279
    ## 25               719              424              395              197
    ## 26               184              152              126               84
    ## 27               271              191              200               96
    ## 28               666              436              428              203
    ## 29               760              483              479              272
    ## 30               459              310              371              157
    ## 31               572              382              357              210
    ## 32               638              457              474              254
    ## 33               874              569              592              294
    ## 34               552              376              373              216
    ## 35               749              448              453              268
    ## 36               657              457              419              220
    ## 37               256              167              185               85
    ## 38               163               82              125               79
    ## 39               383              251              253              136
    ## 40                88               63               49               33
    ## 41               559              358              385              198
    ## 42               410              286              281              175
    ## 43               736              420              425              242
    ## 44               761              493              467              260
    ## 45               647              450              485              256
    ## 46               376              245              274              140
    ## 47               939              590              670              318
    ## 48               495              300              339              176
    ## 49               421              259              257              139
    ## 50               955              646              627              309
    ## 51              4938             4051             8989             3967
    ## 52               482              474              956              354
    ## 53              1359             1273             2632             1102
    ## 54              3647             3306             6953             3023
    ## 55              1712             1746             3458             1380
    ## 56              1957             1832             3789             1508
    ## 57              2702             2408             5110             2213
    ## 58              1944             1704             3648             1467
    ## 59              1592             1401             2993             1267
    ## 60              2815             2607             5422             2193
    ## 61              3272             3124             6396             2722
    ## 62              2338             2234             4572             1858
    ## 63              1424             1329             2753             1256
    ## 64              3301             3007             6308             2420
    ## 65              2869             2667             5536             2410
    ## 66              1829             1643             3472             1398
    ## 67              1681             1538             3219             1289
    ## 68              1925             1641             3566             1423
    ## 69              2021             1793             3814             1515
    ## 70              2693             2184             4877             1606
    ## 71               926              891             1817              703
    ## 72              3196             2750             5946             2398
    ## 73              1786             1685             3471             1383
    ## 74              1623             1482             3105             1206
    ## 75              3344             3201             6545             2439
    ## 76              1806             1687             3493             1549
    ## 77              3702             3195             6897             2906
    ## 78              1286             1048             2334             1034
    ## 79              1307             1458             2765             1122
    ## 80              2052             1973             4025             1873
    ## 81              1810             1807             3617             1428
    ## 82              3040             2816             5856             2320
    ## 83              3221             2989             6210             2630
    ## 84              3004             2691             5695             2235
    ## 85              1719             1553             3272             1411
    ## 86              6333             5476            11809             4758
    ## 87              3736             3428             7164             2806
    ## 88               983              842             1825              837
    ## 89               843              806             1649              609
    ## 90              1594             1456             3050             1367
    ## 91              1570             1484             3054             1280
    ## 92              1268             1244             2512             1012
    ## 93              1860             1671             3531             1438
    ## 94              1908             1611             3519             1537
    ## 95               729              699             1428              633
    ## 96               914              871             1785              836
    ## 97               861              738             1599              785
    ## 98               651              682             1333              605
    ## 99               335              335              670              322
    ## 100              941              778             1719              817
    ## 101              318              344              662              335
    ## 102              601              494             1095              489
    ## 103              544              451              995              460
    ## 104             1251             1022             2273             1035
    ## 105              995              910             1905              903
    ## 106             1270             1189             2459             1126
    ## 107             1103              802             1905              856
    ## 108             1675             1248             2923             1265
    ## 109             1505             1371             2876             1332
    ## 110             1103              906             2009              887
    ## 111             1118             1088             2206              998
    ## 112              170              169              339              162
    ## 113              744              688             1432              630
    ## 114             2435             2345             4780             1923
    ## 115             1932             1647             3579             1370
    ## 116             1798             1596             3394             1370
    ## 117             1107             1055             2162              962
    ## 118             2616             2510             5126             2114
    ## 119             2021             1903             3924             1653
    ## 120             1459             1296             2755             1086
    ## 121             3432             3175             6607             2636
    ## 122             3374             3051             6425             2513
    ## 123             3806             3460             7266             2946
    ## 124             2384             2098             4482             1732
    ## 125             3229             3207             6436             2735
    ## 126             3187             2912             6099             2571
    ## 127              825              743             1568              677
    ## 128             1228             1076             2304              974
    ## 129             1442             1366             2808             1247
    ## 130             1783             1694             3477             1539
    ## 131             1095              974             2069              917
    ## 132             2440             2192             4632             1919
    ## 133             2010             1730             3740             1496
    ## 134             1380             1270             2650             1056
    ## 135             1946             1782             3728             1576
    ## 136             1772             1646             3418             1427
    ## 137             1098             1028             2126              940
    ## 138              342              367              198              301
    ## 139              431              453              230              312
    ## 140              614              629              314              378
    ## 141              619              648              375              441
    ## 142              670              654              348              421
    ## 143              361              414              212              288
    ## 144              538              508              297              298
    ## 145               59               54               23               43
    ## 146               46               59               34               34
    ## 147              295              238              119              137
    ## 148              145              199              107              130
    ## 149              440              470              247              331
    ## 150              479              444              236              248
    ## 151              114              115               62               78
    ## 152               98               98               58               71
    ## 153              276              241              157              193
    ## 154              288              250              151              178
    ## 155              694              676              408              422
    ## 156              448              439              232              275
    ## 157              212              211              126              102
    ## 158              375              467              279              365
    ## 159              609              588              317              352
    ## 160              290              333              189              201
    ## 161              597              613              381              383
    ## 162              883              783              453              512
    ## 163              562              548              357              373
    ## 164              588              492              318              272
    ## 165              720              662              423              399
    ## 166              989             1023              667              655
    ## 167              565              587              357              395
    ## 168              655              630              372              427
    ## 169              641              638              361              418
    ## 170              697              717              437              509
    ## 171              825              843              498              528
    ## 172              657              580              360              330
    ## 173              668              613              395              517
    ## 174              310              309              180              216
    ## 175              403              365              240              277
    ## 176               74               64               37               43
    ## 177              175              173              120              121
    ## 178              246              227              133              137
    ## 179               82               91               45               51
    ## 180              120              149               83               87
    ## 181               68               77               43               33
    ## 182              141              140               67               88
    ## 183              233              225              108              162
    ## 184              644              710              416              477
    ## 185              506              477              270              292
    ## 186              307              287              189              170
    ## 187              625              608              410              457
    ## 188              294              309              174              200
    ## 189              386              438              261              323
    ## 190              368              319              203              214
    ## 191              207              192              121              123
    ## 192              811              683              431              425
    ## 193              780              762              417              556
    ## 194              478              380              236              233
    ## 195              875              729              418              387
    ## 196              599              502              281              327
    ## 197              422              343              211              190
    ## 198              413              467              281              290
    ## 199              808              749              433              454
    ## 200              862              807              490              425
    ## 201              555              516              314              303
    ## 202              631              542              371              333
    ## 203              575              556              280              378
    ## 204              479              500              266              333
    ## 205              450              450              249              276
    ## 206              351              398              181              240
    ## 207              307              341              183              251
    ## 208              576              641              369              434
    ## 209              519              506              303              335
    ## 210              705              709              362              421
    ## 211              549              661              417              563
    ## 212              317              324              197              169
    ## 213              588              639              409              540
    ## 214              714              831              539              637
    ## 215              584              675              422              572
    ## 216              436              409              205              294
    ## 217              628              697              332              420
    ## 218              247              228              139              142
    ## 219              387              380              193              257
    ## 220              662              683              366              495
    ## 221             1056             1046              700              653
    ## 222              533              503              307              337
    ## 223              742              765              403              441
    ## 224              473              483              257              336
    ## 225              645              585              338              331
    ## 226              356              305              189              174
    ## 227              793              632              394              363
    ## 228              418              381              221              187
    ## 229              687              711              376              449
    ## 230              557              517              282              361
    ## 231              593              590              302              284
    ## 232              228              228              138              142
    ## 233              688              512              328              286
    ## 234              590              505              267              271
    ## 235              574              476              269              243
    ## 236              955              639              384              375
    ## 237              322              214              122               86
    ## 238             1365              991              606              446
    ## 239              832              558              339              269
    ## 240             1476             1170              645              507
    ## 241              388              300              194              181
    ## 242              543              406              253              218
    ## 243             1077             1069              646              625
    ## 244             1145              997              675              625
    ## 245             1127             1050              657              561
    ## 246             1363             1157              735              605
    ## 247              527              755              495              471
    ## 248              496              818              531              583
    ## 249              629              592              329              270
    ## 250              632              574              337              284
    ## 251              383              316              170              164
    ## 252              812              723              427              377
    ## 253              275              284              156              177
    ## 254              750              701              424              392
    ## 255             1033              714              413              330
    ## 256             1033              972              560              522
    ## 257              787              606              328              315
    ## 258              606              481              258              263
    ## 259              539              493              301              233
    ## 260              374              278              164              177
    ## 261              267              235              161              133
    ## 262              271              227              131              109
    ## 263              302              291              173              137
    ## 264              254              211              124              115
    ## 265              377              250              169              179
    ## 266              959              739              393              385
    ## 267              279              214              110              153
    ##     X70.74.Laki.Laki X70.74.Perempuan X.75.Laki.Laki X.75..Perempuan
    ## 1                 33               20             13              27
    ## 2                 13                5              5               8
    ## 3                 24               25             18              26
    ## 4                 26               27             16              13
    ## 5                 10               18             11              17
    ## 6                 17               11              8               7
    ## 7                 37               32             34              23
    ## 8                259              142            214             165
    ## 9                241              132            215             159
    ## 10               215              116            150             121
    ## 11               152              100            136              72
    ## 12               255              156            196             138
    ## 13               243              147            203             136
    ## 14               344              199            258             156
    ## 15               360              187            284             180
    ## 16               289              184            203             168
    ## 17               316              188            252             157
    ## 18               262              163            199             140
    ## 19               259              186            179              98
    ## 20               267              147            171             100
    ## 21               358              289            294             180
    ## 22               273              169            192             130
    ## 23               462              306            284             180
    ## 24               309              227            205             113
    ## 25               295              179            209             133
    ## 26                73               40             50              31
    ## 27               122               76             88              61
    ## 28               264              142            169             121
    ## 29               344              193            234             156
    ## 30               192              105            153              95
    ## 31               238              146            173             112
    ## 32               396              267            276             217
    ## 33               440              285            322             235
    ## 34               261              166            199             140
    ## 35               278              149            210             166
    ## 36               261              144            195             106
    ## 37               100               57             70              56
    ## 38                97               63             60              68
    ## 39               171               85            121              61
    ## 40                47               28             29              27
    ## 41               296              161            239             213
    ## 42               185              111            130              67
    ## 43               310              170            215             121
    ## 44               284              172            204             124
    ## 45               310              170            203             122
    ## 46               149               90            123              71
    ## 47               450              285            320             201
    ## 48               189              144            175              92
    ## 49               169              124            130              64
    ## 50               363              221            281             156
    ## 51              3072             7039           2941            2426
    ## 52               301              655            277             273
    ## 53              1083             2185            979             943
    ## 54              2790             5813           2574            2520
    ## 55              1493             2873           1337            1583
    ## 56              1410             2918           1127            1027
    ## 57              2180             4393           1832            2082
    ## 58              1405             2872           1067            1107
    ## 59              1197             2464            998             954
    ## 60              1932             4125           1483            1405
    ## 61              2820             5542           2219            2525
    ## 62              1749             3607           1347            1235
    ## 63              1114             2370           1007             876
    ## 64              2257             4677           1853            1897
    ## 65              2310             4720           1719            1688
    ## 66              1246             2644            996            1023
    ## 67              1173             2462            936             943
    ## 68              1339             2762           1036            1121
    ## 69              1441             2956           1188            1210
    ## 70              1399             3005           1075            1086
    ## 71               694             1397            588             549
    ## 72              2127             4525           1870            1844
    ## 73              1282             2665           1002             939
    ## 74              1118             2324            846             884
    ## 75              2297             4736           1855            1816
    ## 76              1401             2950           1205            1211
    ## 77              2583             5489           2322            2104
    ## 78               886             1920            787             676
    ## 79              1204             2326            985            1358
    ## 80              1865             3738           1708            1774
    ## 81              1369             2797           1000             999
    ## 82              2195             4515           1663            1761
    ## 83              2544             5174           2042            2001
    ## 84              2089             4324           1790            1604
    ## 85              1259             2670           1041             903
    ## 86              4475             9233           3959            3526
    ## 87              2614             5420           2078            1973
    ## 88               816             1653            661             629
    ## 89               658             1267            523             546
    ## 90              1263             2630            961             953
    ## 91              1232             2512            958             947
    ## 92               951             1963            662             722
    ## 93              1323             2761           1181            1170
    ## 94              1320             2857           1204            1131
    ## 95               664             1297            580             569
    ## 96               832             1668            717             685
    ## 97               698             1483            672             622
    ## 98               552             1157            475             479
    ## 99               313              635            297             299
    ## 100              725             1542            662             578
    ## 101              344              679            325             330
    ## 102              405              894            402             362
    ## 103              425              885            385             368
    ## 104              841             1876            808             746
    ## 105              742             1645            732             624
    ## 106             1042             2168            954             955
    ## 107              704             1560            683             579
    ## 108              994             2259            898             827
    ## 109             1130             2462           1019             922
    ## 110              793             1680            715             675
    ## 111              939             1937            930             914
    ## 112              162              324            156             142
    ## 113              577             1207            528             518
    ## 114             1881             3804           1551            1538
    ## 115             1381             2751           1047            1082
    ## 116             1306             2676           1078             964
    ## 117              909             1871            683             674
    ## 118             2023             4137           1706            1839
    ## 119             1570             3223           1303            1378
    ## 120             1138             2224            954             947
    ## 121             2634             5270           2047            1888
    ## 122             2261             4774           1821            1510
    ## 123             2632             5578           2048            2046
    ## 124             1518             3250           1241            1084
    ## 125             2602             5337           2005            1668
    ## 126             2325             4896           1903            1921
    ## 127              672             1349            579             593
    ## 128              986             1960            796             769
    ## 129             1117             2364            901             956
    ## 130             1381             2920           1093            1057
    ## 131              780             1697            672             618
    ## 132             1859             3778           1517            1385
    ## 133             1339             2835           1087            1153
    ## 134              966             2022            790             840
    ## 135             1435             3011           1198            1181
    ## 136             1331             2758           1026            1124
    ## 137              936             1876            811             852
    ## 138              184              259            189             288
    ## 139              211              265            209             268
    ## 140              241              300            206             216
    ## 141              259              330            204             270
    ## 142              254              335            223             322
    ## 143              218              229            127             178
    ## 144              175              274            188             244
    ## 145               24               29             38              32
    ## 146               29               27             18              32
    ## 147               86              153             92             105
    ## 148               81              115             64              96
    ## 149              212              249            151             191
    ## 150              136              217            107             157
    ## 151               55               45             37              84
    ## 152               53               45             56              47
    ## 153              125              137             84              75
    ## 154              101              115             98             110
    ## 155              291              277            197             238
    ## 156              168              133             99             119
    ## 157               63               72             49              31
    ## 158              283              249            201             208
    ## 159              253              253            183             219
    ## 160              137              103             78              81
    ## 161              294              273            169             189
    ## 162              339              330            191             245
    ## 163              272              258            182             194
    ## 164              183              176            122             114
    ## 165              259              252            161             190
    ## 166              461              410            382             427
    ## 167              265              217            158             157
    ## 168              274              320            209             226
    ## 169              294              263            182             214
    ## 170              356              260            179             179
    ## 171              372              412            353             386
    ## 172              233              262            235             253
    ## 173              381              329            242             230
    ## 174              144              184            132             176
    ## 175              162              192            163             199
    ## 176               26               33             49              79
    ## 177               81               98            106             150
    ## 178               93              112             97             129
    ## 179               38               49             72              94
    ## 180               48               70             60             125
    ## 181               30               38             37              49
    ## 182               49               66             45             102
    ## 183               82              112             95             131
    ## 184              301              325            236             274
    ## 185              222              210            132             157
    ## 186              109               96             77              78
    ## 187              305              269            196             209
    ## 188              154              126             69              80
    ## 189              215              231            157             170
    ## 190              131              146            105             122
    ## 191               72               68             44              65
    ## 192              275              240            169             201
    ## 193              431              289            213             231
    ## 194              155              129            100              98
    ## 195              268              223            140             200
    ## 196              237              213            127             135
    ## 197              139              131            103             123
    ## 198              216              146            100             108
    ## 199              324              316            207             266
    ## 200              290              233            159             173
    ## 201              188              188            106             162
    ## 202              241              213            138             136
    ## 203              231              270            161             257
    ## 204              197              214            143             202
    ## 205              172              219            111             185
    ## 206              151              169            131             204
    ## 207              155              175             92             180
    ## 208              280              332            230             252
    ## 209              205              203            172             182
    ## 210              285              312            196             340
    ## 211              357              351            246             273
    ## 212              116              101             75              91
    ## 213              335              364            289             362
    ## 214              423              420            299             319
    ## 215              363              364            288             334
    ## 216              151              173            121             159
    ## 217              262              324            204             320
    ## 218               88              109             95             138
    ## 219              143              201            135             161
    ## 220              285              376            277             418
    ## 221              486              423            319             299
    ## 222              225              220            138             172
    ## 223              307              350            228             247
    ## 224              224              218            136             243
    ## 225              228              197            127             184
    ## 226              138              115             72             112
    ## 227              238              242            143             166
    ## 228              123              119             72             111
    ## 229              279              265            174             244
    ## 230              211              228            154             204
    ## 231              230              212            136             206
    ## 232              104               70             44              59
    ## 233              184              161            120             136
    ## 234              193              154             98             128
    ## 235              168              132             91             139
    ## 236              248              245            159             181
    ## 237               71               86             61              67
    ## 238              339              260            192             208
    ## 239              183              168            102              97
    ## 240              423              280            195             232
    ## 241              114               91             63              70
    ## 242              139              138             98              97
    ## 243              428              352            235             268
    ## 244              414              327            234             245
    ## 245              443              401            200             278
    ## 246              458              344            221             299
    ## 247              370              280            178             161
    ## 248              441              326            197             213
    ## 249              184              167            102             123
    ## 250              211              176            111             146
    ## 251              116               95             55              66
    ## 252              264              217            160             156
    ## 253              115               89             55              63
    ## 254              306              267            216             227
    ## 255              203              207            117             147
    ## 256              453              294            185             250
    ## 257              221              163            116             153
    ## 258              178              128             83             104
    ## 259              164              119            103             120
    ## 260              112              101             61             110
    ## 261               77               90             52              62
    ## 262               80              105             42              82
    ## 263              118               94             52              51
    ## 264               64               83             59              64
    ## 265              108               96             70              84
    ## 266              293              291            160             165
    ## 267              101               53             45              44

Membaca Dataset File Excel dengan read.xlsx

``` r
library(openxlsx)
```

    ## Warning: package 'openxlsx' was built under R version 4.0.5

``` r
#Membaca dataset dengan read.xlsx dan dimasukkan ke variable penduduk.dki
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
str(penduduk.dki.xlsx)
```

    ## 'data.frame':    267 obs. of  25 variables:
    ##  $ TAHUN               : num  2013 2013 2013 2013 2013 ...
    ##  $ NAMA.PROVINSI       : chr  "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" "PROVINSI DKI JAKARTA" ...
    ##  $ NAMA.KABUPATEN/KOTA : chr  "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" ...
    ##  $ NAMA.KECAMATAN      : chr  "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU SLT" ...
    ##  $ NAMA.KELURAHAN      : chr  "P. PANGGANG" "P. KELAPA" "P. HARAPAN" "P. UNTUNG JAWA" ...
    ##  $ LUAS.WILAYAH.(KM2)  : num  0.91 3.76 3.59 0.59 1.57 1.39 2.58 1.26 1.12 1.14 ...
    ##  $ KEPADATAN.(JIWA/KM2): num  6779 1705 628 3625 3084 ...
    ##  $ 35-39.Laki-Laki     : num  231 84 255 199 98 113 166 850 954 752 ...
    ##  $ 35-39.Perempuan     : num  235 88 238 185 75 112 174 748 920 675 ...
    ##  $ 40-44.Laki-Laki     : num  233 99 232 178 73 108 130 749 914 691 ...
    ##  $ 40-44.Perempuan     : num  210 88 234 176 94 80 165 798 943 691 ...
    ##  $ 45-49.Laki-Laki     : num  171 72 212 162 67 66 176 779 871 659 ...
    ##  $ 45-49.Perempuan     : num  158 63 193 139 69 62 162 766 823 631 ...
    ##  $ 50-54.Laki-Laki     : num  137 34 150 100 60 61 129 715 736 611 ...
    ##  $ 50-54.Perempuan     : num  126 29 161 119 40 63 97 662 679 514 ...
    ##  $ 55-59.Laki-Laki     : num  98 30 139 97 37 37 108 614 680 539 ...
    ##  $ 55-59.Perempuan     : num  106 39 101 83 32 36 90 537 510 466 ...
    ##  $ 60-64.Laki-Laki     : num  72 29 73 58 22 32 88 555 544 428 ...
    ##  $ 60-64.Perempuan     : num  65 24 56 56 13 26 42 343 421 279 ...
    ##  $ 65-69.Laki-Laki     : num  36 12 18 40 18 21 68 413 398 328 ...
    ##  $ 65-69.Perempuan     : num  33 21 35 54 15 14 34 215 235 160 ...
    ##  $ 70-74.Laki-Laki     : num  33 13 24 26 10 17 37 259 241 215 ...
    ##  $ 70-74.Perempuan     : num  20 5 25 27 18 11 32 142 132 116 ...
    ##  $ >75.Laki-Laki       : num  13 5 18 16 11 8 34 214 215 150 ...
    ##  $ >75.Perempuan       : num  27 8 26 13 17 7 23 165 159 121 ...

Function names

``` r
#Membaca dataset csv
penduduk.dki.csv <-read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
#Menggunakan names untuk variable penduduk.dki.csv
names(penduduk.dki.csv)
```

    ##  [1] "TAHUN"                "NAMA.PROVINSI"        "NAMA.KABUPATEN.KOTA" 
    ##  [4] "NAMA.KECAMATAN"       "NAMA.KELURAHAN"       "LUAS.WILAYAH..KM2."  
    ##  [7] "KEPADATAN..JIWA.KM2." "X"                    "X.1"                 
    ## [10] "X.2"                  "X.3"                  "X.4"                 
    ## [13] "X.5"                  "X.6"                  "X.7"                 
    ## [16] "X.8"                  "X.9"                  "X.10"                
    ## [19] "X.11"                 "X35.39.Laki.Laki"     "X35.39.Perempuan"    
    ## [22] "X40.44.Laki.Laki"     "X40.44.Perempuan"     "X45.49.Laki.Laki"    
    ## [25] "X45.49.Perempuan"     "X50.54.Laki.Laki"     "X50.54.Perempuan"    
    ## [28] "X55.59.Laki.Laki"     "X55.59.Perempuan"     "X60.64.Laki.Laki"    
    ## [31] "X60.64.Perempuan"     "X65.69.Laki.Laki"     "X65.69.Perempuan"    
    ## [34] "X70.74.Laki.Laki"     "X70.74.Perempuan"     "X.75.Laki.Laki"      
    ## [37] "X.75..Perempuan"

Merubah Satu Nama Kolom

``` r
#Membaca dataset csv
penduduk.dki.csv <-read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
names(penduduk.dki.csv)[1] <- "PERIODE"
names(penduduk.dki.csv)[2] <- "PROPINSI"
names(penduduk.dki.csv)
```

    ##  [1] "PERIODE"              "PROPINSI"             "NAMA.KABUPATEN.KOTA" 
    ##  [4] "NAMA.KECAMATAN"       "NAMA.KELURAHAN"       "LUAS.WILAYAH..KM2."  
    ##  [7] "KEPADATAN..JIWA.KM2." "X"                    "X.1"                 
    ## [10] "X.2"                  "X.3"                  "X.4"                 
    ## [13] "X.5"                  "X.6"                  "X.7"                 
    ## [16] "X.8"                  "X.9"                  "X.10"                
    ## [19] "X.11"                 "X35.39.Laki.Laki"     "X35.39.Perempuan"    
    ## [22] "X40.44.Laki.Laki"     "X40.44.Perempuan"     "X45.49.Laki.Laki"    
    ## [25] "X45.49.Perempuan"     "X50.54.Laki.Laki"     "X50.54.Perempuan"    
    ## [28] "X55.59.Laki.Laki"     "X55.59.Perempuan"     "X60.64.Laki.Laki"    
    ## [31] "X60.64.Perempuan"     "X65.69.Laki.Laki"     "X65.69.Perempuan"    
    ## [34] "X70.74.Laki.Laki"     "X70.74.Perempuan"     "X.75.Laki.Laki"      
    ## [37] "X.75..Perempuan"

Merubah Sejumlah Nama Kolom

``` r
#Membaca dataset csv
penduduk.dki.csv <-read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
names(penduduk.dki.csv)[c(1:2)] <- c("PERIODE", "PROPINSI")
names(penduduk.dki.csv)
```

    ##  [1] "PERIODE"              "PROPINSI"             "NAMA.KABUPATEN.KOTA" 
    ##  [4] "NAMA.KECAMATAN"       "NAMA.KELURAHAN"       "LUAS.WILAYAH..KM2."  
    ##  [7] "KEPADATAN..JIWA.KM2." "X"                    "X.1"                 
    ## [10] "X.2"                  "X.3"                  "X.4"                 
    ## [13] "X.5"                  "X.6"                  "X.7"                 
    ## [16] "X.8"                  "X.9"                  "X.10"                
    ## [19] "X.11"                 "X35.39.Laki.Laki"     "X35.39.Perempuan"    
    ## [22] "X40.44.Laki.Laki"     "X40.44.Perempuan"     "X45.49.Laki.Laki"    
    ## [25] "X45.49.Perempuan"     "X50.54.Laki.Laki"     "X50.54.Perempuan"    
    ## [28] "X55.59.Laki.Laki"     "X55.59.Perempuan"     "X60.64.Laki.Laki"    
    ## [31] "X60.64.Perempuan"     "X65.69.Laki.Laki"     "X65.69.Perempuan"    
    ## [34] "X70.74.Laki.Laki"     "X70.74.Perempuan"     "X.75.Laki.Laki"      
    ## [37] "X.75..Perempuan"

Membuang Kolom dengan Bantuan Operator %in%

``` r
#Membaca dataset csv
penduduk.dki.csv <-read.csv("https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.csv", sep=",")
#Membuang kolom X, X.1, X.2 s/d X.11
penduduk.dki.csv <- penduduk.dki.csv[,!names(penduduk.dki.csv) %in% c("X", "X.1","X.2","X.3","X.4","X.5","X.6","X.7","X.8","X.9","X.10","X.11")]
names(penduduk.dki.csv)
```

    ##  [1] "TAHUN"                "NAMA.PROVINSI"        "NAMA.KABUPATEN.KOTA" 
    ##  [4] "NAMA.KECAMATAN"       "NAMA.KELURAHAN"       "LUAS.WILAYAH..KM2."  
    ##  [7] "KEPADATAN..JIWA.KM2." "X35.39.Laki.Laki"     "X35.39.Perempuan"    
    ## [10] "X40.44.Laki.Laki"     "X40.44.Perempuan"     "X45.49.Laki.Laki"    
    ## [13] "X45.49.Perempuan"     "X50.54.Laki.Laki"     "X50.54.Perempuan"    
    ## [16] "X55.59.Laki.Laki"     "X55.59.Perempuan"     "X60.64.Laki.Laki"    
    ## [19] "X60.64.Perempuan"     "X65.69.Laki.Laki"     "X65.69.Perempuan"    
    ## [22] "X70.74.Laki.Laki"     "X70.74.Perempuan"     "X.75.Laki.Laki"      
    ## [25] "X.75..Perempuan"

Merubah Tipe Kolom menjadi Factor

``` r
library(openxlsx)
#Membaca dataset dengan read.xlsx dan dimasukkan ke variable penduduk.dki
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
penduduk.dki.xlsx$NAMA.PROVINSI<-as.factor(penduduk.dki.xlsx$NAMA.PROVINSI)
str(penduduk.dki.xlsx)
```

    ## 'data.frame':    267 obs. of  25 variables:
    ##  $ TAHUN               : num  2013 2013 2013 2013 2013 ...
    ##  $ NAMA.PROVINSI       : Factor w/ 1 level "PROVINSI DKI JAKARTA": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ NAMA.KABUPATEN/KOTA : chr  "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" "KAB.ADM.KEP.SERIBU" ...
    ##  $ NAMA.KECAMATAN      : chr  "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU UTR" "KEP. SERIBU SLT" ...
    ##  $ NAMA.KELURAHAN      : chr  "P. PANGGANG" "P. KELAPA" "P. HARAPAN" "P. UNTUNG JAWA" ...
    ##  $ LUAS.WILAYAH.(KM2)  : num  0.91 3.76 3.59 0.59 1.57 1.39 2.58 1.26 1.12 1.14 ...
    ##  $ KEPADATAN.(JIWA/KM2): num  6779 1705 628 3625 3084 ...
    ##  $ 35-39.Laki-Laki     : num  231 84 255 199 98 113 166 850 954 752 ...
    ##  $ 35-39.Perempuan     : num  235 88 238 185 75 112 174 748 920 675 ...
    ##  $ 40-44.Laki-Laki     : num  233 99 232 178 73 108 130 749 914 691 ...
    ##  $ 40-44.Perempuan     : num  210 88 234 176 94 80 165 798 943 691 ...
    ##  $ 45-49.Laki-Laki     : num  171 72 212 162 67 66 176 779 871 659 ...
    ##  $ 45-49.Perempuan     : num  158 63 193 139 69 62 162 766 823 631 ...
    ##  $ 50-54.Laki-Laki     : num  137 34 150 100 60 61 129 715 736 611 ...
    ##  $ 50-54.Perempuan     : num  126 29 161 119 40 63 97 662 679 514 ...
    ##  $ 55-59.Laki-Laki     : num  98 30 139 97 37 37 108 614 680 539 ...
    ##  $ 55-59.Perempuan     : num  106 39 101 83 32 36 90 537 510 466 ...
    ##  $ 60-64.Laki-Laki     : num  72 29 73 58 22 32 88 555 544 428 ...
    ##  $ 60-64.Perempuan     : num  65 24 56 56 13 26 42 343 421 279 ...
    ##  $ 65-69.Laki-Laki     : num  36 12 18 40 18 21 68 413 398 328 ...
    ##  $ 65-69.Perempuan     : num  33 21 35 54 15 14 34 215 235 160 ...
    ##  $ 70-74.Laki-Laki     : num  33 13 24 26 10 17 37 259 241 215 ...
    ##  $ 70-74.Perempuan     : num  20 5 25 27 18 11 32 142 132 116 ...
    ##  $ >75.Laki-Laki       : num  13 5 18 16 11 8 34 214 215 150 ...
    ##  $ >75.Perempuan       : num  27 8 26 13 17 7 23 165 159 121 ...

Mengambil Kolom Laki.Laki / Perempuan dengan grep

``` r
library(openxlsx)
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
#Tampilkan nama-nama kolom yang mengandung kata "perempuan".
pola_nama_perempuan <- grep(pattern="perempuan",x=names(penduduk.dki.xlsx), ignore.case=TRUE)
names(penduduk.dki.xlsx[pola_nama_perempuan])
```

    ## [1] "35-39.Perempuan" "40-44.Perempuan" "45-49.Perempuan" "50-54.Perempuan"
    ## [5] "55-59.Perempuan" "60-64.Perempuan" "65-69.Perempuan" "70-74.Perempuan"
    ## [9] ">75.Perempuan"

``` r
#Tampilkan nama-nama kolom yang mengandung kata "laki-laki"
pola_nama_laki_laki <- grep(pattern="laki-laki",x=names(penduduk.dki.xlsx), ignore.case=TRUE)
names(penduduk.dki.xlsx[pola_nama_laki_laki])
```

    ## [1] "35-39.Laki-Laki" "40-44.Laki-Laki" "45-49.Laki-Laki" "50-54.Laki-Laki"
    ## [5] "55-59.Laki-Laki" "60-64.Laki-Laki" "65-69.Laki-Laki" "70-74.Laki-Laki"
    ## [9] ">75.Laki-Laki"

Menambahkan kolom Penjumlahan

``` r
library(openxlsx)
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
#Tampilkan nama-nama kolom yang mengandung kata "perempuan".
pola_nama_perempuan <- grep(pattern="perempuan", x = names(penduduk.dki.xlsx), ignore.case=TRUE)
penduduk.dki.xlsx$PEREMPUAN35TAHUNKEATAS  <- rowSums(penduduk.dki.xlsx[pola_nama_perempuan])
```

Normalisasi Data dari Kolom ke Baris

``` r
library(openxlsx)
library(reshape2)
```

    ## Warning: package 'reshape2' was built under R version 4.0.5

``` r
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
#Transformasi kolom dataset penduduk.dki.xlsx, disimpan ke variable penduduk.dki.transform
penduduk.dki.transform <- melt(data=penduduk.dki.xlsx, id.vars=c( "NAMA.KECAMATAN", "NAMA.KELURAHAN"), measure.vars = c("35-39.Laki-Laki", "35-39.Perempuan"), variable.name = "DEMOGRAFIK", value.name="JUMLAH")
#Menampilkan variable penduduk.dki.transform
penduduk.dki.transform
```

    ##        NAMA.KECAMATAN         NAMA.KELURAHAN      DEMOGRAFIK JUMLAH
    ## 1     KEP. SERIBU UTR            P. PANGGANG 35-39.Laki-Laki    231
    ## 2     KEP. SERIBU UTR              P. KELAPA 35-39.Laki-Laki     84
    ## 3     KEP. SERIBU UTR             P. HARAPAN 35-39.Laki-Laki    255
    ## 4     KEP. SERIBU SLT         P. UNTUNG JAWA 35-39.Laki-Laki    199
    ## 5     KEP. SERIBU SLT              P. TIDUNG 35-39.Laki-Laki     98
    ## 6     KEP. SERIBU SLT                P. PARI 35-39.Laki-Laki    113
    ## 7              GAMBIR                 GAMBIR 35-39.Laki-Laki    166
    ## 8              GAMBIR                 CIDENG 35-39.Laki-Laki    850
    ## 9              GAMBIR           PETOJO UTARA 35-39.Laki-Laki    954
    ## 10             GAMBIR         PETOJO SELATAN 35-39.Laki-Laki    752
    ## 11             GAMBIR           KEBON KELAPA 35-39.Laki-Laki    592
    ## 12             GAMBIR              DURI PULO 35-39.Laki-Laki   1213
    ## 13        SAWAH BESAR             PASAR BARU 35-39.Laki-Laki    714
    ## 14        SAWAH BESAR           KARANG ANYAR 35-39.Laki-Laki   1575
    ## 15        SAWAH BESAR                KARTINI 35-39.Laki-Laki   1307
    ## 16        SAWAH BESAR    GUNUNG SAHARI UTARA 35-39.Laki-Laki    817
    ## 17        SAWAH BESAR     MANGGA DUA SELATAN 35-39.Laki-Laki   1683
    ## 18          KEMAYORAN              KEMAYORAN 35-39.Laki-Laki   1164
    ## 19          KEMAYORAN           KEBON KOSONG 35-39.Laki-Laki   1644
    ## 20          KEMAYORAN          HARAPAN MULIA 35-39.Laki-Laki   1256
    ## 21          KEMAYORAN                SERDANG 35-39.Laki-Laki   1603
    ## 22          KEMAYORAN  GUNUNG SAHARI SELATAN 35-39.Laki-Laki   1071
    ## 23          KEMAYORAN           CEMPAKA BARU 35-39.Laki-Laki   1750
    ## 24          KEMAYORAN             SUMUR BATU 35-39.Laki-Laki   1452
    ## 25          KEMAYORAN           UTAN PANJANG 35-39.Laki-Laki   1610
    ## 26              SENEN                  SENEN 35-39.Laki-Laki    398
    ## 27              SENEN                 KENARI 35-39.Laki-Laki    456
    ## 28              SENEN                PASEBAN 35-39.Laki-Laki   1266
    ## 29              SENEN                 KRAMAT 35-39.Laki-Laki   1552
    ## 30              SENEN                KWITANG 35-39.Laki-Laki    908
    ## 31              SENEN                 BUNGUR 35-39.Laki-Laki   1046
    ## 32      CEMPAKA PUTIH    CEMPAKA PUTIH TIMUR 35-39.Laki-Laki   1264
    ## 33      CEMPAKA PUTIH    CEMPAKA PUTIH BARAT 35-39.Laki-Laki   1858
    ## 34      CEMPAKA PUTIH               RAWASARI 35-39.Laki-Laki   1200
    ## 35            MENTENG                MENTENG 35-39.Laki-Laki   1349
    ## 36            MENTENG             PEGANGSAAN 35-39.Laki-Laki   1172
    ## 37            MENTENG                 CIKINI 35-39.Laki-Laki    424
    ## 38            MENTENG             GONDANGDIA 35-39.Laki-Laki    192
    ## 39            MENTENG            KEBON SIRIH 35-39.Laki-Laki    733
    ## 40        TANAH ABANG                 GELORA 35-39.Laki-Laki    185
    ## 41        TANAH ABANG        BENDUNGAN HILIR 35-39.Laki-Laki   1124
    ## 42        TANAH ABANG          KARET TENGSIN 35-39.Laki-Laki   1118
    ## 43        TANAH ABANG             PETAMBURAN 35-39.Laki-Laki   1851
    ## 44        TANAH ABANG           KEBON MELATI 35-39.Laki-Laki   1862
    ## 45        TANAH ABANG           KEBON KACANG 35-39.Laki-Laki   1150
    ## 46        TANAH ABANG           KAMPUNG BALI 35-39.Laki-Laki    612
    ## 47         JOHAR BARU             JOHAR BARU 35-39.Laki-Laki   2036
    ## 48         JOHAR BARU           KAMPUNG RAWA 35-39.Laki-Laki   1210
    ## 49         JOHAR BARU                  GALUR 35-39.Laki-Laki    999
    ## 50         JOHAR BARU           TANAH TINGGI 35-39.Laki-Laki   2118
    ## 51        PENJARINGAN            PENJARINGAN 35-39.Laki-Laki   9225
    ## 52        PENJARINGAN            KAMAL MUARA 35-39.Laki-Laki   1045
    ## 53        PENJARINGAN            KAPUK MUARA 35-39.Laki-Laki   2763
    ## 54        PENJARINGAN              PEJAGALAN 35-39.Laki-Laki   7137
    ## 55        PENJARINGAN                  PLUIT 35-39.Laki-Laki   3656
    ## 56      TANJUNG PRIOK          TANJUNG PRIOK 35-39.Laki-Laki   3374
    ## 57      TANJUNG PRIOK            SUNTER JAYA 35-39.Laki-Laki   5374
    ## 58      TANJUNG PRIOK               PAPANGGO 35-39.Laki-Laki   3667
    ## 59      TANJUNG PRIOK           SUNGAI BAMBU 35-39.Laki-Laki   2807
    ## 60      TANJUNG PRIOK           KEBON BAWANG 35-39.Laki-Laki   4677
    ## 61      TANJUNG PRIOK           SUNTER AGUNG 35-39.Laki-Laki   6094
    ## 62      TANJUNG PRIOK                WARAKAS 35-39.Laki-Laki   4224
    ## 63               KOJA                   KOJA 35-39.Laki-Laki   3088
    ## 64               KOJA             TUGU UTARA 35-39.Laki-Laki   6608
    ## 65               KOJA                  LAGOA 35-39.Laki-Laki   5931
    ## 66               KOJA       RAWA BADAK UTARA 35-39.Laki-Laki   3260
    ## 67               KOJA           TUGU SELATAN 35-39.Laki-Laki   3744
    ## 68               KOJA     RAWA BADAK SELATAN 35-39.Laki-Laki   3910
    ## 69          CILINCING              CILINCING 35-39.Laki-Laki   4654
    ## 70          CILINCING               SUKAPURA 35-39.Laki-Laki   5221
    ## 71          CILINCING                MARUNDA 35-39.Laki-Laki   2187
    ## 72          CILINCING              KALI BARU 35-39.Laki-Laki   7616
    ## 73          CILINCING           SEMPER TIMUR 35-39.Laki-Laki   3230
    ## 74          CILINCING                ROROTAN 35-39.Laki-Laki   3442
    ## 75          CILINCING           SEMPER BARAT 35-39.Laki-Laki   6419
    ## 76         PADEMANGAN       PADEMANGAN TIMUR 35-39.Laki-Laki   3005
    ## 77         PADEMANGAN       PADEMANGAN BARAT 35-39.Laki-Laki   7178
    ## 78         PADEMANGAN                  ANCOL 35-39.Laki-Laki   2259
    ## 79      KELAPA GADING    KELAPA GADING TIMUR 35-39.Laki-Laki   2539
    ## 80      KELAPA GADING         PEGANGSAAN DUA 35-39.Laki-Laki   4170
    ## 81      KELAPA GADING    KELAPA GADING BARAT 35-39.Laki-Laki   2628
    ## 82         CENGKARENG       CENGKARENG BARAT 35-39.Laki-Laki   5316
    ## 83         CENGKARENG           DURI KOSAMBI 35-39.Laki-Laki   6922
    ## 84         CENGKARENG             RAWA BUAYA 35-39.Laki-Laki   5632
    ## 85         CENGKARENG     KEDAUNG KALI ANGKE 35-39.Laki-Laki   2951
    ## 86         CENGKARENG                  KAPUK 35-39.Laki-Laki  13011
    ## 87         CENGKARENG       CENGKARENG TIMUR 35-39.Laki-Laki   7146
    ## 88  GROGOL PETAMBURAN                 GROGOL 35-39.Laki-Laki   1530
    ## 89  GROGOL PETAMBURAN    TANJUNG DUREN UTARA 35-39.Laki-Laki   1277
    ## 90  GROGOL PETAMBURAN                 TOMANG 35-39.Laki-Laki   2404
    ## 91  GROGOL PETAMBURAN               JELAMBAR 35-39.Laki-Laki   2358
    ## 92  GROGOL PETAMBURAN  TANJUNG DUREN SELATAN 35-39.Laki-Laki   1857
    ## 93  GROGOL PETAMBURAN          JELAMBAR BARU 35-39.Laki-Laki   3165
    ## 94  GROGOL PETAMBURAN          WIJAYA KUSUMA 35-39.Laki-Laki   3523
    ## 95         TAMAN SARI             TAMAN SARI 35-39.Laki-Laki   1365
    ## 96         TAMAN SARI                 KRUKUT 35-39.Laki-Laki   1848
    ## 97         TAMAN SARI                 MAPHAR 35-39.Laki-Laki   1555
    ## 98         TAMAN SARI                 TANGKI 35-39.Laki-Laki   1248
    ## 99         TAMAN SARI           MANGGA BESAR 35-39.Laki-Laki    675
    ## 100        TAMAN SARI              KEAGUNGAN 35-39.Laki-Laki   1673
    ## 101        TAMAN SARI                 GLODOK 35-39.Laki-Laki    650
    ## 102        TAMAN SARI              PINANGSIA 35-39.Laki-Laki    991
    ## 103           TAMBORA                TAMBORA 35-39.Laki-Laki    968
    ## 104           TAMBORA             KALI ANYAR 35-39.Laki-Laki   2532
    ## 105           TAMBORA             DURI UTARA 35-39.Laki-Laki   1919
    ## 106           TAMBORA           TANAH SEREAL 35-39.Laki-Laki   2485
    ## 107           TAMBORA              KERENDANG 35-39.Laki-Laki   2057
    ## 108           TAMBORA          JEMBATAN BESI 35-39.Laki-Laki   3124
    ## 109           TAMBORA                  ANGKE 35-39.Laki-Laki   2767
    ## 110           TAMBORA          JEMBATAN LIMA 35-39.Laki-Laki   2104
    ## 111           TAMBORA                PEKOJAN 35-39.Laki-Laki   2061
    ## 112           TAMBORA             ROA MALAKA 35-39.Laki-Laki    257
    ## 113           TAMBORA           DURI SELATAN 35-39.Laki-Laki   1319
    ## 114       KEBON JERUK            KEBON JERUK 35-39.Laki-Laki   4362
    ## 115       KEBON JERUK         SUKABUMI UTARA 35-39.Laki-Laki   3197
    ## 116       KEBON JERUK       SUKABUMI SELATAN 35-39.Laki-Laki   3396
    ## 117       KEBON JERUK             KELAPA DUA 35-39.Laki-Laki   1962
    ## 118       KEBON JERUK              DURI KEPA 35-39.Laki-Laki   5160
    ## 119       KEBON JERUK           KEDOYA UTARA 35-39.Laki-Laki   3914
    ## 120       KEBON JERUK         KEDOYA SELATAN 35-39.Laki-Laki   2709
    ## 121        KALI DERES              KALIDERES 35-39.Laki-Laki   6660
    ## 122        KALI DERES                SEMANAN 35-39.Laki-Laki   6508
    ## 123        KALI DERES             TEGAL ALUR 35-39.Laki-Laki   8053
    ## 124        KALI DERES                  KAMAL 35-39.Laki-Laki   4847
    ## 125        KALI DERES             PEGADUNGAN 35-39.Laki-Laki   5990
    ## 126          PALMERAH               PALMERAH 35-39.Laki-Laki   5308
    ## 127          PALMERAH                  SLIPI 35-39.Laki-Laki   1445
    ## 128          PALMERAH       KOTA BAMBU UTARA 35-39.Laki-Laki   2268
    ## 129          PALMERAH              JATI PULO 35-39.Laki-Laki   2575
    ## 130          PALMERAH            KEMANGGISAN 35-39.Laki-Laki   2642
    ## 131          PALMERAH     KOTA BAMBU SELATAN 35-39.Laki-Laki   1967
    ## 132         KEMBANGAN        KEMBANGAN UTARA 35-39.Laki-Laki   4531
    ## 133         KEMBANGAN           MERUYA UTARA 35-39.Laki-Laki   3545
    ## 134         KEMBANGAN         MERUYA SELATAN 35-39.Laki-Laki   2471
    ## 135         KEMBANGAN              SRENGSENG 35-39.Laki-Laki   3761
    ## 136         KEMBANGAN                  JOGLO 35-39.Laki-Laki   3226
    ## 137         KEMBANGAN      KEMBANGAN SELATAN 35-39.Laki-Laki   2439
    ## 138             TEBET            TEBET TIMUR 35-39.Laki-Laki    838
    ## 139             TEBET            TEBET BARAT 35-39.Laki-Laki   1060
    ## 140             TEBET          MENTENG DALAM 35-39.Laki-Laki   2029
    ## 141             TEBET             KEBON BARU 35-39.Laki-Laki   2004
    ## 142             TEBET             BUKIT DURI 35-39.Laki-Laki   1880
    ## 143             TEBET      MANGGARAI SELATAN 35-39.Laki-Laki   1239
    ## 144             TEBET              MANGGARAI 35-39.Laki-Laki   1545
    ## 145        SETIA BUDI             SETIA BUDI 35-39.Laki-Laki    168
    ## 146        SETIA BUDI         KARET SEMANGGI 35-39.Laki-Laki    126
    ## 147        SETIA BUDI         KARET KUNINGAN 35-39.Laki-Laki    879
    ## 148        SETIA BUDI                  KARET 35-39.Laki-Laki    603
    ## 149        SETIA BUDI           MENTENG ATAS 35-39.Laki-Laki   1504
    ## 150        SETIA BUDI          PASAR MANGGIS 35-39.Laki-Laki   1445
    ## 151        SETIA BUDI                 GUNTUR 35-39.Laki-Laki    208
    ## 152        SETIA BUDI         KUNINGAN TIMUR 35-39.Laki-Laki    328
    ## 153  MAMPANG PRAPATAN       MAMPANG PRAPATAN 35-39.Laki-Laki   1101
    ## 154  MAMPANG PRAPATAN                 BANGKA 35-39.Laki-Laki   1119
    ## 155  MAMPANG PRAPATAN           PELA MAMPANG 35-39.Laki-Laki   2458
    ## 156  MAMPANG PRAPATAN           TEGAL PARANG 35-39.Laki-Laki   1826
    ## 157  MAMPANG PRAPATAN         KUNINGAN BARAT 35-39.Laki-Laki    727
    ## 158      PASAR MINGGU           PASAR MINGGU 35-39.Laki-Laki   1296
    ## 159      PASAR MINGGU            JATI PADANG 35-39.Laki-Laki   2023
    ## 160      PASAR MINGGU         CILANDAK TIMUR 35-39.Laki-Laki   1398
    ## 161      PASAR MINGGU                RAGUNAN 35-39.Laki-Laki   2284
    ## 162      PASAR MINGGU          PEJATEN TIMUR 35-39.Laki-Laki   3168
    ## 163      PASAR MINGGU          PEJATEN BARAT 35-39.Laki-Laki   1963
    ## 164      PASAR MINGGU              KEBAGUSAN 35-39.Laki-Laki   2300
    ## 165    KEBAYORAN LAMA   KEBAYORAN LAMA UTARA 35-39.Laki-Laki   2638
    ## 166    KEBAYORAN LAMA          PONDOK PINANG 35-39.Laki-Laki   2770
    ## 167    KEBAYORAN LAMA                CIPULIR 35-39.Laki-Laki   2191
    ## 168    KEBAYORAN LAMA           GROGOL UTARA 35-39.Laki-Laki   2266
    ## 169    KEBAYORAN LAMA         GROGOL SELATAN 35-39.Laki-Laki   2309
    ## 170    KEBAYORAN LAMA KEBAYORAN LAMA SELATAN 35-39.Laki-Laki   2316
    ## 171          CILANDAK         CILANDAK BARAT 35-39.Laki-Laki   2700
    ## 172          CILANDAK            LEBAK BULUS 35-39.Laki-Laki   1823
    ## 173          CILANDAK            PONDOK LABU 35-39.Laki-Laki   2261
    ## 174          CILANDAK       GANDARIA SELATAN 35-39.Laki-Laki   1145
    ## 175          CILANDAK         CIPETE SELATAN 35-39.Laki-Laki   1387
    ## 176    KEBAYORAN BARU                MELAWAI 35-39.Laki-Laki    116
    ## 177    KEBAYORAN BARU                 GUNUNG 35-39.Laki-Laki    423
    ## 178    KEBAYORAN BARU            KRAMAT PELA 35-39.Laki-Laki    706
    ## 179    KEBAYORAN BARU                 SELONG 35-39.Laki-Laki    178
    ## 180    KEBAYORAN BARU             RAWA BARAT 35-39.Laki-Laki    274
    ## 181    KEBAYORAN BARU                SENAYAN 35-39.Laki-Laki    176
    ## 182    KEBAYORAN BARU                   PULO 35-39.Laki-Laki    256
    ## 183    KEBAYORAN BARU              PETOGOGAN 35-39.Laki-Laki    621
    ## 184    KEBAYORAN BARU         GANDARIA UTARA 35-39.Laki-Laki   2056
    ## 185    KEBAYORAN BARU           CIPETE UTARA 35-39.Laki-Laki   1907
    ## 186          PANCORAN               PANCORAN 35-39.Laki-Laki   1026
    ## 187          PANCORAN               KALIBATA 35-39.Laki-Laki   2300
    ## 188          PANCORAN              RAWA JATI 35-39.Laki-Laki    990
    ## 189          PANCORAN             DUREN TIGA 35-39.Laki-Laki   1540
    ## 190          PANCORAN             PENGADEGAN 35-39.Laki-Laki   1140
    ## 191          PANCORAN                 CIKOKO 35-39.Laki-Laki    698
    ## 192         JAGAKARSA              JAGAKARSA 35-39.Laki-Laki   3050
    ## 193         JAGAKARSA        SRENGSENG SAWAH 35-39.Laki-Laki   2783
    ## 194         JAGAKARSA               CIGANJUR 35-39.Laki-Laki   1859
    ## 195         JAGAKARSA          LENTENG AGUNG 35-39.Laki-Laki   2617
    ## 196         JAGAKARSA          TANJUNG BARAT 35-39.Laki-Laki   2017
    ## 197         JAGAKARSA                CIPEDAK 35-39.Laki-Laki   1708
    ## 198      PESANGGRAHAN           PESANGGRAHAN 35-39.Laki-Laki   1499
    ## 199      PESANGGRAHAN                BINTARO 35-39.Laki-Laki   2675
    ## 200      PESANGGRAHAN       PETUKANGAN UTARA 35-39.Laki-Laki   2787
    ## 201      PESANGGRAHAN     PETUKANGAN SELATAN 35-39.Laki-Laki   1836
    ## 202      PESANGGRAHAN                ULUJAMI 35-39.Laki-Laki   2304
    ## 203          MATRAMAN          PISANGAN BARU 35-39.Laki-Laki   1759
    ## 204          MATRAMAN        UTAN KAYU UTARA 35-39.Laki-Laki   1606
    ## 205          MATRAMAN             KAYU MANIS 35-39.Laki-Laki   1377
    ## 206          MATRAMAN             PAL MERIAM 35-39.Laki-Laki   1101
    ## 207          MATRAMAN          KEBON MANGGIS 35-39.Laki-Laki    840
    ## 208          MATRAMAN      UTAN KAYU SELATAN 35-39.Laki-Laki   1820
    ## 209       PULO GADUNG            PULO GADUNG 35-39.Laki-Laki   1998
    ## 210       PULO GADUNG         PISANGAN TIMUR 35-39.Laki-Laki   2249
    ## 211       PULO GADUNG               CIPINANG 35-39.Laki-Laki   2192
    ## 212       PULO GADUNG        JATINEGARA KAUM 35-39.Laki-Laki   1278
    ## 213       PULO GADUNG             RAWAMANGUN 35-39.Laki-Laki   2054
    ## 214       PULO GADUNG             KAYU PUTIH 35-39.Laki-Laki   2361
    ## 215       PULO GADUNG                   JATI 35-39.Laki-Laki   1764
    ## 216        JATINEGARA         KAMPUNG MELAYU 35-39.Laki-Laki   1361
    ## 217        JATINEGARA            BIDARA CINA 35-39.Laki-Laki   2105
    ## 218        JATINEGARA            BALI MESTER 35-39.Laki-Laki    444
    ## 219        JATINEGARA             RAWA BUNGA 35-39.Laki-Laki   1131
    ## 220        JATINEGARA      CIPINANG CEMPEDAK 35-39.Laki-Laki   1614
    ## 221        JATINEGARA         CIPINANG MUARA 35-39.Laki-Laki   3063
    ## 222        JATINEGARA CIPINANG BESAR SELATAN 35-39.Laki-Laki   1875
    ## 223        JATINEGARA   CIPINANG BESAR UTARA 35-39.Laki-Laki   2704
    ## 224       KRAMAT JATI            KRAMAT JATI 35-39.Laki-Laki   1946
    ## 225       KRAMAT JATI         KAMPUNG TENGAH 35-39.Laki-Laki   2224
    ## 226       KRAMAT JATI                  DUKUH 35-39.Laki-Laki   1277
    ## 227       KRAMAT JATI             BATU AMPAR 35-39.Laki-Laki   2480
    ## 228       KRAMAT JATI           BALE KAMBANG 35-39.Laki-Laki   1413
    ## 229       KRAMAT JATI              CILILITAN 35-39.Laki-Laki   2265
    ## 230       KRAMAT JATI                 CAWANG 35-39.Laki-Laki   1942
    ## 231        PASAR REBO                 GEDONG 35-39.Laki-Laki   1823
    ## 232        PASAR REBO                   BARU 35-39.Laki-Laki   1678
    ## 233        PASAR REBO              CIJANTUNG 35-39.Laki-Laki   2107
    ## 234        PASAR REBO               KALISARI 35-39.Laki-Laki   2006
    ## 235        PASAR REBO                PEKAYON 35-39.Laki-Laki   2139
    ## 236            CAKUNG             JATINEGARA 35-39.Laki-Laki   5035
    ## 237            CAKUNG            RAWA TERATE 35-39.Laki-Laki   1565
    ## 238            CAKUNG           PENGGILINGAN 35-39.Laki-Laki   4651
    ## 239            CAKUNG           CAKUNG TIMUR 35-39.Laki-Laki   3053
    ## 240            CAKUNG            PULO GEBANG 35-39.Laki-Laki   4162
    ## 241            CAKUNG          UJUNG MENTENG 35-39.Laki-Laki   1420
    ## 242            CAKUNG           CAKUNG BARAT 35-39.Laki-Laki   3285
    ## 243       DUREN SAWIT            DUREN SAWIT 35-39.Laki-Laki   3210
    ## 244       DUREN SAWIT           PONDOK BAMBU 35-39.Laki-Laki   3427
    ## 245       DUREN SAWIT                KLENDER 35-39.Laki-Laki   3896
    ## 246       DUREN SAWIT          PONDOK KELAPA 35-39.Laki-Laki   3467
    ## 247       DUREN SAWIT            MALAKA SARI 35-39.Laki-Laki   1682
    ## 248       DUREN SAWIT            MALAKA JAYA 35-39.Laki-Laki   1949
    ## 249       DUREN SAWIT            PONDOK KOPI 35-39.Laki-Laki   1611
    ## 250           MAKASAR                MAKASAR 35-39.Laki-Laki   1888
    ## 251           MAKASAR           PINANG RANTI 35-39.Laki-Laki   1299
    ## 252           MAKASAR             KEBON PALA 35-39.Laki-Laki   2689
    ## 253           MAKASAR  HALIM PERDANA KUSUMAH 35-39.Laki-Laki   1479
    ## 254           MAKASAR        CIPINANG MELAYU 35-39.Laki-Laki   2208
    ## 255           CIRACAS                CIRACAS 35-39.Laki-Laki   3179
    ## 256           CIRACAS                CIBUBUR 35-39.Laki-Laki   3311
    ## 257           CIRACAS       KELAPA DUA WETAN 35-39.Laki-Laki   2185
    ## 258           CIRACAS                SUSUKAN 35-39.Laki-Laki   1988
    ## 259           CIRACAS               RAMBUTAN 35-39.Laki-Laki   1857
    ## 260          CIPAYUNG               CIPAYUNG 35-39.Laki-Laki   1241
    ## 261          CIPAYUNG              CILANGKAP 35-39.Laki-Laki   1237
    ## 262          CIPAYUNG         PONDOK RANGGON 35-39.Laki-Laki   1088
    ## 263          CIPAYUNG                 MUNJUL 35-39.Laki-Laki   1167
    ## 264          CIPAYUNG                   SETU 35-39.Laki-Laki    937
    ## 265          CIPAYUNG             BAMBU APUS 35-39.Laki-Laki   1242
    ## 266          CIPAYUNG           LUBANG BUAYA 35-39.Laki-Laki   3258
    ## 267          CIPAYUNG                  CEGER 35-39.Laki-Laki   1007
    ## 268   KEP. SERIBU UTR            P. PANGGANG 35-39.Perempuan    235
    ## 269   KEP. SERIBU UTR              P. KELAPA 35-39.Perempuan     88
    ## 270   KEP. SERIBU UTR             P. HARAPAN 35-39.Perempuan    238
    ## 271   KEP. SERIBU SLT         P. UNTUNG JAWA 35-39.Perempuan    185
    ## 272   KEP. SERIBU SLT              P. TIDUNG 35-39.Perempuan     75
    ## 273   KEP. SERIBU SLT                P. PARI 35-39.Perempuan    112
    ## 274            GAMBIR                 GAMBIR 35-39.Perempuan    174
    ## 275            GAMBIR                 CIDENG 35-39.Perempuan    748
    ## 276            GAMBIR           PETOJO UTARA 35-39.Perempuan    920
    ## 277            GAMBIR         PETOJO SELATAN 35-39.Perempuan    675
    ## 278            GAMBIR           KEBON KELAPA 35-39.Perempuan    491
    ## 279            GAMBIR              DURI PULO 35-39.Perempuan   1106
    ## 280       SAWAH BESAR             PASAR BARU 35-39.Perempuan    611
    ## 281       SAWAH BESAR           KARANG ANYAR 35-39.Perempuan   1485
    ## 282       SAWAH BESAR                KARTINI 35-39.Perempuan   1177
    ## 283       SAWAH BESAR    GUNUNG SAHARI UTARA 35-39.Perempuan    835
    ## 284       SAWAH BESAR     MANGGA DUA SELATAN 35-39.Perempuan   1662
    ## 285         KEMAYORAN              KEMAYORAN 35-39.Perempuan   1063
    ## 286         KEMAYORAN           KEBON KOSONG 35-39.Perempuan   1542
    ## 287         KEMAYORAN          HARAPAN MULIA 35-39.Perempuan   1213
    ## 288         KEMAYORAN                SERDANG 35-39.Perempuan   1559
    ## 289         KEMAYORAN  GUNUNG SAHARI SELATAN 35-39.Perempuan    979
    ## 290         KEMAYORAN           CEMPAKA BARU 35-39.Perempuan   1710
    ## 291         KEMAYORAN             SUMUR BATU 35-39.Perempuan   1372
    ## 292         KEMAYORAN           UTAN PANJANG 35-39.Perempuan   1549
    ## 293             SENEN                  SENEN 35-39.Perempuan    428
    ## 294             SENEN                 KENARI 35-39.Perempuan    447
    ## 295             SENEN                PASEBAN 35-39.Perempuan   1232
    ## 296             SENEN                 KRAMAT 35-39.Perempuan   1479
    ## 297             SENEN                KWITANG 35-39.Perempuan    793
    ## 298             SENEN                 BUNGUR 35-39.Perempuan    993
    ## 299     CEMPAKA PUTIH    CEMPAKA PUTIH TIMUR 35-39.Perempuan   1267
    ## 300     CEMPAKA PUTIH    CEMPAKA PUTIH BARAT 35-39.Perempuan   1811
    ## 301     CEMPAKA PUTIH               RAWASARI 35-39.Perempuan   1160
    ## 302           MENTENG                MENTENG 35-39.Perempuan   1194
    ## 303           MENTENG             PEGANGSAAN 35-39.Perempuan   1096
    ## 304           MENTENG                 CIKINI 35-39.Perempuan    428
    ## 305           MENTENG             GONDANGDIA 35-39.Perempuan    165
    ## 306           MENTENG            KEBON SIRIH 35-39.Perempuan    717
    ## 307       TANAH ABANG                 GELORA 35-39.Perempuan    178
    ## 308       TANAH ABANG        BENDUNGAN HILIR 35-39.Perempuan   1138
    ## 309       TANAH ABANG          KARET TENGSIN 35-39.Perempuan   1078
    ## 310       TANAH ABANG             PETAMBURAN 35-39.Perempuan   1780
    ## 311       TANAH ABANG           KEBON MELATI 35-39.Perempuan   1721
    ## 312       TANAH ABANG           KEBON KACANG 35-39.Perempuan   1041
    ## 313       TANAH ABANG           KAMPUNG BALI 35-39.Perempuan    613
    ## 314        JOHAR BARU             JOHAR BARU 35-39.Perempuan   1878
    ## 315        JOHAR BARU           KAMPUNG RAWA 35-39.Perempuan   1255
    ## 316        JOHAR BARU                  GALUR 35-39.Perempuan   1060
    ## 317        JOHAR BARU           TANAH TINGGI 35-39.Perempuan   2013
    ## 318       PENJARINGAN            PENJARINGAN 35-39.Perempuan   5535
    ## 319       PENJARINGAN            KAMAL MUARA 35-39.Perempuan    517
    ## 320       PENJARINGAN            KAPUK MUARA 35-39.Perempuan   1631
    ## 321       PENJARINGAN              PEJAGALAN 35-39.Perempuan   4468
    ## 322       PENJARINGAN                  PLUIT 35-39.Perempuan   2264
    ## 323     TANJUNG PRIOK          TANJUNG PRIOK 35-39.Perempuan   2025
    ## 324     TANJUNG PRIOK            SUNTER JAYA 35-39.Perempuan   3427
    ## 325     TANJUNG PRIOK               PAPANGGO 35-39.Perempuan   2290
    ## 326     TANJUNG PRIOK           SUNGAI BAMBU 35-39.Perempuan   1749
    ## 327     TANJUNG PRIOK           KEBON BAWANG 35-39.Perempuan   3009
    ## 328     TANJUNG PRIOK           SUNTER AGUNG 35-39.Perempuan   3710
    ## 329     TANJUNG PRIOK                WARAKAS 35-39.Perempuan   2608
    ## 330              KOJA                   KOJA 35-39.Perempuan   1767
    ## 331              KOJA             TUGU UTARA 35-39.Perempuan   3954
    ## 332              KOJA                  LAGOA 35-39.Perempuan   3342
    ## 333              KOJA       RAWA BADAK UTARA 35-39.Perempuan   2064
    ## 334              KOJA           TUGU SELATAN 35-39.Perempuan   2235
    ## 335              KOJA     RAWA BADAK SELATAN 35-39.Perempuan   2420
    ## 336         CILINCING              CILINCING 35-39.Perempuan   2614
    ## 337         CILINCING               SUKAPURA 35-39.Perempuan   3376
    ## 338         CILINCING                MARUNDA 35-39.Perempuan   1207
    ## 339         CILINCING              KALI BARU 35-39.Perempuan   4096
    ## 340         CILINCING           SEMPER TIMUR 35-39.Perempuan   1683
    ## 341         CILINCING                ROROTAN 35-39.Perempuan   1876
    ## 342         CILINCING           SEMPER BARAT 35-39.Perempuan   3579
    ## 343        PADEMANGAN       PADEMANGAN TIMUR 35-39.Perempuan   1935
    ## 344        PADEMANGAN       PADEMANGAN BARAT 35-39.Perempuan   4264
    ## 345        PADEMANGAN                  ANCOL 35-39.Perempuan   1380
    ## 346     KELAPA GADING    KELAPA GADING TIMUR 35-39.Perempuan   1744
    ## 347     KELAPA GADING         PEGANGSAAN DUA 35-39.Perempuan   2259
    ## 348     KELAPA GADING    KELAPA GADING BARAT 35-39.Perempuan   1433
    ## 349        CENGKARENG       CENGKARENG BARAT 35-39.Perempuan   3221
    ## 350        CENGKARENG           DURI KOSAMBI 35-39.Perempuan   3764
    ## 351        CENGKARENG             RAWA BUAYA 35-39.Perempuan   3396
    ## 352        CENGKARENG     KEDAUNG KALI ANGKE 35-39.Perempuan   1756
    ## 353        CENGKARENG                  KAPUK 35-39.Perempuan   7488
    ## 354        CENGKARENG       CENGKARENG TIMUR 35-39.Perempuan   4147
    ## 355 GROGOL PETAMBURAN                 GROGOL 35-39.Perempuan    903
    ## 356 GROGOL PETAMBURAN    TANJUNG DUREN UTARA 35-39.Perempuan    812
    ## 357 GROGOL PETAMBURAN                 TOMANG 35-39.Perempuan   1449
    ## 358 GROGOL PETAMBURAN               JELAMBAR 35-39.Perempuan   1581
    ## 359 GROGOL PETAMBURAN  TANJUNG DUREN SELATAN 35-39.Perempuan   1220
    ## 360 GROGOL PETAMBURAN          JELAMBAR BARU 35-39.Perempuan   2116
    ## 361 GROGOL PETAMBURAN          WIJAYA KUSUMA 35-39.Perempuan   2301
    ## 362        TAMAN SARI             TAMAN SARI 35-39.Perempuan    729
    ## 363        TAMAN SARI                 KRUKUT 35-39.Perempuan   1107
    ## 364        TAMAN SARI                 MAPHAR 35-39.Perempuan    919
    ## 365        TAMAN SARI                 TANGKI 35-39.Perempuan    691
    ## 366        TAMAN SARI           MANGGA BESAR 35-39.Perempuan    386
    ## 367        TAMAN SARI              KEAGUNGAN 35-39.Perempuan    975
    ## 368        TAMAN SARI                 GLODOK 35-39.Perempuan    359
    ## 369        TAMAN SARI              PINANGSIA 35-39.Perempuan    600
    ## 370           TAMBORA                TAMBORA 35-39.Perempuan    588
    ## 371           TAMBORA             KALI ANYAR 35-39.Perempuan   1567
    ## 372           TAMBORA             DURI UTARA 35-39.Perempuan   1120
    ## 373           TAMBORA           TANAH SEREAL 35-39.Perempuan   1386
    ## 374           TAMBORA              KERENDANG 35-39.Perempuan   1212
    ## 375           TAMBORA          JEMBATAN BESI 35-39.Perempuan   2075
    ## 376           TAMBORA                  ANGKE 35-39.Perempuan   1721
    ## 377           TAMBORA          JEMBATAN LIMA 35-39.Perempuan   1277
    ## 378           TAMBORA                PEKOJAN 35-39.Perempuan   1197
    ## 379           TAMBORA             ROA MALAKA 35-39.Perempuan    180
    ## 380           TAMBORA           DURI SELATAN 35-39.Perempuan    769
    ## 381       KEBON JERUK            KEBON JERUK 35-39.Perempuan   2563
    ## 382       KEBON JERUK         SUKABUMI UTARA 35-39.Perempuan   2005
    ## 383       KEBON JERUK       SUKABUMI SELATAN 35-39.Perempuan   2049
    ## 384       KEBON JERUK             KELAPA DUA 35-39.Perempuan   1161
    ## 385       KEBON JERUK              DURI KEPA 35-39.Perempuan   3164
    ## 386       KEBON JERUK           KEDOYA UTARA 35-39.Perempuan   2355
    ## 387       KEBON JERUK         KEDOYA SELATAN 35-39.Perempuan   1675
    ## 388        KALI DERES              KALIDERES 35-39.Perempuan   3659
    ## 389        KALI DERES                SEMANAN 35-39.Perempuan   3687
    ## 390        KALI DERES             TEGAL ALUR 35-39.Perempuan   4591
    ## 391        KALI DERES                  KAMAL 35-39.Perempuan   2640
    ## 392        KALI DERES             PEGADUNGAN 35-39.Perempuan   3120
    ## 393          PALMERAH               PALMERAH 35-39.Perempuan   3083
    ## 394          PALMERAH                  SLIPI 35-39.Perempuan    856
    ## 395          PALMERAH       KOTA BAMBU UTARA 35-39.Perempuan   1359
    ## 396          PALMERAH              JATI PULO 35-39.Perempuan   1451
    ## 397          PALMERAH            KEMANGGISAN 35-39.Perempuan   1596
    ## 398          PALMERAH     KOTA BAMBU SELATAN 35-39.Perempuan   1141
    ## 399         KEMBANGAN        KEMBANGAN UTARA 35-39.Perempuan   2734
    ## 400         KEMBANGAN           MERUYA UTARA 35-39.Perempuan   2226
    ## 401         KEMBANGAN         MERUYA SELATAN 35-39.Perempuan   1427
    ## 402         KEMBANGAN              SRENGSENG 35-39.Perempuan   2109
    ## 403         KEMBANGAN                  JOGLO 35-39.Perempuan   1840
    ## 404         KEMBANGAN      KEMBANGAN SELATAN 35-39.Perempuan   1360
    ## 405             TEBET            TEBET TIMUR 35-39.Perempuan    890
    ## 406             TEBET            TEBET BARAT 35-39.Perempuan   1058
    ## 407             TEBET          MENTENG DALAM 35-39.Perempuan   1913
    ## 408             TEBET             KEBON BARU 35-39.Perempuan   1988
    ## 409             TEBET             BUKIT DURI 35-39.Perempuan   1801
    ## 410             TEBET      MANGGARAI SELATAN 35-39.Perempuan   1289
    ## 411             TEBET              MANGGARAI 35-39.Perempuan   1479
    ## 412        SETIA BUDI             SETIA BUDI 35-39.Perempuan    179
    ## 413        SETIA BUDI         KARET SEMANGGI 35-39.Perempuan    134
    ## 414        SETIA BUDI         KARET KUNINGAN 35-39.Perempuan    883
    ## 415        SETIA BUDI                  KARET 35-39.Perempuan    557
    ## 416        SETIA BUDI           MENTENG ATAS 35-39.Perempuan   1523
    ## 417        SETIA BUDI          PASAR MANGGIS 35-39.Perempuan   1437
    ## 418        SETIA BUDI                 GUNTUR 35-39.Perempuan    206
    ## 419        SETIA BUDI         KUNINGAN TIMUR 35-39.Perempuan    304
    ## 420  MAMPANG PRAPATAN       MAMPANG PRAPATAN 35-39.Perempuan    976
    ## 421  MAMPANG PRAPATAN                 BANGKA 35-39.Perempuan   1098
    ## 422  MAMPANG PRAPATAN           PELA MAMPANG 35-39.Perempuan   2321
    ## 423  MAMPANG PRAPATAN           TEGAL PARANG 35-39.Perempuan   1683
    ## 424  MAMPANG PRAPATAN         KUNINGAN BARAT 35-39.Perempuan    656
    ## 425      PASAR MINGGU           PASAR MINGGU 35-39.Perempuan   1288
    ## 426      PASAR MINGGU            JATI PADANG 35-39.Perempuan   1910
    ## 427      PASAR MINGGU         CILANDAK TIMUR 35-39.Perempuan   1389
    ## 428      PASAR MINGGU                RAGUNAN 35-39.Perempuan   2160
    ## 429      PASAR MINGGU          PEJATEN TIMUR 35-39.Perempuan   2919
    ## 430      PASAR MINGGU          PEJATEN BARAT 35-39.Perempuan   1894
    ## 431      PASAR MINGGU              KEBAGUSAN 35-39.Perempuan   2193
    ## 432    KEBAYORAN LAMA   KEBAYORAN LAMA UTARA 35-39.Perempuan   2396
    ## 433    KEBAYORAN LAMA          PONDOK PINANG 35-39.Perempuan   2765
    ## 434    KEBAYORAN LAMA                CIPULIR 35-39.Perempuan   2109
    ## 435    KEBAYORAN LAMA           GROGOL UTARA 35-39.Perempuan   2227
    ## 436    KEBAYORAN LAMA         GROGOL SELATAN 35-39.Perempuan   2266
    ## 437    KEBAYORAN LAMA KEBAYORAN LAMA SELATAN 35-39.Perempuan   2252
    ## 438          CILANDAK         CILANDAK BARAT 35-39.Perempuan   2678
    ## 439          CILANDAK            LEBAK BULUS 35-39.Perempuan   1852
    ## 440          CILANDAK            PONDOK LABU 35-39.Perempuan   2436
    ## 441          CILANDAK       GANDARIA SELATAN 35-39.Perempuan   1165
    ## 442          CILANDAK         CIPETE SELATAN 35-39.Perempuan   1331
    ## 443    KEBAYORAN BARU                MELAWAI 35-39.Perempuan    127
    ## 444    KEBAYORAN BARU                 GUNUNG 35-39.Perempuan    442
    ## 445    KEBAYORAN BARU            KRAMAT PELA 35-39.Perempuan    660
    ## 446    KEBAYORAN BARU                 SELONG 35-39.Perempuan    188
    ## 447    KEBAYORAN BARU             RAWA BARAT 35-39.Perempuan    272
    ## 448    KEBAYORAN BARU                SENAYAN 35-39.Perempuan    192
    ## 449    KEBAYORAN BARU                   PULO 35-39.Perempuan    295
    ## 450    KEBAYORAN BARU              PETOGOGAN 35-39.Perempuan    562
    ## 451    KEBAYORAN BARU         GANDARIA UTARA 35-39.Perempuan   2108
    ## 452    KEBAYORAN BARU           CIPETE UTARA 35-39.Perempuan   1758
    ## 453          PANCORAN               PANCORAN 35-39.Perempuan   1049
    ## 454          PANCORAN               KALIBATA 35-39.Perempuan   2242
    ## 455          PANCORAN              RAWA JATI 35-39.Perempuan    985
    ## 456          PANCORAN             DUREN TIGA 35-39.Perempuan   1460
    ## 457          PANCORAN             PENGADEGAN 35-39.Perempuan   1041
    ## 458          PANCORAN                 CIKOKO 35-39.Perempuan    595
    ## 459         JAGAKARSA              JAGAKARSA 35-39.Perempuan   2964
    ## 460         JAGAKARSA        SRENGSENG SAWAH 35-39.Perempuan   2874
    ## 461         JAGAKARSA               CIGANJUR 35-39.Perempuan   1817
    ## 462         JAGAKARSA          LENTENG AGUNG 35-39.Perempuan   2596
    ## 463         JAGAKARSA          TANJUNG BARAT 35-39.Perempuan   2022
    ## 464         JAGAKARSA                CIPEDAK 35-39.Perempuan   1774
    ## 465      PESANGGRAHAN           PESANGGRAHAN 35-39.Perempuan   1484
    ## 466      PESANGGRAHAN                BINTARO 35-39.Perempuan   2616
    ## 467      PESANGGRAHAN       PETUKANGAN UTARA 35-39.Perempuan   2791
    ## 468      PESANGGRAHAN     PETUKANGAN SELATAN 35-39.Perempuan   1727
    ## 469      PESANGGRAHAN                ULUJAMI 35-39.Perempuan   2186
    ## 470          MATRAMAN          PISANGAN BARU 35-39.Perempuan   1638
    ## 471          MATRAMAN        UTAN KAYU UTARA 35-39.Perempuan   1542
    ## 472          MATRAMAN             KAYU MANIS 35-39.Perempuan   1336
    ## 473          MATRAMAN             PAL MERIAM 35-39.Perempuan   1061
    ## 474          MATRAMAN          KEBON MANGGIS 35-39.Perempuan    873
    ## 475          MATRAMAN      UTAN KAYU SELATAN 35-39.Perempuan   1810
    ## 476       PULO GADUNG            PULO GADUNG 35-39.Perempuan   1836
    ## 477       PULO GADUNG         PISANGAN TIMUR 35-39.Perempuan   2200
    ## 478       PULO GADUNG               CIPINANG 35-39.Perempuan   2124
    ## 479       PULO GADUNG        JATINEGARA KAUM 35-39.Perempuan   1190
    ## 480       PULO GADUNG             RAWAMANGUN 35-39.Perempuan   2057
    ## 481       PULO GADUNG             KAYU PUTIH 35-39.Perempuan   2418
    ## 482       PULO GADUNG                   JATI 35-39.Perempuan   1797
    ## 483        JATINEGARA         KAMPUNG MELAYU 35-39.Perempuan   1154
    ## 484        JATINEGARA            BIDARA CINA 35-39.Perempuan   2064
    ## 485        JATINEGARA            BALI MESTER 35-39.Perempuan    466
    ## 486        JATINEGARA             RAWA BUNGA 35-39.Perempuan   1008
    ## 487        JATINEGARA      CIPINANG CEMPEDAK 35-39.Perempuan   1758
    ## 488        JATINEGARA         CIPINANG MUARA 35-39.Perempuan   2953
    ## 489        JATINEGARA CIPINANG BESAR SELATAN 35-39.Perempuan   1682
    ## 490        JATINEGARA   CIPINANG BESAR UTARA 35-39.Perempuan   2409
    ## 491       KRAMAT JATI            KRAMAT JATI 35-39.Perempuan   1799
    ## 492       KRAMAT JATI         KAMPUNG TENGAH 35-39.Perempuan   2135
    ## 493       KRAMAT JATI                  DUKUH 35-39.Perempuan   1210
    ## 494       KRAMAT JATI             BATU AMPAR 35-39.Perempuan   2417
    ## 495       KRAMAT JATI           BALE KAMBANG 35-39.Perempuan   1425
    ## 496       KRAMAT JATI              CILILITAN 35-39.Perempuan   2141
    ## 497       KRAMAT JATI                 CAWANG 35-39.Perempuan   1800
    ## 498        PASAR REBO                 GEDONG 35-39.Perempuan   1804
    ## 499        PASAR REBO                   BARU 35-39.Perempuan   1341
    ## 500        PASAR REBO              CIJANTUNG 35-39.Perempuan   1998
    ## 501        PASAR REBO               KALISARI 35-39.Perempuan   1951
    ## 502        PASAR REBO                PEKAYON 35-39.Perempuan   2060
    ## 503            CAKUNG             JATINEGARA 35-39.Perempuan   4775
    ## 504            CAKUNG            RAWA TERATE 35-39.Perempuan   1417
    ## 505            CAKUNG           PENGGILINGAN 35-39.Perempuan   4385
    ## 506            CAKUNG           CAKUNG TIMUR 35-39.Perempuan   2953
    ## 507            CAKUNG            PULO GEBANG 35-39.Perempuan   4030
    ## 508            CAKUNG          UJUNG MENTENG 35-39.Perempuan   1441
    ## 509            CAKUNG           CAKUNG BARAT 35-39.Perempuan   3275
    ## 510       DUREN SAWIT            DUREN SAWIT 35-39.Perempuan   3055
    ## 511       DUREN SAWIT           PONDOK BAMBU 35-39.Perempuan   3122
    ## 512       DUREN SAWIT                KLENDER 35-39.Perempuan   3569
    ## 513       DUREN SAWIT          PONDOK KELAPA 35-39.Perempuan   3356
    ## 514       DUREN SAWIT            MALAKA SARI 35-39.Perempuan   1703
    ## 515       DUREN SAWIT            MALAKA JAYA 35-39.Perempuan   1984
    ## 516       DUREN SAWIT            PONDOK KOPI 35-39.Perempuan   1604
    ## 517           MAKASAR                MAKASAR 35-39.Perempuan   1815
    ## 518           MAKASAR           PINANG RANTI 35-39.Perempuan   1284
    ## 519           MAKASAR             KEBON PALA 35-39.Perempuan   2502
    ## 520           MAKASAR  HALIM PERDANA KUSUMAH 35-39.Perempuan   1576
    ## 521           MAKASAR        CIPINANG MELAYU 35-39.Perempuan   2104
    ## 522           CIRACAS                CIRACAS 35-39.Perempuan   3085
    ## 523           CIRACAS                CIBUBUR 35-39.Perempuan   3175
    ## 524           CIRACAS       KELAPA DUA WETAN 35-39.Perempuan   2177
    ## 525           CIRACAS                SUSUKAN 35-39.Perempuan   1846
    ## 526           CIRACAS               RAMBUTAN 35-39.Perempuan   1849
    ## 527          CIPAYUNG               CIPAYUNG 35-39.Perempuan   1172
    ## 528          CIPAYUNG              CILANGKAP 35-39.Perempuan   1276
    ## 529          CIPAYUNG         PONDOK RANGGON 35-39.Perempuan   1064
    ## 530          CIPAYUNG                 MUNJUL 35-39.Perempuan   1112
    ## 531          CIPAYUNG                   SETU 35-39.Perempuan    928
    ## 532          CIPAYUNG             BAMBU APUS 35-39.Perempuan   1187
    ## 533          CIPAYUNG           LUBANG BUAYA 35-39.Perempuan   2988
    ## 534          CIPAYUNG                  CEGER 35-39.Perempuan    930

Split Fields

``` r
library(openxlsx)
library(reshape2)
penduduk.dki.xlsx <- read.xlsx(xlsxFile="https://storage.googleapis.com/dqlab-dataset/dkikepadatankelurahan2013.xlsx")
penduduk.dki.transform <- melt(data=penduduk.dki.xlsx, id.vars=c( "NAMA.KECAMATAN", "NAMA.KELURAHAN"), measure.vars = c("35-39.Laki-Laki", "35-39.Perempuan"), variable.name = "DEMOGRAFIK", value.name="JUMLAH") 
#Memecah isi kolom DEMOGRAFIK menjadi "RENTANG.UMUR" dan "JENIS.KELAMIN"
penduduk.dki.transform[c("RENTANG.UMUR", "JENIS.KELAMIN")] <- colsplit(penduduk.dki.transform$DEMOGRAFIK,"\\.",c("RENTANG.UMUR","JENIS.KELAMIN"))
penduduk.dki.transform$DEMOGRAFIK <- NULL
penduduk.dki.transform
```

    ##        NAMA.KECAMATAN         NAMA.KELURAHAN JUMLAH RENTANG.UMUR JENIS.KELAMIN
    ## 1     KEP. SERIBU UTR            P. PANGGANG    231        35-39     Laki-Laki
    ## 2     KEP. SERIBU UTR              P. KELAPA     84        35-39     Laki-Laki
    ## 3     KEP. SERIBU UTR             P. HARAPAN    255        35-39     Laki-Laki
    ## 4     KEP. SERIBU SLT         P. UNTUNG JAWA    199        35-39     Laki-Laki
    ## 5     KEP. SERIBU SLT              P. TIDUNG     98        35-39     Laki-Laki
    ## 6     KEP. SERIBU SLT                P. PARI    113        35-39     Laki-Laki
    ## 7              GAMBIR                 GAMBIR    166        35-39     Laki-Laki
    ## 8              GAMBIR                 CIDENG    850        35-39     Laki-Laki
    ## 9              GAMBIR           PETOJO UTARA    954        35-39     Laki-Laki
    ## 10             GAMBIR         PETOJO SELATAN    752        35-39     Laki-Laki
    ## 11             GAMBIR           KEBON KELAPA    592        35-39     Laki-Laki
    ## 12             GAMBIR              DURI PULO   1213        35-39     Laki-Laki
    ## 13        SAWAH BESAR             PASAR BARU    714        35-39     Laki-Laki
    ## 14        SAWAH BESAR           KARANG ANYAR   1575        35-39     Laki-Laki
    ## 15        SAWAH BESAR                KARTINI   1307        35-39     Laki-Laki
    ## 16        SAWAH BESAR    GUNUNG SAHARI UTARA    817        35-39     Laki-Laki
    ## 17        SAWAH BESAR     MANGGA DUA SELATAN   1683        35-39     Laki-Laki
    ## 18          KEMAYORAN              KEMAYORAN   1164        35-39     Laki-Laki
    ## 19          KEMAYORAN           KEBON KOSONG   1644        35-39     Laki-Laki
    ## 20          KEMAYORAN          HARAPAN MULIA   1256        35-39     Laki-Laki
    ## 21          KEMAYORAN                SERDANG   1603        35-39     Laki-Laki
    ## 22          KEMAYORAN  GUNUNG SAHARI SELATAN   1071        35-39     Laki-Laki
    ## 23          KEMAYORAN           CEMPAKA BARU   1750        35-39     Laki-Laki
    ## 24          KEMAYORAN             SUMUR BATU   1452        35-39     Laki-Laki
    ## 25          KEMAYORAN           UTAN PANJANG   1610        35-39     Laki-Laki
    ## 26              SENEN                  SENEN    398        35-39     Laki-Laki
    ## 27              SENEN                 KENARI    456        35-39     Laki-Laki
    ## 28              SENEN                PASEBAN   1266        35-39     Laki-Laki
    ## 29              SENEN                 KRAMAT   1552        35-39     Laki-Laki
    ## 30              SENEN                KWITANG    908        35-39     Laki-Laki
    ## 31              SENEN                 BUNGUR   1046        35-39     Laki-Laki
    ## 32      CEMPAKA PUTIH    CEMPAKA PUTIH TIMUR   1264        35-39     Laki-Laki
    ## 33      CEMPAKA PUTIH    CEMPAKA PUTIH BARAT   1858        35-39     Laki-Laki
    ## 34      CEMPAKA PUTIH               RAWASARI   1200        35-39     Laki-Laki
    ## 35            MENTENG                MENTENG   1349        35-39     Laki-Laki
    ## 36            MENTENG             PEGANGSAAN   1172        35-39     Laki-Laki
    ## 37            MENTENG                 CIKINI    424        35-39     Laki-Laki
    ## 38            MENTENG             GONDANGDIA    192        35-39     Laki-Laki
    ## 39            MENTENG            KEBON SIRIH    733        35-39     Laki-Laki
    ## 40        TANAH ABANG                 GELORA    185        35-39     Laki-Laki
    ## 41        TANAH ABANG        BENDUNGAN HILIR   1124        35-39     Laki-Laki
    ## 42        TANAH ABANG          KARET TENGSIN   1118        35-39     Laki-Laki
    ## 43        TANAH ABANG             PETAMBURAN   1851        35-39     Laki-Laki
    ## 44        TANAH ABANG           KEBON MELATI   1862        35-39     Laki-Laki
    ## 45        TANAH ABANG           KEBON KACANG   1150        35-39     Laki-Laki
    ## 46        TANAH ABANG           KAMPUNG BALI    612        35-39     Laki-Laki
    ## 47         JOHAR BARU             JOHAR BARU   2036        35-39     Laki-Laki
    ## 48         JOHAR BARU           KAMPUNG RAWA   1210        35-39     Laki-Laki
    ## 49         JOHAR BARU                  GALUR    999        35-39     Laki-Laki
    ## 50         JOHAR BARU           TANAH TINGGI   2118        35-39     Laki-Laki
    ## 51        PENJARINGAN            PENJARINGAN   9225        35-39     Laki-Laki
    ## 52        PENJARINGAN            KAMAL MUARA   1045        35-39     Laki-Laki
    ## 53        PENJARINGAN            KAPUK MUARA   2763        35-39     Laki-Laki
    ## 54        PENJARINGAN              PEJAGALAN   7137        35-39     Laki-Laki
    ## 55        PENJARINGAN                  PLUIT   3656        35-39     Laki-Laki
    ## 56      TANJUNG PRIOK          TANJUNG PRIOK   3374        35-39     Laki-Laki
    ## 57      TANJUNG PRIOK            SUNTER JAYA   5374        35-39     Laki-Laki
    ## 58      TANJUNG PRIOK               PAPANGGO   3667        35-39     Laki-Laki
    ## 59      TANJUNG PRIOK           SUNGAI BAMBU   2807        35-39     Laki-Laki
    ## 60      TANJUNG PRIOK           KEBON BAWANG   4677        35-39     Laki-Laki
    ## 61      TANJUNG PRIOK           SUNTER AGUNG   6094        35-39     Laki-Laki
    ## 62      TANJUNG PRIOK                WARAKAS   4224        35-39     Laki-Laki
    ## 63               KOJA                   KOJA   3088        35-39     Laki-Laki
    ## 64               KOJA             TUGU UTARA   6608        35-39     Laki-Laki
    ## 65               KOJA                  LAGOA   5931        35-39     Laki-Laki
    ## 66               KOJA       RAWA BADAK UTARA   3260        35-39     Laki-Laki
    ## 67               KOJA           TUGU SELATAN   3744        35-39     Laki-Laki
    ## 68               KOJA     RAWA BADAK SELATAN   3910        35-39     Laki-Laki
    ## 69          CILINCING              CILINCING   4654        35-39     Laki-Laki
    ## 70          CILINCING               SUKAPURA   5221        35-39     Laki-Laki
    ## 71          CILINCING                MARUNDA   2187        35-39     Laki-Laki
    ## 72          CILINCING              KALI BARU   7616        35-39     Laki-Laki
    ## 73          CILINCING           SEMPER TIMUR   3230        35-39     Laki-Laki
    ## 74          CILINCING                ROROTAN   3442        35-39     Laki-Laki
    ## 75          CILINCING           SEMPER BARAT   6419        35-39     Laki-Laki
    ## 76         PADEMANGAN       PADEMANGAN TIMUR   3005        35-39     Laki-Laki
    ## 77         PADEMANGAN       PADEMANGAN BARAT   7178        35-39     Laki-Laki
    ## 78         PADEMANGAN                  ANCOL   2259        35-39     Laki-Laki
    ## 79      KELAPA GADING    KELAPA GADING TIMUR   2539        35-39     Laki-Laki
    ## 80      KELAPA GADING         PEGANGSAAN DUA   4170        35-39     Laki-Laki
    ## 81      KELAPA GADING    KELAPA GADING BARAT   2628        35-39     Laki-Laki
    ## 82         CENGKARENG       CENGKARENG BARAT   5316        35-39     Laki-Laki
    ## 83         CENGKARENG           DURI KOSAMBI   6922        35-39     Laki-Laki
    ## 84         CENGKARENG             RAWA BUAYA   5632        35-39     Laki-Laki
    ## 85         CENGKARENG     KEDAUNG KALI ANGKE   2951        35-39     Laki-Laki
    ## 86         CENGKARENG                  KAPUK  13011        35-39     Laki-Laki
    ## 87         CENGKARENG       CENGKARENG TIMUR   7146        35-39     Laki-Laki
    ## 88  GROGOL PETAMBURAN                 GROGOL   1530        35-39     Laki-Laki
    ## 89  GROGOL PETAMBURAN    TANJUNG DUREN UTARA   1277        35-39     Laki-Laki
    ## 90  GROGOL PETAMBURAN                 TOMANG   2404        35-39     Laki-Laki
    ## 91  GROGOL PETAMBURAN               JELAMBAR   2358        35-39     Laki-Laki
    ## 92  GROGOL PETAMBURAN  TANJUNG DUREN SELATAN   1857        35-39     Laki-Laki
    ## 93  GROGOL PETAMBURAN          JELAMBAR BARU   3165        35-39     Laki-Laki
    ## 94  GROGOL PETAMBURAN          WIJAYA KUSUMA   3523        35-39     Laki-Laki
    ## 95         TAMAN SARI             TAMAN SARI   1365        35-39     Laki-Laki
    ## 96         TAMAN SARI                 KRUKUT   1848        35-39     Laki-Laki
    ## 97         TAMAN SARI                 MAPHAR   1555        35-39     Laki-Laki
    ## 98         TAMAN SARI                 TANGKI   1248        35-39     Laki-Laki
    ## 99         TAMAN SARI           MANGGA BESAR    675        35-39     Laki-Laki
    ## 100        TAMAN SARI              KEAGUNGAN   1673        35-39     Laki-Laki
    ## 101        TAMAN SARI                 GLODOK    650        35-39     Laki-Laki
    ## 102        TAMAN SARI              PINANGSIA    991        35-39     Laki-Laki
    ## 103           TAMBORA                TAMBORA    968        35-39     Laki-Laki
    ## 104           TAMBORA             KALI ANYAR   2532        35-39     Laki-Laki
    ## 105           TAMBORA             DURI UTARA   1919        35-39     Laki-Laki
    ## 106           TAMBORA           TANAH SEREAL   2485        35-39     Laki-Laki
    ## 107           TAMBORA              KERENDANG   2057        35-39     Laki-Laki
    ## 108           TAMBORA          JEMBATAN BESI   3124        35-39     Laki-Laki
    ## 109           TAMBORA                  ANGKE   2767        35-39     Laki-Laki
    ## 110           TAMBORA          JEMBATAN LIMA   2104        35-39     Laki-Laki
    ## 111           TAMBORA                PEKOJAN   2061        35-39     Laki-Laki
    ## 112           TAMBORA             ROA MALAKA    257        35-39     Laki-Laki
    ## 113           TAMBORA           DURI SELATAN   1319        35-39     Laki-Laki
    ## 114       KEBON JERUK            KEBON JERUK   4362        35-39     Laki-Laki
    ## 115       KEBON JERUK         SUKABUMI UTARA   3197        35-39     Laki-Laki
    ## 116       KEBON JERUK       SUKABUMI SELATAN   3396        35-39     Laki-Laki
    ## 117       KEBON JERUK             KELAPA DUA   1962        35-39     Laki-Laki
    ## 118       KEBON JERUK              DURI KEPA   5160        35-39     Laki-Laki
    ## 119       KEBON JERUK           KEDOYA UTARA   3914        35-39     Laki-Laki
    ## 120       KEBON JERUK         KEDOYA SELATAN   2709        35-39     Laki-Laki
    ## 121        KALI DERES              KALIDERES   6660        35-39     Laki-Laki
    ## 122        KALI DERES                SEMANAN   6508        35-39     Laki-Laki
    ## 123        KALI DERES             TEGAL ALUR   8053        35-39     Laki-Laki
    ## 124        KALI DERES                  KAMAL   4847        35-39     Laki-Laki
    ## 125        KALI DERES             PEGADUNGAN   5990        35-39     Laki-Laki
    ## 126          PALMERAH               PALMERAH   5308        35-39     Laki-Laki
    ## 127          PALMERAH                  SLIPI   1445        35-39     Laki-Laki
    ## 128          PALMERAH       KOTA BAMBU UTARA   2268        35-39     Laki-Laki
    ## 129          PALMERAH              JATI PULO   2575        35-39     Laki-Laki
    ## 130          PALMERAH            KEMANGGISAN   2642        35-39     Laki-Laki
    ## 131          PALMERAH     KOTA BAMBU SELATAN   1967        35-39     Laki-Laki
    ## 132         KEMBANGAN        KEMBANGAN UTARA   4531        35-39     Laki-Laki
    ## 133         KEMBANGAN           MERUYA UTARA   3545        35-39     Laki-Laki
    ## 134         KEMBANGAN         MERUYA SELATAN   2471        35-39     Laki-Laki
    ## 135         KEMBANGAN              SRENGSENG   3761        35-39     Laki-Laki
    ## 136         KEMBANGAN                  JOGLO   3226        35-39     Laki-Laki
    ## 137         KEMBANGAN      KEMBANGAN SELATAN   2439        35-39     Laki-Laki
    ## 138             TEBET            TEBET TIMUR    838        35-39     Laki-Laki
    ## 139             TEBET            TEBET BARAT   1060        35-39     Laki-Laki
    ## 140             TEBET          MENTENG DALAM   2029        35-39     Laki-Laki
    ## 141             TEBET             KEBON BARU   2004        35-39     Laki-Laki
    ## 142             TEBET             BUKIT DURI   1880        35-39     Laki-Laki
    ## 143             TEBET      MANGGARAI SELATAN   1239        35-39     Laki-Laki
    ## 144             TEBET              MANGGARAI   1545        35-39     Laki-Laki
    ## 145        SETIA BUDI             SETIA BUDI    168        35-39     Laki-Laki
    ## 146        SETIA BUDI         KARET SEMANGGI    126        35-39     Laki-Laki
    ## 147        SETIA BUDI         KARET KUNINGAN    879        35-39     Laki-Laki
    ## 148        SETIA BUDI                  KARET    603        35-39     Laki-Laki
    ## 149        SETIA BUDI           MENTENG ATAS   1504        35-39     Laki-Laki
    ## 150        SETIA BUDI          PASAR MANGGIS   1445        35-39     Laki-Laki
    ## 151        SETIA BUDI                 GUNTUR    208        35-39     Laki-Laki
    ## 152        SETIA BUDI         KUNINGAN TIMUR    328        35-39     Laki-Laki
    ## 153  MAMPANG PRAPATAN       MAMPANG PRAPATAN   1101        35-39     Laki-Laki
    ## 154  MAMPANG PRAPATAN                 BANGKA   1119        35-39     Laki-Laki
    ## 155  MAMPANG PRAPATAN           PELA MAMPANG   2458        35-39     Laki-Laki
    ## 156  MAMPANG PRAPATAN           TEGAL PARANG   1826        35-39     Laki-Laki
    ## 157  MAMPANG PRAPATAN         KUNINGAN BARAT    727        35-39     Laki-Laki
    ## 158      PASAR MINGGU           PASAR MINGGU   1296        35-39     Laki-Laki
    ## 159      PASAR MINGGU            JATI PADANG   2023        35-39     Laki-Laki
    ## 160      PASAR MINGGU         CILANDAK TIMUR   1398        35-39     Laki-Laki
    ## 161      PASAR MINGGU                RAGUNAN   2284        35-39     Laki-Laki
    ## 162      PASAR MINGGU          PEJATEN TIMUR   3168        35-39     Laki-Laki
    ## 163      PASAR MINGGU          PEJATEN BARAT   1963        35-39     Laki-Laki
    ## 164      PASAR MINGGU              KEBAGUSAN   2300        35-39     Laki-Laki
    ## 165    KEBAYORAN LAMA   KEBAYORAN LAMA UTARA   2638        35-39     Laki-Laki
    ## 166    KEBAYORAN LAMA          PONDOK PINANG   2770        35-39     Laki-Laki
    ## 167    KEBAYORAN LAMA                CIPULIR   2191        35-39     Laki-Laki
    ## 168    KEBAYORAN LAMA           GROGOL UTARA   2266        35-39     Laki-Laki
    ## 169    KEBAYORAN LAMA         GROGOL SELATAN   2309        35-39     Laki-Laki
    ## 170    KEBAYORAN LAMA KEBAYORAN LAMA SELATAN   2316        35-39     Laki-Laki
    ## 171          CILANDAK         CILANDAK BARAT   2700        35-39     Laki-Laki
    ## 172          CILANDAK            LEBAK BULUS   1823        35-39     Laki-Laki
    ## 173          CILANDAK            PONDOK LABU   2261        35-39     Laki-Laki
    ## 174          CILANDAK       GANDARIA SELATAN   1145        35-39     Laki-Laki
    ## 175          CILANDAK         CIPETE SELATAN   1387        35-39     Laki-Laki
    ## 176    KEBAYORAN BARU                MELAWAI    116        35-39     Laki-Laki
    ## 177    KEBAYORAN BARU                 GUNUNG    423        35-39     Laki-Laki
    ## 178    KEBAYORAN BARU            KRAMAT PELA    706        35-39     Laki-Laki
    ## 179    KEBAYORAN BARU                 SELONG    178        35-39     Laki-Laki
    ## 180    KEBAYORAN BARU             RAWA BARAT    274        35-39     Laki-Laki
    ## 181    KEBAYORAN BARU                SENAYAN    176        35-39     Laki-Laki
    ## 182    KEBAYORAN BARU                   PULO    256        35-39     Laki-Laki
    ## 183    KEBAYORAN BARU              PETOGOGAN    621        35-39     Laki-Laki
    ## 184    KEBAYORAN BARU         GANDARIA UTARA   2056        35-39     Laki-Laki
    ## 185    KEBAYORAN BARU           CIPETE UTARA   1907        35-39     Laki-Laki
    ## 186          PANCORAN               PANCORAN   1026        35-39     Laki-Laki
    ## 187          PANCORAN               KALIBATA   2300        35-39     Laki-Laki
    ## 188          PANCORAN              RAWA JATI    990        35-39     Laki-Laki
    ## 189          PANCORAN             DUREN TIGA   1540        35-39     Laki-Laki
    ## 190          PANCORAN             PENGADEGAN   1140        35-39     Laki-Laki
    ## 191          PANCORAN                 CIKOKO    698        35-39     Laki-Laki
    ## 192         JAGAKARSA              JAGAKARSA   3050        35-39     Laki-Laki
    ## 193         JAGAKARSA        SRENGSENG SAWAH   2783        35-39     Laki-Laki
    ## 194         JAGAKARSA               CIGANJUR   1859        35-39     Laki-Laki
    ## 195         JAGAKARSA          LENTENG AGUNG   2617        35-39     Laki-Laki
    ## 196         JAGAKARSA          TANJUNG BARAT   2017        35-39     Laki-Laki
    ## 197         JAGAKARSA                CIPEDAK   1708        35-39     Laki-Laki
    ## 198      PESANGGRAHAN           PESANGGRAHAN   1499        35-39     Laki-Laki
    ## 199      PESANGGRAHAN                BINTARO   2675        35-39     Laki-Laki
    ## 200      PESANGGRAHAN       PETUKANGAN UTARA   2787        35-39     Laki-Laki
    ## 201      PESANGGRAHAN     PETUKANGAN SELATAN   1836        35-39     Laki-Laki
    ## 202      PESANGGRAHAN                ULUJAMI   2304        35-39     Laki-Laki
    ## 203          MATRAMAN          PISANGAN BARU   1759        35-39     Laki-Laki
    ## 204          MATRAMAN        UTAN KAYU UTARA   1606        35-39     Laki-Laki
    ## 205          MATRAMAN             KAYU MANIS   1377        35-39     Laki-Laki
    ## 206          MATRAMAN             PAL MERIAM   1101        35-39     Laki-Laki
    ## 207          MATRAMAN          KEBON MANGGIS    840        35-39     Laki-Laki
    ## 208          MATRAMAN      UTAN KAYU SELATAN   1820        35-39     Laki-Laki
    ## 209       PULO GADUNG            PULO GADUNG   1998        35-39     Laki-Laki
    ## 210       PULO GADUNG         PISANGAN TIMUR   2249        35-39     Laki-Laki
    ## 211       PULO GADUNG               CIPINANG   2192        35-39     Laki-Laki
    ## 212       PULO GADUNG        JATINEGARA KAUM   1278        35-39     Laki-Laki
    ## 213       PULO GADUNG             RAWAMANGUN   2054        35-39     Laki-Laki
    ## 214       PULO GADUNG             KAYU PUTIH   2361        35-39     Laki-Laki
    ## 215       PULO GADUNG                   JATI   1764        35-39     Laki-Laki
    ## 216        JATINEGARA         KAMPUNG MELAYU   1361        35-39     Laki-Laki
    ## 217        JATINEGARA            BIDARA CINA   2105        35-39     Laki-Laki
    ## 218        JATINEGARA            BALI MESTER    444        35-39     Laki-Laki
    ## 219        JATINEGARA             RAWA BUNGA   1131        35-39     Laki-Laki
    ## 220        JATINEGARA      CIPINANG CEMPEDAK   1614        35-39     Laki-Laki
    ## 221        JATINEGARA         CIPINANG MUARA   3063        35-39     Laki-Laki
    ## 222        JATINEGARA CIPINANG BESAR SELATAN   1875        35-39     Laki-Laki
    ## 223        JATINEGARA   CIPINANG BESAR UTARA   2704        35-39     Laki-Laki
    ## 224       KRAMAT JATI            KRAMAT JATI   1946        35-39     Laki-Laki
    ## 225       KRAMAT JATI         KAMPUNG TENGAH   2224        35-39     Laki-Laki
    ## 226       KRAMAT JATI                  DUKUH   1277        35-39     Laki-Laki
    ## 227       KRAMAT JATI             BATU AMPAR   2480        35-39     Laki-Laki
    ## 228       KRAMAT JATI           BALE KAMBANG   1413        35-39     Laki-Laki
    ## 229       KRAMAT JATI              CILILITAN   2265        35-39     Laki-Laki
    ## 230       KRAMAT JATI                 CAWANG   1942        35-39     Laki-Laki
    ## 231        PASAR REBO                 GEDONG   1823        35-39     Laki-Laki
    ## 232        PASAR REBO                   BARU   1678        35-39     Laki-Laki
    ## 233        PASAR REBO              CIJANTUNG   2107        35-39     Laki-Laki
    ## 234        PASAR REBO               KALISARI   2006        35-39     Laki-Laki
    ## 235        PASAR REBO                PEKAYON   2139        35-39     Laki-Laki
    ## 236            CAKUNG             JATINEGARA   5035        35-39     Laki-Laki
    ## 237            CAKUNG            RAWA TERATE   1565        35-39     Laki-Laki
    ## 238            CAKUNG           PENGGILINGAN   4651        35-39     Laki-Laki
    ## 239            CAKUNG           CAKUNG TIMUR   3053        35-39     Laki-Laki
    ## 240            CAKUNG            PULO GEBANG   4162        35-39     Laki-Laki
    ## 241            CAKUNG          UJUNG MENTENG   1420        35-39     Laki-Laki
    ## 242            CAKUNG           CAKUNG BARAT   3285        35-39     Laki-Laki
    ## 243       DUREN SAWIT            DUREN SAWIT   3210        35-39     Laki-Laki
    ## 244       DUREN SAWIT           PONDOK BAMBU   3427        35-39     Laki-Laki
    ## 245       DUREN SAWIT                KLENDER   3896        35-39     Laki-Laki
    ## 246       DUREN SAWIT          PONDOK KELAPA   3467        35-39     Laki-Laki
    ## 247       DUREN SAWIT            MALAKA SARI   1682        35-39     Laki-Laki
    ## 248       DUREN SAWIT            MALAKA JAYA   1949        35-39     Laki-Laki
    ## 249       DUREN SAWIT            PONDOK KOPI   1611        35-39     Laki-Laki
    ## 250           MAKASAR                MAKASAR   1888        35-39     Laki-Laki
    ## 251           MAKASAR           PINANG RANTI   1299        35-39     Laki-Laki
    ## 252           MAKASAR             KEBON PALA   2689        35-39     Laki-Laki
    ## 253           MAKASAR  HALIM PERDANA KUSUMAH   1479        35-39     Laki-Laki
    ## 254           MAKASAR        CIPINANG MELAYU   2208        35-39     Laki-Laki
    ## 255           CIRACAS                CIRACAS   3179        35-39     Laki-Laki
    ## 256           CIRACAS                CIBUBUR   3311        35-39     Laki-Laki
    ## 257           CIRACAS       KELAPA DUA WETAN   2185        35-39     Laki-Laki
    ## 258           CIRACAS                SUSUKAN   1988        35-39     Laki-Laki
    ## 259           CIRACAS               RAMBUTAN   1857        35-39     Laki-Laki
    ## 260          CIPAYUNG               CIPAYUNG   1241        35-39     Laki-Laki
    ## 261          CIPAYUNG              CILANGKAP   1237        35-39     Laki-Laki
    ## 262          CIPAYUNG         PONDOK RANGGON   1088        35-39     Laki-Laki
    ## 263          CIPAYUNG                 MUNJUL   1167        35-39     Laki-Laki
    ## 264          CIPAYUNG                   SETU    937        35-39     Laki-Laki
    ## 265          CIPAYUNG             BAMBU APUS   1242        35-39     Laki-Laki
    ## 266          CIPAYUNG           LUBANG BUAYA   3258        35-39     Laki-Laki
    ## 267          CIPAYUNG                  CEGER   1007        35-39     Laki-Laki
    ## 268   KEP. SERIBU UTR            P. PANGGANG    235        35-39     Perempuan
    ## 269   KEP. SERIBU UTR              P. KELAPA     88        35-39     Perempuan
    ## 270   KEP. SERIBU UTR             P. HARAPAN    238        35-39     Perempuan
    ## 271   KEP. SERIBU SLT         P. UNTUNG JAWA    185        35-39     Perempuan
    ## 272   KEP. SERIBU SLT              P. TIDUNG     75        35-39     Perempuan
    ## 273   KEP. SERIBU SLT                P. PARI    112        35-39     Perempuan
    ## 274            GAMBIR                 GAMBIR    174        35-39     Perempuan
    ## 275            GAMBIR                 CIDENG    748        35-39     Perempuan
    ## 276            GAMBIR           PETOJO UTARA    920        35-39     Perempuan
    ## 277            GAMBIR         PETOJO SELATAN    675        35-39     Perempuan
    ## 278            GAMBIR           KEBON KELAPA    491        35-39     Perempuan
    ## 279            GAMBIR              DURI PULO   1106        35-39     Perempuan
    ## 280       SAWAH BESAR             PASAR BARU    611        35-39     Perempuan
    ## 281       SAWAH BESAR           KARANG ANYAR   1485        35-39     Perempuan
    ## 282       SAWAH BESAR                KARTINI   1177        35-39     Perempuan
    ## 283       SAWAH BESAR    GUNUNG SAHARI UTARA    835        35-39     Perempuan
    ## 284       SAWAH BESAR     MANGGA DUA SELATAN   1662        35-39     Perempuan
    ## 285         KEMAYORAN              KEMAYORAN   1063        35-39     Perempuan
    ## 286         KEMAYORAN           KEBON KOSONG   1542        35-39     Perempuan
    ## 287         KEMAYORAN          HARAPAN MULIA   1213        35-39     Perempuan
    ## 288         KEMAYORAN                SERDANG   1559        35-39     Perempuan
    ## 289         KEMAYORAN  GUNUNG SAHARI SELATAN    979        35-39     Perempuan
    ## 290         KEMAYORAN           CEMPAKA BARU   1710        35-39     Perempuan
    ## 291         KEMAYORAN             SUMUR BATU   1372        35-39     Perempuan
    ## 292         KEMAYORAN           UTAN PANJANG   1549        35-39     Perempuan
    ## 293             SENEN                  SENEN    428        35-39     Perempuan
    ## 294             SENEN                 KENARI    447        35-39     Perempuan
    ## 295             SENEN                PASEBAN   1232        35-39     Perempuan
    ## 296             SENEN                 KRAMAT   1479        35-39     Perempuan
    ## 297             SENEN                KWITANG    793        35-39     Perempuan
    ## 298             SENEN                 BUNGUR    993        35-39     Perempuan
    ## 299     CEMPAKA PUTIH    CEMPAKA PUTIH TIMUR   1267        35-39     Perempuan
    ## 300     CEMPAKA PUTIH    CEMPAKA PUTIH BARAT   1811        35-39     Perempuan
    ## 301     CEMPAKA PUTIH               RAWASARI   1160        35-39     Perempuan
    ## 302           MENTENG                MENTENG   1194        35-39     Perempuan
    ## 303           MENTENG             PEGANGSAAN   1096        35-39     Perempuan
    ## 304           MENTENG                 CIKINI    428        35-39     Perempuan
    ## 305           MENTENG             GONDANGDIA    165        35-39     Perempuan
    ## 306           MENTENG            KEBON SIRIH    717        35-39     Perempuan
    ## 307       TANAH ABANG                 GELORA    178        35-39     Perempuan
    ## 308       TANAH ABANG        BENDUNGAN HILIR   1138        35-39     Perempuan
    ## 309       TANAH ABANG          KARET TENGSIN   1078        35-39     Perempuan
    ## 310       TANAH ABANG             PETAMBURAN   1780        35-39     Perempuan
    ## 311       TANAH ABANG           KEBON MELATI   1721        35-39     Perempuan
    ## 312       TANAH ABANG           KEBON KACANG   1041        35-39     Perempuan
    ## 313       TANAH ABANG           KAMPUNG BALI    613        35-39     Perempuan
    ## 314        JOHAR BARU             JOHAR BARU   1878        35-39     Perempuan
    ## 315        JOHAR BARU           KAMPUNG RAWA   1255        35-39     Perempuan
    ## 316        JOHAR BARU                  GALUR   1060        35-39     Perempuan
    ## 317        JOHAR BARU           TANAH TINGGI   2013        35-39     Perempuan
    ## 318       PENJARINGAN            PENJARINGAN   5535        35-39     Perempuan
    ## 319       PENJARINGAN            KAMAL MUARA    517        35-39     Perempuan
    ## 320       PENJARINGAN            KAPUK MUARA   1631        35-39     Perempuan
    ## 321       PENJARINGAN              PEJAGALAN   4468        35-39     Perempuan
    ## 322       PENJARINGAN                  PLUIT   2264        35-39     Perempuan
    ## 323     TANJUNG PRIOK          TANJUNG PRIOK   2025        35-39     Perempuan
    ## 324     TANJUNG PRIOK            SUNTER JAYA   3427        35-39     Perempuan
    ## 325     TANJUNG PRIOK               PAPANGGO   2290        35-39     Perempuan
    ## 326     TANJUNG PRIOK           SUNGAI BAMBU   1749        35-39     Perempuan
    ## 327     TANJUNG PRIOK           KEBON BAWANG   3009        35-39     Perempuan
    ## 328     TANJUNG PRIOK           SUNTER AGUNG   3710        35-39     Perempuan
    ## 329     TANJUNG PRIOK                WARAKAS   2608        35-39     Perempuan
    ## 330              KOJA                   KOJA   1767        35-39     Perempuan
    ## 331              KOJA             TUGU UTARA   3954        35-39     Perempuan
    ## 332              KOJA                  LAGOA   3342        35-39     Perempuan
    ## 333              KOJA       RAWA BADAK UTARA   2064        35-39     Perempuan
    ## 334              KOJA           TUGU SELATAN   2235        35-39     Perempuan
    ## 335              KOJA     RAWA BADAK SELATAN   2420        35-39     Perempuan
    ## 336         CILINCING              CILINCING   2614        35-39     Perempuan
    ## 337         CILINCING               SUKAPURA   3376        35-39     Perempuan
    ## 338         CILINCING                MARUNDA   1207        35-39     Perempuan
    ## 339         CILINCING              KALI BARU   4096        35-39     Perempuan
    ## 340         CILINCING           SEMPER TIMUR   1683        35-39     Perempuan
    ## 341         CILINCING                ROROTAN   1876        35-39     Perempuan
    ## 342         CILINCING           SEMPER BARAT   3579        35-39     Perempuan
    ## 343        PADEMANGAN       PADEMANGAN TIMUR   1935        35-39     Perempuan
    ## 344        PADEMANGAN       PADEMANGAN BARAT   4264        35-39     Perempuan
    ## 345        PADEMANGAN                  ANCOL   1380        35-39     Perempuan
    ## 346     KELAPA GADING    KELAPA GADING TIMUR   1744        35-39     Perempuan
    ## 347     KELAPA GADING         PEGANGSAAN DUA   2259        35-39     Perempuan
    ## 348     KELAPA GADING    KELAPA GADING BARAT   1433        35-39     Perempuan
    ## 349        CENGKARENG       CENGKARENG BARAT   3221        35-39     Perempuan
    ## 350        CENGKARENG           DURI KOSAMBI   3764        35-39     Perempuan
    ## 351        CENGKARENG             RAWA BUAYA   3396        35-39     Perempuan
    ## 352        CENGKARENG     KEDAUNG KALI ANGKE   1756        35-39     Perempuan
    ## 353        CENGKARENG                  KAPUK   7488        35-39     Perempuan
    ## 354        CENGKARENG       CENGKARENG TIMUR   4147        35-39     Perempuan
    ## 355 GROGOL PETAMBURAN                 GROGOL    903        35-39     Perempuan
    ## 356 GROGOL PETAMBURAN    TANJUNG DUREN UTARA    812        35-39     Perempuan
    ## 357 GROGOL PETAMBURAN                 TOMANG   1449        35-39     Perempuan
    ## 358 GROGOL PETAMBURAN               JELAMBAR   1581        35-39     Perempuan
    ## 359 GROGOL PETAMBURAN  TANJUNG DUREN SELATAN   1220        35-39     Perempuan
    ## 360 GROGOL PETAMBURAN          JELAMBAR BARU   2116        35-39     Perempuan
    ## 361 GROGOL PETAMBURAN          WIJAYA KUSUMA   2301        35-39     Perempuan
    ## 362        TAMAN SARI             TAMAN SARI    729        35-39     Perempuan
    ## 363        TAMAN SARI                 KRUKUT   1107        35-39     Perempuan
    ## 364        TAMAN SARI                 MAPHAR    919        35-39     Perempuan
    ## 365        TAMAN SARI                 TANGKI    691        35-39     Perempuan
    ## 366        TAMAN SARI           MANGGA BESAR    386        35-39     Perempuan
    ## 367        TAMAN SARI              KEAGUNGAN    975        35-39     Perempuan
    ## 368        TAMAN SARI                 GLODOK    359        35-39     Perempuan
    ## 369        TAMAN SARI              PINANGSIA    600        35-39     Perempuan
    ## 370           TAMBORA                TAMBORA    588        35-39     Perempuan
    ## 371           TAMBORA             KALI ANYAR   1567        35-39     Perempuan
    ## 372           TAMBORA             DURI UTARA   1120        35-39     Perempuan
    ## 373           TAMBORA           TANAH SEREAL   1386        35-39     Perempuan
    ## 374           TAMBORA              KERENDANG   1212        35-39     Perempuan
    ## 375           TAMBORA          JEMBATAN BESI   2075        35-39     Perempuan
    ## 376           TAMBORA                  ANGKE   1721        35-39     Perempuan
    ## 377           TAMBORA          JEMBATAN LIMA   1277        35-39     Perempuan
    ## 378           TAMBORA                PEKOJAN   1197        35-39     Perempuan
    ## 379           TAMBORA             ROA MALAKA    180        35-39     Perempuan
    ## 380           TAMBORA           DURI SELATAN    769        35-39     Perempuan
    ## 381       KEBON JERUK            KEBON JERUK   2563        35-39     Perempuan
    ## 382       KEBON JERUK         SUKABUMI UTARA   2005        35-39     Perempuan
    ## 383       KEBON JERUK       SUKABUMI SELATAN   2049        35-39     Perempuan
    ## 384       KEBON JERUK             KELAPA DUA   1161        35-39     Perempuan
    ## 385       KEBON JERUK              DURI KEPA   3164        35-39     Perempuan
    ## 386       KEBON JERUK           KEDOYA UTARA   2355        35-39     Perempuan
    ## 387       KEBON JERUK         KEDOYA SELATAN   1675        35-39     Perempuan
    ## 388        KALI DERES              KALIDERES   3659        35-39     Perempuan
    ## 389        KALI DERES                SEMANAN   3687        35-39     Perempuan
    ## 390        KALI DERES             TEGAL ALUR   4591        35-39     Perempuan
    ## 391        KALI DERES                  KAMAL   2640        35-39     Perempuan
    ## 392        KALI DERES             PEGADUNGAN   3120        35-39     Perempuan
    ## 393          PALMERAH               PALMERAH   3083        35-39     Perempuan
    ## 394          PALMERAH                  SLIPI    856        35-39     Perempuan
    ## 395          PALMERAH       KOTA BAMBU UTARA   1359        35-39     Perempuan
    ## 396          PALMERAH              JATI PULO   1451        35-39     Perempuan
    ## 397          PALMERAH            KEMANGGISAN   1596        35-39     Perempuan
    ## 398          PALMERAH     KOTA BAMBU SELATAN   1141        35-39     Perempuan
    ## 399         KEMBANGAN        KEMBANGAN UTARA   2734        35-39     Perempuan
    ## 400         KEMBANGAN           MERUYA UTARA   2226        35-39     Perempuan
    ## 401         KEMBANGAN         MERUYA SELATAN   1427        35-39     Perempuan
    ## 402         KEMBANGAN              SRENGSENG   2109        35-39     Perempuan
    ## 403         KEMBANGAN                  JOGLO   1840        35-39     Perempuan
    ## 404         KEMBANGAN      KEMBANGAN SELATAN   1360        35-39     Perempuan
    ## 405             TEBET            TEBET TIMUR    890        35-39     Perempuan
    ## 406             TEBET            TEBET BARAT   1058        35-39     Perempuan
    ## 407             TEBET          MENTENG DALAM   1913        35-39     Perempuan
    ## 408             TEBET             KEBON BARU   1988        35-39     Perempuan
    ## 409             TEBET             BUKIT DURI   1801        35-39     Perempuan
    ## 410             TEBET      MANGGARAI SELATAN   1289        35-39     Perempuan
    ## 411             TEBET              MANGGARAI   1479        35-39     Perempuan
    ## 412        SETIA BUDI             SETIA BUDI    179        35-39     Perempuan
    ## 413        SETIA BUDI         KARET SEMANGGI    134        35-39     Perempuan
    ## 414        SETIA BUDI         KARET KUNINGAN    883        35-39     Perempuan
    ## 415        SETIA BUDI                  KARET    557        35-39     Perempuan
    ## 416        SETIA BUDI           MENTENG ATAS   1523        35-39     Perempuan
    ## 417        SETIA BUDI          PASAR MANGGIS   1437        35-39     Perempuan
    ## 418        SETIA BUDI                 GUNTUR    206        35-39     Perempuan
    ## 419        SETIA BUDI         KUNINGAN TIMUR    304        35-39     Perempuan
    ## 420  MAMPANG PRAPATAN       MAMPANG PRAPATAN    976        35-39     Perempuan
    ## 421  MAMPANG PRAPATAN                 BANGKA   1098        35-39     Perempuan
    ## 422  MAMPANG PRAPATAN           PELA MAMPANG   2321        35-39     Perempuan
    ## 423  MAMPANG PRAPATAN           TEGAL PARANG   1683        35-39     Perempuan
    ## 424  MAMPANG PRAPATAN         KUNINGAN BARAT    656        35-39     Perempuan
    ## 425      PASAR MINGGU           PASAR MINGGU   1288        35-39     Perempuan
    ## 426      PASAR MINGGU            JATI PADANG   1910        35-39     Perempuan
    ## 427      PASAR MINGGU         CILANDAK TIMUR   1389        35-39     Perempuan
    ## 428      PASAR MINGGU                RAGUNAN   2160        35-39     Perempuan
    ## 429      PASAR MINGGU          PEJATEN TIMUR   2919        35-39     Perempuan
    ## 430      PASAR MINGGU          PEJATEN BARAT   1894        35-39     Perempuan
    ## 431      PASAR MINGGU              KEBAGUSAN   2193        35-39     Perempuan
    ## 432    KEBAYORAN LAMA   KEBAYORAN LAMA UTARA   2396        35-39     Perempuan
    ## 433    KEBAYORAN LAMA          PONDOK PINANG   2765        35-39     Perempuan
    ## 434    KEBAYORAN LAMA                CIPULIR   2109        35-39     Perempuan
    ## 435    KEBAYORAN LAMA           GROGOL UTARA   2227        35-39     Perempuan
    ## 436    KEBAYORAN LAMA         GROGOL SELATAN   2266        35-39     Perempuan
    ## 437    KEBAYORAN LAMA KEBAYORAN LAMA SELATAN   2252        35-39     Perempuan
    ## 438          CILANDAK         CILANDAK BARAT   2678        35-39     Perempuan
    ## 439          CILANDAK            LEBAK BULUS   1852        35-39     Perempuan
    ## 440          CILANDAK            PONDOK LABU   2436        35-39     Perempuan
    ## 441          CILANDAK       GANDARIA SELATAN   1165        35-39     Perempuan
    ## 442          CILANDAK         CIPETE SELATAN   1331        35-39     Perempuan
    ## 443    KEBAYORAN BARU                MELAWAI    127        35-39     Perempuan
    ## 444    KEBAYORAN BARU                 GUNUNG    442        35-39     Perempuan
    ## 445    KEBAYORAN BARU            KRAMAT PELA    660        35-39     Perempuan
    ## 446    KEBAYORAN BARU                 SELONG    188        35-39     Perempuan
    ## 447    KEBAYORAN BARU             RAWA BARAT    272        35-39     Perempuan
    ## 448    KEBAYORAN BARU                SENAYAN    192        35-39     Perempuan
    ## 449    KEBAYORAN BARU                   PULO    295        35-39     Perempuan
    ## 450    KEBAYORAN BARU              PETOGOGAN    562        35-39     Perempuan
    ## 451    KEBAYORAN BARU         GANDARIA UTARA   2108        35-39     Perempuan
    ## 452    KEBAYORAN BARU           CIPETE UTARA   1758        35-39     Perempuan
    ## 453          PANCORAN               PANCORAN   1049        35-39     Perempuan
    ## 454          PANCORAN               KALIBATA   2242        35-39     Perempuan
    ## 455          PANCORAN              RAWA JATI    985        35-39     Perempuan
    ## 456          PANCORAN             DUREN TIGA   1460        35-39     Perempuan
    ## 457          PANCORAN             PENGADEGAN   1041        35-39     Perempuan
    ## 458          PANCORAN                 CIKOKO    595        35-39     Perempuan
    ## 459         JAGAKARSA              JAGAKARSA   2964        35-39     Perempuan
    ## 460         JAGAKARSA        SRENGSENG SAWAH   2874        35-39     Perempuan
    ## 461         JAGAKARSA               CIGANJUR   1817        35-39     Perempuan
    ## 462         JAGAKARSA          LENTENG AGUNG   2596        35-39     Perempuan
    ## 463         JAGAKARSA          TANJUNG BARAT   2022        35-39     Perempuan
    ## 464         JAGAKARSA                CIPEDAK   1774        35-39     Perempuan
    ## 465      PESANGGRAHAN           PESANGGRAHAN   1484        35-39     Perempuan
    ## 466      PESANGGRAHAN                BINTARO   2616        35-39     Perempuan
    ## 467      PESANGGRAHAN       PETUKANGAN UTARA   2791        35-39     Perempuan
    ## 468      PESANGGRAHAN     PETUKANGAN SELATAN   1727        35-39     Perempuan
    ## 469      PESANGGRAHAN                ULUJAMI   2186        35-39     Perempuan
    ## 470          MATRAMAN          PISANGAN BARU   1638        35-39     Perempuan
    ## 471          MATRAMAN        UTAN KAYU UTARA   1542        35-39     Perempuan
    ## 472          MATRAMAN             KAYU MANIS   1336        35-39     Perempuan
    ## 473          MATRAMAN             PAL MERIAM   1061        35-39     Perempuan
    ## 474          MATRAMAN          KEBON MANGGIS    873        35-39     Perempuan
    ## 475          MATRAMAN      UTAN KAYU SELATAN   1810        35-39     Perempuan
    ## 476       PULO GADUNG            PULO GADUNG   1836        35-39     Perempuan
    ## 477       PULO GADUNG         PISANGAN TIMUR   2200        35-39     Perempuan
    ## 478       PULO GADUNG               CIPINANG   2124        35-39     Perempuan
    ## 479       PULO GADUNG        JATINEGARA KAUM   1190        35-39     Perempuan
    ## 480       PULO GADUNG             RAWAMANGUN   2057        35-39     Perempuan
    ## 481       PULO GADUNG             KAYU PUTIH   2418        35-39     Perempuan
    ## 482       PULO GADUNG                   JATI   1797        35-39     Perempuan
    ## 483        JATINEGARA         KAMPUNG MELAYU   1154        35-39     Perempuan
    ## 484        JATINEGARA            BIDARA CINA   2064        35-39     Perempuan
    ## 485        JATINEGARA            BALI MESTER    466        35-39     Perempuan
    ## 486        JATINEGARA             RAWA BUNGA   1008        35-39     Perempuan
    ## 487        JATINEGARA      CIPINANG CEMPEDAK   1758        35-39     Perempuan
    ## 488        JATINEGARA         CIPINANG MUARA   2953        35-39     Perempuan
    ## 489        JATINEGARA CIPINANG BESAR SELATAN   1682        35-39     Perempuan
    ## 490        JATINEGARA   CIPINANG BESAR UTARA   2409        35-39     Perempuan
    ## 491       KRAMAT JATI            KRAMAT JATI   1799        35-39     Perempuan
    ## 492       KRAMAT JATI         KAMPUNG TENGAH   2135        35-39     Perempuan
    ## 493       KRAMAT JATI                  DUKUH   1210        35-39     Perempuan
    ## 494       KRAMAT JATI             BATU AMPAR   2417        35-39     Perempuan
    ## 495       KRAMAT JATI           BALE KAMBANG   1425        35-39     Perempuan
    ## 496       KRAMAT JATI              CILILITAN   2141        35-39     Perempuan
    ## 497       KRAMAT JATI                 CAWANG   1800        35-39     Perempuan
    ## 498        PASAR REBO                 GEDONG   1804        35-39     Perempuan
    ## 499        PASAR REBO                   BARU   1341        35-39     Perempuan
    ## 500        PASAR REBO              CIJANTUNG   1998        35-39     Perempuan
    ## 501        PASAR REBO               KALISARI   1951        35-39     Perempuan
    ## 502        PASAR REBO                PEKAYON   2060        35-39     Perempuan
    ## 503            CAKUNG             JATINEGARA   4775        35-39     Perempuan
    ## 504            CAKUNG            RAWA TERATE   1417        35-39     Perempuan
    ## 505            CAKUNG           PENGGILINGAN   4385        35-39     Perempuan
    ## 506            CAKUNG           CAKUNG TIMUR   2953        35-39     Perempuan
    ## 507            CAKUNG            PULO GEBANG   4030        35-39     Perempuan
    ## 508            CAKUNG          UJUNG MENTENG   1441        35-39     Perempuan
    ## 509            CAKUNG           CAKUNG BARAT   3275        35-39     Perempuan
    ## 510       DUREN SAWIT            DUREN SAWIT   3055        35-39     Perempuan
    ## 511       DUREN SAWIT           PONDOK BAMBU   3122        35-39     Perempuan
    ## 512       DUREN SAWIT                KLENDER   3569        35-39     Perempuan
    ## 513       DUREN SAWIT          PONDOK KELAPA   3356        35-39     Perempuan
    ## 514       DUREN SAWIT            MALAKA SARI   1703        35-39     Perempuan
    ## 515       DUREN SAWIT            MALAKA JAYA   1984        35-39     Perempuan
    ## 516       DUREN SAWIT            PONDOK KOPI   1604        35-39     Perempuan
    ## 517           MAKASAR                MAKASAR   1815        35-39     Perempuan
    ## 518           MAKASAR           PINANG RANTI   1284        35-39     Perempuan
    ## 519           MAKASAR             KEBON PALA   2502        35-39     Perempuan
    ## 520           MAKASAR  HALIM PERDANA KUSUMAH   1576        35-39     Perempuan
    ## 521           MAKASAR        CIPINANG MELAYU   2104        35-39     Perempuan
    ## 522           CIRACAS                CIRACAS   3085        35-39     Perempuan
    ## 523           CIRACAS                CIBUBUR   3175        35-39     Perempuan
    ## 524           CIRACAS       KELAPA DUA WETAN   2177        35-39     Perempuan
    ## 525           CIRACAS                SUSUKAN   1846        35-39     Perempuan
    ## 526           CIRACAS               RAMBUTAN   1849        35-39     Perempuan
    ## 527          CIPAYUNG               CIPAYUNG   1172        35-39     Perempuan
    ## 528          CIPAYUNG              CILANGKAP   1276        35-39     Perempuan
    ## 529          CIPAYUNG         PONDOK RANGGON   1064        35-39     Perempuan
    ## 530          CIPAYUNG                 MUNJUL   1112        35-39     Perempuan
    ## 531          CIPAYUNG                   SETU    928        35-39     Perempuan
    ## 532          CIPAYUNG             BAMBU APUS   1187        35-39     Perempuan
    ## 533          CIPAYUNG           LUBANG BUAYA   2988        35-39     Perempuan
    ## 534          CIPAYUNG                  CEGER    930        35-39     Perempuan
