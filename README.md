# KB-F_05111840000058

# 8 Puzzle BFS
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

![bfs](https://user-images.githubusercontent.com/52326074/77224197-c1909a80-6b95-11ea-92fa-ccdca09a36ac.png)

# 8 Puzzle - DFS (Depth First Search)
Algoritma DFS `Depth First Search` adalah algoritma rekursif yang menggunakan gagasan backtracking. Ini melibatkan pencarian lengkap dari semua node dengan melanjutkan, jika mungkin, dengan mundur.

Depth First Search Menggunakan struktur data `stack` sebagai lawan dari queue yang digunakan Breadth First Search.

Di sini, kata mundur berarti bahwa ketika pencarian bergerak maju dan tidak ada lagi node di sepanjang jalur saat ini, pencarian bergerak mundur di jalur yang sama untuk menemukan node untuk dilintasi. Semua node akan dikunjungi di jalur saat ini sampai semua node yang belum dikunjungi telah dilalui setelah jalur berikutnya akan dipilih.

Sifat rekursif DFS ini dapat diimplementasikan menggunakan tumpukan. Ide dasarnya adalah sebagai berikut:
- Pilih simpul awal dan dorong semua simpul yang berdekatan ke tumpukan.
- Pop sebuah node dari stack untuk memilih node berikutnya untuk mengunjungi dan mendorong semua node yang berdekatan ke dalam stack.
- Ulangi proses ini sampai tumpukan kosong. Namun, pastikan bahwa node yang dikunjungi ditandai. Ini akan mencegah Anda mengunjungi simpul yang sama lebih dari sekali. Jika Anda tidak menandai node yang dikunjungi dan Anda mengunjungi node yang sama lebih dari sekali, Anda mungkin berakhir dalam loop tak terbatas.

![dfs](https://user-images.githubusercontent.com/52326074/77224296-cace3700-6b96-11ea-9dc1-810524ec907a.jpg)

# 8 Puzzle - IDS (Iterative Deepening Search)

`Iterative Deepening Search` (IDS) merupakan sebuah strategi umum yang biasanya dikombinasikan dengan Depth First tree search, yang akan menemukan berapa depth limit terbaik untuk digunakan. Hal ini dilakukan dengan secara menambah limit secara bertahap, mulai dari 0,1, 2, dan seterusnya sampai goal sudah ditemukan.

![ids](https://user-images.githubusercontent.com/52326074/77226305-dd05a080-6ba9-11ea-8a8e-4216c8be6935.png)

Iterative Deepening DFS dengan kata-kata sederhana menjalankan DFS dengan secara bertahap meningkatkan batas kedalaman - 0, kemudian mengulangi DFS dari awal dengan batas kedalaman 1, kemudian mengulangi DFS dari awal dengan tingkat kedalaman 2, dan seterusnya, hingga solusi ditemukan . Jadi bagaimana ini menggabungkan manfaat DFS dan BFS?

Ini memiliki persyaratan memori sederhana seperti DFS yaitu O (bm)

Sejak menjalankan DFS (meskipun dengan meningkatkan level kedalaman dengan setiap iterasi), persyaratan memorinya akan sama dengan DFS.

Ini optimal asalkan biaya jalur adalah fungsi nececreasing dari kedalaman node, seperti BFS. Karena Anda mengulangi strategi DFS dengan meningkatkan batas kedalaman dengan setiap iterasi, Anda dapat yakin bahwa Anda melintasi saudara kandung leluhur Anda dalam iterasi sebelumnya yang pada gilirannya menjamin bahwa tidak ada keadaan solusi yang ada pada level yang lebih dangkal.

Lengkap seperti BFS asalkan faktor percabangannya terbatas. Karena itu melintasi lebar juga - karena Anda mengulangi DFS dengan tingkat kedalaman yang meningkat - itu tidak bisa terjebak pada jalur yang tak terbatas.
