# Tutorial 1: Timer

## 1.2. Understanding how it works.

Pada kode ini, spawner.spawn(...) tidak langsung menjalankan task, tetapi hanya mengirim future ke task queue. Tetapi disini, println!("Angger's computer: hey hey!") dieksekusi langsung di thread utama, tanpa await, tanpa delay, langsung dijalankan. Dan akhirnya, executor.run() baru mengeksekusi task yang sudah dikirim ke queue. Di sinilah future dijalankan dan queue di dalamnya dieksekusi. Jadi urutan yang sebenarnya adalah spawner.spawn(...): mendaftarkan future ke task queue, belum dijalankan, lalu println!("Angger's computer: hey hey!"): langsung dieksekusi di thread utama — cepat, tanpa delay, terakhir barulah, executor.run() dijalankan.

![Alt text](image.png)