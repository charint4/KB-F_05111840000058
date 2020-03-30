# KB-F_05111840000058

#8 Puzzle BFS
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

