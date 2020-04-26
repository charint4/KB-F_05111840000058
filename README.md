# KB-F_05111840000058

# 8 Puzzle BFS (Breadth First Search)
BFS (Breadth First Search) adalah strategi sederhana di mana simpul akar diperluas terlebih dahulu, kemudian semua penerus simpul akar diperluas selanjutnya, kemudian penerusnya dan seterusnya sampai jalan terbaik yang mungkin telah ditemukan. Karena kenyataan bahwa strategi untuk grafik traversal ini tidak memiliki informasi tambahan tentang status di luar yang disediakan dalam definisi masalah, Breadth First Search digolongkan sebagai pencarian yang kurang informasi atau blind.

Breadth First Search Menggunakan struktur data queue sebagai lawan dari stack yang digunakan Depth First Search.

BFS menggunakan struktur data antrian yang merupakan struktur data First In, First Out atau FIFO. Antrian ini menyimpan semua node yang harus kita jelajahi dan setiap kali sebuah node dieksplorasi ditambahkan ke set node yang dikunjungi.

Jika dilakukan pencarian luas pertama di pohon biner di atas maka itu akan melakukan hal berikut:

Tetapkan Node 1 sebagai Node awal
Tambahkan Node ini ke queue
Tambahkan Node ini ke set yang dikunjungi
Jika node ini adalah node tujuan kami, maka kembalikan benar, kalau tidak tambahkan Node 2 dan Node 3 ke queue
Periksa Node 2 dan jika itu tidak menambahkan Node 4 dan Node 5 ke queue
Ambil node berikutnya dari queue yang seharusnya Node 3 dan periksa
Jika Node 3 bukan node tujuan kami tambahkan Node 6 dan Node 7 ke queue
Ulangi sampai Node sasaran ditemukan.
Jika dilakukan penghentian eksekusi setelah Node 3 diperiksa, maka queue akan terlihat Node 4, Node 5, Node 7, Node 8.

Seperti yang pada gambardibawah ini, jika mengikuti algoritma ini maka akan secara rekursif mencari setiap tingkat pohon biner menjadi lebih dalam dan lebih dalam sampai Anda menemukan jalan terpendek yang mungkin.

# 8 Puzzle - DFS (Depth First Search)
Algoritma DFS `Depth First Search` adalah algoritma rekursif yang menggunakan gagasan backtracking. Ini melibatkan pencarian lengkap dari semua node dengan melanjutkan, jika mungkin, dengan mundur.

Depth First Search Menggunakan struktur data `stack` sebagai lawan dari queue yang digunakan Breadth First Search.

Di sini, kata mundur berarti bahwa ketika pencarian bergerak maju dan tidak ada lagi node di sepanjang jalur saat ini, pencarian bergerak mundur di jalur yang sama untuk menemukan node untuk dilintasi. Semua node akan dikunjungi di jalur saat ini sampai semua node yang belum dikunjungi telah dilalui setelah jalur berikutnya akan dipilih.

Sifat rekursif DFS ini dapat diimplementasikan menggunakan tumpukan. Ide dasarnya adalah sebagai berikut:
- Pilih simpul awal dan dorong semua simpul yang berdekatan ke tumpukan.
- Pop sebuah node dari stack untuk memilih node berikutnya untuk mengunjungi dan mendorong semua node yang berdekatan ke dalam stack.
- Ulangi proses ini sampai tumpukan kosong. Namun, pastikan bahwa node yang dikunjungi ditandai. Ini akan mencegah Anda mengunjungi simpul yang sama lebih dari sekali. Jika Anda tidak menandai node yang dikunjungi dan Anda mengunjungi node yang sama lebih dari sekali, Anda mungkin berakhir dalam loop tak terbatas.



# 8 Puzzle - IDS (Iterative Deepening Search)

`Iterative Deepening Search` (IDS) merupakan sebuah strategi umum yang biasanya dikombinasikan dengan Depth First tree search, yang akan menemukan berapa depth limit terbaik untuk digunakan. Hal ini dilakukan dengan secara menambah limit secara bertahap, mulai dari 0,1, 2, dan seterusnya sampai goal sudah ditemukan.


Iterative Deepening DFS dengan kata-kata sederhana menjalankan DFS dengan secara bertahap meningkatkan batas kedalaman - 0, kemudian mengulangi DFS dari awal dengan batas kedalaman 1, kemudian mengulangi DFS dari awal dengan tingkat kedalaman 2, dan seterusnya, hingga solusi ditemukan . Jadi bagaimana ini menggabungkan manfaat DFS dan BFS?

Ini memiliki persyaratan memori sederhana seperti DFS yaitu O (bm)

Sejak menjalankan DFS (meskipun dengan meningkatkan level kedalaman dengan setiap iterasi), persyaratan memorinya akan sama dengan DFS.

Ini optimal asalkan biaya jalur adalah fungsi nececreasing dari kedalaman node, seperti BFS. Karena Anda mengulangi strategi DFS dengan meningkatkan batas kedalaman dengan setiap iterasi, Anda dapat yakin bahwa Anda melintasi saudara kandung leluhur Anda dalam iterasi sebelumnya yang pada gilirannya menjamin bahwa tidak ada keadaan solusi yang ada pada level yang lebih dangkal.

Lengkap seperti BFS asalkan faktor percabangannya terbatas. Karena itu melintasi lebar juga - karena Anda mengulangi DFS dengan tingkat kedalaman yang meningkat - itu tidak bisa terjebak pada jalur yang tak terbatas.

# 4 Queen CSP
Dalam program dibawah ini, merupakan fungsi untuk mengecek tempat yang akan ditempati oleh queen. Apakah tempatnya aman atau tidak.
```
bool isSafe(int board[N][N], int row, int col) 
{ 
    int i, j; 
  
    for (i = 0; i < col; i++) 
        if (board[row][i]) 
            return false; 

    for (i=row, j=col; i>=0 && j>=0; i--, j--) 
        if (board[i][j]) 
            return false; 

    for (i=row, j=col; j>=0 && i<N; i++, j--) 
        if (board[i][j]) 
            return false; 
  
    return true; 
} 
```
![4qcsp](https://user-images.githubusercontent.com/52326074/77139569-14d8ef00-6aa9-11ea-88c5-8cb7a395e267.png)

Tidak ada dua ratu di baris, kolom, atau diagonal yang sama.

Perhatikan bahwa ini bukan masalah optimisasi, melaikan ingin menemukan semua solusi yang mungkin, bukan satu solusi optimal, yang menjadikannya kandidat alami untuk pemrograman kendala. Bagian berikut menjelaskan pendekatan Constraint Programming untuk masalah N-queens

CP (Constraint Programming) bekerja dengan secara sistematis mencoba semua kemungkinan penugasan nilai untuk variabel dalam masalah, untuk menemukan solusi yang layak. Dalam masalah 4-queens, pemecah dimulai pada kolom paling kiri dan berturut-turut menempatkan satu ratu di setiap kolom, di lokasi yang tidak diserang oleh ratu yang sebelumnya ditempatkan.

## Propagation and backtracking

Ada dua elemen kunci untuk pencarian pemrograman kendala:
- `Propagation` - Setiap kali pemecah memberikan nilai ke variabel, kendala menambahkan batasan pada nilai yang mungkin dari variabel yang tidak ditetapkan. Pembatasan ini menyebar ke penugasan variabel masa depan. Misalnya, dalam masalah 4-queens, setiap kali pemecah menempatkan ratu, ia tidak dapat menempatkan ratu lain di baris dan diagonal ratu saat ini aktif. Propagasi dapat mempercepat pencarian secara signifikan dengan mengurangi sekumpulan nilai variabel yang harus dieksplorasi oleh pemecah.
- `Backtracking occurs` - ketika solver tidak dapat memberikan nilai ke variabel berikutnya, karena kendala, atau ia menemukan solusi. Dalam kedua kasus tersebut, pemecah melakukan backtracks ke tahap sebelumnya dan mengubah nilai variabel pada tahap itu ke nilai yang belum pernah dicoba. Dalam contoh 4-queens, ini berarti memindahkan ratu ke kotak baru pada kolom saat ini.

Dengan hipotesis ini, kendala apa yang bisa kita sebarkan? Satu kendala adalah bahwa hanya ada satu ratu dalam kolom (X abu-abu di bawah), dan kendala lain melarang dua ratu pada diagonal yang sama (X merah di bawah).

![4qcsp1](https://user-images.githubusercontent.com/52326074/77139791-f7f0eb80-6aa9-11ea-8474-4ea76873034e.png)

Kendala ketiga dilarang ratu di baris yang sama:

![4qcsp2](https://user-images.githubusercontent.com/52326074/77139793-f9221880-6aa9-11ea-8247-01dbe0430e0d.png)

Kendala diperbanyak, dapat diuji hipotesis lain, dan menempatkan ratu kedua di salah satu kotak yang tersisa. Pemecahannya mungkin memutuskan untuk menempatkan di dalamnya kotak pertama yang tersedia di kolom kedua:

![4qcsp3](https://user-images.githubusercontent.com/52326074/77139794-f9221880-6aa9-11ea-90f0-64b47585851f.png)

Setelah menyebarkan batasan diagonal, dapat dilihat bahwa itu tidak meninggalkan kotak yang tersedia di kolom ketiga atau baris terakhir:

![4qcsp4](https://user-images.githubusercontent.com/52326074/77139795-f9baaf00-6aa9-11ea-828f-f4a2cde6f04b.png)

Tanpa solusi yang memungkinkan pada tahap ini, maka perlu mundur. Salah satu opsi adalah bagi pemecah untuk memilih kuadrat lain yang tersedia di kolom kedua. Namun, propagasi kendala kemudian memaksa ratu ke baris kedua kolom ketiga, tidak meninggalkan tempat yang valid untuk ratu keempat:

![4qcsp5](https://user-images.githubusercontent.com/52326074/77139797-fa534580-6aa9-11ea-9503-e91583625389.png)

Jadi pemecah harus mundur lagi, kali ini semua jalan kembali ke penempatan ratu pertama. Sekarang telah menunjukkan bahwa tidak ada solusi untuk masalah ratu yang akan menempati kotak sudut.

Karena tidak ada ratu di sudut, pemecah memindahkan ratu pertama satu per satu, dan menyebar, hanya menyisakan satu tempat untuk ratu kedua :

![4qcsp6](https://user-images.githubusercontent.com/52326074/77139798-fa534580-6aa9-11ea-89c3-497d77960785.png)

Menyebarkan lagi mengungkapkan hanya satu tempat tersisa untuk ratu ketiga:

![4qcsp7](https://user-images.githubusercontent.com/52326074/77139799-faebdc00-6aa9-11ea-9420-03e82c5afa31.png)

Dan untuk ratu keempat dan terakhir:

![4qcsp8](https://user-images.githubusercontent.com/52326074/77139801-fb847280-6aa9-11ea-9919-ccff9a4bce2e.png)

Dapat dilihat bahwa sudah ditemukan solusi pertama! Jika ingin menginstruksikan pemecahnya untuk berhenti setelah menemukan solusi pertama, itu akan berakhir di sini. Kalau tidak, itu akan mundur lagi dan menempatkan ratu pertama di baris ketiga kolom pertama.

# 8 Queen Hill Climbing
Hill Climbing adalah pencarian heuristik yang digunakan untuk masalah optimasi matematis di bidang Inteligensi Buatan.

Dengan sejumlah besar input dan fungsi heuristik yang baik, ia mencoba untuk menemukan solusi yang cukup baik untuk masalah tersebut. Solusi ini mungkin bukan global optimal maksimum.
- Dalam definisi di atas, `Mathematical Optimization Problems` menyiratkan bahwa mendaki bukit memecahkan masalah di mana kita perlu memaksimalkan atau meminimalkan fungsi nyata yang diberikan dengan memilih nilai dari input yang diberikan. Contoh-Traveling salesman masalah di mana kita perlu meminimalkan jarak yang ditempuh oleh salesman.
- `Heuristic Search` berarti bahwa algoritma pencarian ini mungkin tidak menemukan solusi optimal untuk masalah tersebut. Namun, itu akan memberikan solusi yang baik dalam waktu yang wajar.
- `Heuristic Function` adalah fungsi yang akan memberi peringkat semua alternatif yang mungkin pada setiap langkah percabangan dalam algoritma pencarian berdasarkan informasi yang tersedia. Ini membantu algoritma untuk memilih rute terbaik dari rute yang mungkin.

![hc](https://user-images.githubusercontent.com/52326074/77150635-e36f1c00-6ac6-11ea-977e-153dd3b862e3.png)

## Fitur Hill Climbing
### a. Varian dari menghasilkan dan menguji algoritma

Ini adalah varian dari algoritma generate and test. Algoritma generate and test adalah sebagai berikut:
- Hasilkan solusi yang mungkin.
- Tes untuk melihat apakah ini solusi yang diharapkan.
- Jika solusinya telah ditemukan, keluar lagi, lanjutkan ke langkah 1.

Oleh karena itu kami menyebut Hill climbing sebagai varian dari algoritma hasil dan uji karena mengambil umpan balik dari prosedur pengujian. Kemudian umpan balik ini digunakan oleh generator dalam memutuskan langkah selanjutnya dalam ruang pencarian.

### b. Menggunakan Greedy Aproach

Pada titik mana pun di ruang keadaan, pencarian bergerak ke arah itu saja yang mengoptimalkan biaya fungsi dengan harapan menemukan solusi optimal di akhir.

## Jenis Hill Climbing
### a. Simple Hill Climbing

Ini memeriksa node tetangga satu per satu dan memilih node tetangga pertama yang mengoptimalkan biaya saat ini sebagai node berikutnya. Ini memeriksa node tetangga satu per satu dan memilih node tetangga pertama yang mengoptimalkan biaya saat ini sebagai node berikutnya.

Algoritma Simple Hill climbing :
- Evaluasi keadaan awal. Jika itu adalah keadaan tujuan maka berhentilah dan kembalikan kesuksesan. Kalau tidak, jadikan kondisi awal sebagai kondisi saat ini.
- Loop sampai keadaan solusi ditemukan atau tidak ada operator baru yang dapat diterapkan ke keadaan saat ini.
- Exit

### b. Steepest-Ascent Hill Climbing

Pertama-tama memeriksa semua node tetangga dan kemudian memilih simpul yang paling dekat dengan keadaan solusi pada simpul berikutnya.

- Evaluasi keadaan awal. Jika status tujuan maka keluar dari yang lain jadikan status saat ini sebagai keadaan awal
- Ulangi langkah ini sampai solusi ditemukan atau keadaan saat ini tidak berubah
- Exit

### c. Stochastic Hill Climbing

Itu tidak memeriksa semua node tetangga sebelum memutuskan node mana yang akan dipilih. Itu hanya memilih node tetangga secara acak dan memutuskan (berdasarkan jumlah peningkatan tetangga itu) apakah akan pindah ke tetangga itu atau untuk memeriksa yang lain.

## State Space Diagram untuk Hill Climbing

adalah representasi grafis dari himpunan status yang dapat dicapai oleh algoritma pencarian kami vs nilai fungsi objektif kami (fungsi yang ingin kami maksimalkan).

`X - axis` menunjukkan ruang keadaan yaitu keadaan atau konfigurasi yang dapat dicapai algoritma kami.

`Y - axis` menunjukkan nilai-nilai fungsi obyektif yang sesuai dengan keadaan tertentu.

Solusi terbaik adalah ruang negara di mana fungsi objektif memiliki nilai maksimum (global maksimum).

![8phc](https://user-images.githubusercontent.com/52326074/77142942-355a7680-6ab4-11ea-8c1d-66b86aaef6c9.png)

## Daerah berbeda di State Space Diagram

- `Local Maximum` Ini adalah state yang lebih baik daripada state tetangganya namun ada state yang lebih baik daripada itu (global maksimum). Keadaan ini lebih baik karena di sini nilai fungsi objektif lebih tinggi daripada tetangganya.
- `Global Maximum` Ini adalah keadaan terbaik yang mungkin dalam diagram ruang keadaan. Ini karena pada keadaan ini, fungsi objektif memiliki nilai tertinggi.
- `Plateua/Flat Local Maximum` Ini adalah wilayah datar ruang negara di mana negara-negara tetangga memiliki nilai yang sama.
- `Ridge` Ini adalah wilayah yang lebih tinggi dari tetangganya tetapi memiliki kemiringan. Ini adalah jenis khusus maksimum lokal.
- `Current State` Wilayah diagram ruang keadaan tempat kami saat ini hadir selama pencarian.
- `Shoulder` Ini adalah dataran tinggi yang memiliki tepi menanjak.

# 8 Puzzle Heuristic 
Dalam program ini diminta untuk menyelesaikan 8 puzzle menggunakan metode heuristic 1 dan 2. Dimana penjelasan heuristic 1 dan 2 ada dibawah. Jika menggunakan heuristic 1 maka yang dilihat yaitu banyaknya grid yang menempati tempat yg salah, tetapi jika menggunakan heuristic 2 maka yang dilihat yaitu total keseluruhan jarak tiap grid yang menempati tempat yang salah terhadap posisi grid yang benar, atau sering disebut dengan manhattan distance.

Jadi dalam penyelesainnya kita mengeluarkan hasil setiap langkah puzzle dengan melihat penempatan grid yang salah kemudian dicari penempatan grid yang benar untuk mencapai final state yang diinginkan.

Pada pembahasan kali ini, saya ingin menyelesaikan puzzle ini dengan suatu algoritma, yaitu Algoritma Greedy, dengan menggunakan dua fungsi heuristik. Algoritma Greedy merupakan algoritma yang sederhana dan lempeng (straightforward). Secara harfiah greedy artinya rakus atau tamak.

Algoritma Greedy membentuk solusi langkah per langkah. Terdapat banyak pilihan yang perlu dieksplorasi pada setiap langkah solusi. Oleh karena itu, pada setiap langkah harus dibuat keputusan yang terbaik dalam menentukan pilihan. 

Dalam bahasan ini, fungsi heuristik yang akan kita tampilkan yaitu adalah sebagai berikut.
- h₁(n) : sebagai banyak grid yang menempati tempat yang salah.
- h₂(n) : sebagai total keseluruhan jarak tiap grid yang menempati tempat yang salah terhadap posisi grid yang benar, atau sering disebut dengan manhattan distance.

Solusi Penyelesaian dengan fungsi Heuristik Pertama yaitu banyak grid yang menempati tempat yang salah

![8puzzle-heuristic1.1](https://user-images.githubusercontent.com/52326074/77029102-58f6c180-69cd-11ea-9571-7a69fe89de7d.PNG)
![8puzzle-heuristic1.2](https://user-images.githubusercontent.com/52326074/77029100-585e2b00-69cd-11ea-8d32-03512709f26c.PNG)
![8puzzle-heuristic1.3](https://user-images.githubusercontent.com/52326074/77029097-572cfe00-69cd-11ea-845e-7e8b50514214.PNG)

Solusi :
Initial State -> Right -> Up -> Right -> Down -> Down -> Left -> Up -> Right -> Down(Goal)

Solusi Penyelesai dengan fungsi Heuristik Kedua yaitu total keseluruhan jarak tiap grid yang menempati tempat yang salah terhadap posisi grid yang benar, atau sering disebut dengan manhattan distance.

![8puzzle-heuristic2.1](https://user-images.githubusercontent.com/52326074/77029181-8f344100-69cd-11ea-9799-24cda528fdd5.PNG)
![8puzzle-heuristic2.2](https://user-images.githubusercontent.com/52326074/77029178-8e9baa80-69cd-11ea-9d35-2282c1916e48.PNG)
![8puzzle-heuristic2.3](https://user-images.githubusercontent.com/52326074/77029175-8d6a7d80-69cd-11ea-8775-2fd302b4ad62.PNG)

Solusi :
Initial State -> Right -> Up -> Right -> Down -> Down -> Left -> Up -> Right -> Up(Goal)


Kesimpulannya, dari semua yang telah dipaparkan diatas, penggunaan dari dua fungsi heuristik Algoritma Greedy pada solusi penyelesaian 8-puzzle, baik fungsi heuristik pertama dan kedua sama sama mampu memberikan solusi penyelesaian dari awal state sampai ke goal state. Tetapi menurut pendapat saya, pada penggunaan fungsi heuristik pertama jumlah State puzzle yang memiliki fungsi heuristik yang sama lebih banyak dari pada penggunaan fungsi heuristik kedua. Jadi, penggunaan solusi dari fungsi heuristik kedua dalam contoh penyelesaian 8-puzzle diatas lebih optimal dari pada fungsi heuristik pertama.
