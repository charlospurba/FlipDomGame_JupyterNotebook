![image](https://github.com/user-attachments/assets/46a459f0-409f-4dc8-943e-82515022d032)**Deskripsi Game**
Permainan Flip Dom adalah permainan yang menantang kemampuan strategi pemain serta memberikan kesempatan untuk menerapkan algoritma kecerdasan buatan. Dalam permainan ini, pemain harus membuat langkah optimal untuk membalik dan mengatur domino dalam urutan yang tepat di papan permainan. 
Program ini telah dikembangkan dengan tujuan menghadirkan permainan Flip Dom yang dapat dipecahkan oleh komputer menggunakan Minimax Function dengan pemangkasan alfa-beta. Algoritma ini bekerja secara rekursif untuk mengevaluasi status permainan di masa depan, mempertimbangkan berbagai kemungkinan gerakan yang dapat diambil oleh lawan maupun pemain. Pemangkasan alfa-beta digunakan untuk mengoptimalkan proses dengan menghilangkan langkah-langkah yang tidak perlu dievaluasi, sehingga mengurangi waktu komputasi dan mempercepat pencarian solusi terbaik.
Tujuan utama dari aplikasi ini adalah memberikan pengalaman bermain yang seru dan edukatif, serta menunjukkan kekuatan kecerdasan buatan dalam mengambil keputusan strategis. Aplikasi Flip Dom mengikuti aturan klasik permainan berbasis domino, di mana setiap langkah yang diambil harus dipertimbangkan dengan cermat untuk memenangkan permainan melawan AI yang menggunakan algoritma optimal.

**Aturan Permainan**
1.	Permainan dimainkan di papan berukuran 8x8.
2.	 Pemain secara bergiliran menempatkan pion di papan.
3.	Sebuah gerakan valid adalah gerakan yang dapat membalik pion lawan di satu atau lebih arah (horizontal, vertikal, atau diagonal).
4.	Permainan berakhir ketika tidak ada lagi gerakan valid yang tersisa untuk kedua pemain.
5.	Pemain dengan jumlah pion terbanyak di akhir permainan dinyatakan sebagai pemenang


**Fitur Utama yang Terdapat dalam Aplikasi FlipDom**
1.	Fungsi Membuat Papan Permainan (init_game)
Inisialisasi papan 8x8 dengan empat pion awal (dua putih dan dua hitam) di tengah papan, sesuai aturan Othello/Reversi. 
2.	Fungsi Mencetak Papan (print_board)
Menampilkan papan permainan ke konsol dengan pion putih (W), hitam (B), dan ruang kosong (.), termasuk label koordinat untuk memudahkan pemain.
3.	Fungsi Validasi Gerakan (is_valid_move)
Memeriksa validitas langkah pemain sesuai aturan FlipDom, memastikan gerakan dapat membalik pion lawan di setidaknya satu arah. 
4.	Fungsi Mendapatkan Gerakan Valid (get_valid_moves)
Menghasilkan daftar semua langkah valid yang tersedia bagi pemain saat ini. 
5.	Fungsi Melakukan Gerakan dan Membalik Pion (make_move)
Mengeksekusi langkah pemain, membalik pion lawan yang terperangkap, dan mengubah giliran pemain. 
6.	Fungsi Memeriksa Akhir Permainan (is_game_over)
Mendeteksi apakah permainan telah berakhir ketika tidak ada lagi gerakan valid untuk kedua pemain.
7.	Fungsi Menghitung Jumlah Pion (count_pieces)
Menghitung jumlah pion putih dan hitam di papan. 
8.	Fungsi Evaluasi Papan (evaluate_board)
Mengevaluasi posisi papan saat ini berdasarkan jumlah pion hitam dikurangi jumlah pion putih. 
9.	Fungsi Pembatalan Gerakan (undo_move)
Memungkinkan pembatalan langkah terakhir, berguna dalam implementasi algoritma Minimax. 
10.	Fungsi Pencarian Minimax dengan Alpha-Beta Pruning (minimax)
Implementasi algoritma Minimax dengan optimasi Alpha-Beta Pruning untuk menentukan langkah terbaik bagi AI. 
11.	Fungsi Menyimpan dan Memuat Permainan (save_game, load_game)
Memungkinkan penyimpanan dan pemuatan status permainan menggunakan format JSON. 
12.	Fungsi Menampilkan Aturan (show_rules)
Menampilkan aturan dasar permainan FlipDom kepada pemain. 
13.	Fungsi Utama Permainan (play)
Mengatur alur utama permainan, termasuk interaksi dengan pemain, giliran AI, dan penanganan akhir permainan.

**METODE**

**1. Algoritma Minimax**
Algoritma minimax dapat dijelaskan dengan menggunakan dua fungsi dasar yaitu satu untuk pemain yang ingin memaksimalkan skornya (pemain maximizer) dan satu untuk pemain yang ingin meminimalkan skor lawan (pemain minimizer).

Fungsi Minimax
![image](https://github.com/user-attachments/assets/954415ed-4281-45bc-95fa-90d6c8f9ddea)
-	N		: Node saat ini (keadaan permainan).
-	depth		: Kedalaman pencarian yang tersisa.
-	Evaluate(N)	: Fungsi evaluasi yang memberikan nilai pada node terminal.
-	Actions(N)	: Daftar langkah-langkah valid yang dapat diambil dari node N.
-	Result(N, a)	: Keadaan baru setelah langkah a diambil dari node N.
Metode minimax dalam kelas FlipDom menerapkan algoritma ini secara rekursif:
•	Pemain Memaksimalkan (AI): 
Algoritma berusaha memaksimalkan skor AI (jumlah bidak hitam). Algoritma ini mengeksplorasi semua langkah valid dan menghitung kemungkinan hasil.
•	Pemain Meminimalkan (Manusia)
Algoritma mengasumsikan bahwa pemain manusia akan bermain secara optimal untuk meminimalkan skor AI.
Setiap panggilan rekursif mengevaluasi langkah-langkah potensial dengan:
•	Melakukan langkah dengan make_move.
•	Memanggil minimax secara rekursif untuk mengevaluasi hasil bagi pemain berikutnya.
•	Mengembalikan langkah tersebut dengan undo_move untuk mengembalikan papan ke keadaan sebelumnya.

Pada penggunaannya dalam permainan berbabis giliran/turn based salah satu pemain menggunakan MAX dan pemain lawannya menggunakan MIN. Pemain MAX akan memilih nilai yang paling maksimum, sedangkan pemain MIN akan memilih nilai yang paling minimum. Asumsi dari algoritma ini adalah MAX dan MIN akan memilih langkah yang optimal. Pengambilan keputusan akan berdasarkan terhadap MIN dan MAX tiap simpulnya. . Simpul-simpul pada pohon ruang mempunyai kedalamannya (depth) masing-masing yang diawali dari depth 0. Simpul A akan mencari nilai maksimum berdasarkan value dari simpul B dan C, sedangkan simpul B akan mencari nilai minimum berdasarkan value dari D dan E dan juga simpul C akan mencari nilai minimum dari simpul F dan G. Pola penulusan ini akan dilakukan sampai mencapai simpul daun yang mempunyai sebuah nilai. Pada akhirnya algoritma ini akan memberikan nilai dari evaluasi simpul pada akar yang merupakan value terbaik. Pada kedalaman 2 simpul D akan menghasilkan nilai max(-1, 4) → 4, simpul E akan menghasilkan nilai max(2, 6) → 6, simpul F akan menghasilkan nilai max(-3, -5) → -3, dan simpul G akan menghasilkan nilai max (0, 7) → 7. Proses tersebut akan dilakukan juga pada kedalaman yang lebih tinggi hingga dicapai akarnya dan pada akhirnya akan mendapat kan hasil 4.
 ![image](https://github.com/user-attachments/assets/e5d4fa14-cc6c-4701-8a76-e57257128636)
Nilai dari node terminal (nilai di bagian paling bawah) “naik” ke level yang lebih tinggi dalam pohon. Untuk node D, Maximizer memilih nilai terbaik dari -1, 4, dan 2, yaitu 4. Ini kemudian menjadi nilai untuk node D. Untuk node B, Minimizer memilih nilai terendah dari 4 (dari D) dan 6 (dari E), yaitu 4. Begitu juga untuk node C, Minimizer memilih nilai terendah antara -3 (dari F) dan 7 (dari G), yaitu -3. Pada akhirnya, Maximizer di node A akan memilih langkah terbaik antara nilai 4 (dari B) dan -3 (dari C). Karena A adalah Maximizer, ia akan memilih 4 sebagai langkah terbaiknya.
Algoritma ini membantu pemain menentukan langkah optimal dengan mempertimbangkan semua kemungkinan langkah dari kedua belah pihak. Di setiap level permainan, ada dua peran utama: Maximizer dan Minimizer. Maximizer berusaha memaksimalkan keuntungan, sedangkan Minimizer bertujuan meminimalkan nilai Maximizer. Gambar ini menunjukkan sebuah pohon keputusan di mana bagian paling bawah (node-terminal) menggambarkan nilai atau skor akhir dari setiap langkah yang mungkin. Proses Minimax bekerja dengan menghitung nilai terbaik di setiap node. Pada tingkat terendah, Maximizer memilih langkah dengan nilai tertinggi dari opsi yang tersedia, seperti pada node D yang memilih nilai 4 dari opsi di bawahnya (-1, 4, dan 2). Kemudian, Minimizer memilih nilai terendah dari pilihan yang diberikan Maximizer, seperti node B yang memilih 4 dari nilai yang tersedia. Proses ini terus berlanjut ke atas pohon hingga akhirnya Maximizer di puncak (node A) memilih langkah terbaik berdasarkan nilai yang dihasilkan, yaitu 4 dari cabang B.
Dalam permainan Othello, algoritma ini memodelkan langkah-langkah yang mungkin diambil pemain dan lawan, dan membantu Maximizer memilih langkah terbaik dengan memprediksi kemungkinan respon Minimizer. Proses ini berjalan secara rekursif hingga menemukan langkah optimal yang meminimalkan risiko dari tindakan lawan, menjadikannya alat yang efektif dalam membuat keputusan strategis di setiap giliran permainan. Pada implementasinya, algoritma minimax memerlukan waktu yang cukup lama dalam penelusuran langkahnya dikarenakan pencarian dilakukan terhadap seluruh simpul yang dibangkitkan, sehingga diperlukannya optimasi untuk memangkas simpul yang sudah dianggap tidak menuju ke solusi dengan menggunakan optimasi alpha-beta pruning

**2	Algoritma Alpha-Beta Pruning**

Pada permainan FlipDom, node-node pada pohon penelusuran merupakan kondisi-kondisi papan yang mungkin terjadi saat permainan berlangsung. Node-node anak merupakan mobility-mobility dari node induknya. Node yang berada di paling bawah, dievaluasi dengan fungsi evaluasi untuk diperoleh nilainya.
Pemangkasan alpha-beta mengoptimalkan algoritma minimax dengan memotong cabang yang tidak perlu.

Fungsi Minimax dengan Alpha-Beta
 
![image](https://github.com/user-attachments/assets/2571b16e-6979-48b3-a283-7c0091fef0ae)

-	α (alpha): Nilai terbaik yang dijamin untuk pemain maximizer.
-	β (beta): Nilai terbaik yang dijamin untuk pemain minimizer.
Setiap kali nilai dikembalikan ke node orang tua, nilai α dan β diperbarui:
•	Untuk pemain maximizer:
 ![image](https://github.com/user-attachments/assets/4780c6f5-c8f7-448c-bf53-6817f5d7c552)

•	Untuk pemain minimizer:
 ![image](https://github.com/user-attachments/assets/e3ebf2c9-e41d-4694-b1f0-b4ad82325eab)

Jika nilai β kurang dari atau sama dengan α, pencarian dapat dihentikan untuk cabang ini (pemangkasan).
Pruning yang dilakukan dalam game FlipDom dibuat dengan dua parameter yaitu: 
•	Alpha (α): Nilai terbaik yang bisa dijamin oleh pemain memaksimalkan (AI).
•	Beta (β): Nilai terbaik yang bisa dijamin oleh pemain meminimalkan (manusia).
Fungsi dalam game ini pertama kali memeriksa apakah pencarian sudah mencapai kedalaman maksimal (basis rekursi) atau permainan sudah berakhir dengan memanggil is_game_over(). Jika salah satu kondisi terpenuhi, ia akan menghitung nilai evaluasi papan menggunakan evaluate_board() dan menghentikan pencarian lebih lanjut.
Berikut contoh pohon permainan FlipDom dengan kedalaman penelusuran sedalam 3 langkah kedepan:
 ![image](https://github.com/user-attachments/assets/4b7526e1-e8ef-4321-bd72-3a2b822a32c8)

Algoritma negamax tergolong kedalam algoritma Depth First Search (DFS). Algoritma ini menelusuri pohon permainan ke bagian dalam terlebih dahulu sebelum bergerak melebar.
Untuk mengatasi banyaknya node-node yang dievaluasi oleh algoritma minimax, digunakanlah algoritma alpha beta pruning. Algoritma ini akan menggunakan nilai alpha dan beta untuk memangkas pohon pencarian yang harus ditelusuri oleh algoritma minimax. Algoritma ini membuat pencarian menjadi lebih cepat dengan tidak merubah hasil akhir dari pencarian (baik menggunakan alpha beta pruning maupun tidak hasilnya tetap sama).
Kembali ke gambar yang merupakan representasi nyata dari sebuah kondisi permainan FlipDom, algoritma Alpha Beta Pruning terlebih dahulu akan mengecek node awal (root) dengan nilai alpha = -∞ dan beta = +∞. Jika kedalaman node yang diperiksa masih belum sama dengan batas kedalaman yang diberikan maka algoritma ini akan menelusuri node anak pertama (node (b)) dari node awal (root) dengan nilai alpha = - beta dan nilai beta = -alpha. Dengan kata lain kedua nilai alpha dan beta tidak berubah saat algoritma ini melakukan pengecekan terhadap node (b) di kedalaman 1. Begitu pula dengan node (c) di kedalaman 2.
Selanjutnya algoritma Alpha Beta Pruning melakukan penelusuran di node awal pada kedalaman 3 (node (d)) yang menjadi anak dari node sebelumnya (node c)). Karena kedalaman sudah sama dengan batas kedalaman, maka algoritma akan memanggil fungsi evaluasi untuk mendapatkan nilai dari node tersebut. Sebagaimana pada gambar, nilai dari node (d) di kedalaman 3 adalah 4. Setelah diperoleh nilainya, sebelum kembali ke node (c) nilai tersebut dinegasikan menjadi -4.
Algoritma kembali ke node (c), nilai -4 kemudian dibandingkan dengan nilai alpha di node (c) yaitu -∞. Karena nilai -4 > -∞ maka nilai alpha di node itu berubah menjadi -4. Nilai alpha kemudian dibandingkan dengan nilai beta. Karena -4 tidak lebih besar atau sama dengan +∞ maka tidak terjadi pemangkasan (pruning) pada node selanjutnya.
Algoritma kemudian menuju ke node selanjutnya di kedalaman 3 yaitu node (e). Node (e) dievaluasi dengan fungsi evaluasi dan diperoleh nilai 4. Nilai itu kemudian dinegasikan. Algoritma kemudian beralih ke node (c), karena nilai -4 tidak lebih besar dari nilai alpha yang juga bernilai -4, maka nilai alpha tidak berubah. Sehingga node (c) bisa diabaikan. Kemudian algoritma beralih ke node (d), begitu seterusnya sampai ke node
(h). Nilai alpha tidak berubah karena node (d) sampai (h) semua bernilai -4.

Setelah semua anak dari node (c) diperiksa, maka diperoleh nilai node (c) adalah -4. Nilai ini kemudian dinegasikan menjadi 4. Algoritma kemudian menuju ke node (b). Disini terjadi pengecekan apakah nilai dari node (c) yaitu 4 lebih besar dari nilai alpha node (b) yaitu -∞. Karena 4 > -∞, maka nilai alpha node (b) berubah menjadi 4. Karena nilai 4 tidak lebih besar dari nilai beta pada node (b) yaitu ∞, maka tidak terjadi pruning pada node selanjutnya.
Algoritma kemudian menuju ke node-node selanjutnya hingga semua bagian dari pohon permainan ditelusuri untuk mendapatkan langkah terbaik dengan urutan langkah seperti yang telah dijabarkan sebelumnya.
`
Tabel Pengujian Permainan`
![image](https://github.com/user-attachments/assets/d68d63c2-0554-4a28-934f-bc5f8de02547)

Tabel Pengujian Setelah Langkah Pertama Pemain (Hitam)
![image](https://github.com/user-attachments/assets/68b81914-f561-41c8-a0ff-4b6de9cfd478)

Tabel Pengujian Kemungkinan Langkah Pertama Komputer (Putih)
![image](https://github.com/user-attachments/assets/7d939d7f-3837-4a5a-a5c4-7c4083b28618)

Tabel Pengujian Setelah Langkah Pertama Komputer (Putih) dan Kemungkinan Langkah Kedua Pemain (Hitam)
![image](https://github.com/user-attachments/assets/8fb370a4-5e9f-4271-bdaf-cc940755126b)
