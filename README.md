# Reflection Tutorial 8 Subscriber
**Nama : Virgillia Yeala Prabowo**

**Kelas : ADVPROG-A**

**NPM : 2206829856**

### Nomor 1
what is amqp?

Jawaban :

amqp adalah singkatan dari Advanced Message Queuing Protocol. Ini adalah protokol komunikasi yang digunakan untuk pertukaran pesan antara aplikasi atau sistem yang berbeda.
### Nomor 2
what it means? guest:guest@localhost:5672 , what is the first quest, and what is the second guest, and what is localhost:5672 is for?

Jawaban : 

"guest:guest@localhost:5672" adalah URI (Uniform Resource Identifier) yang digunakan untuk mengakses server AMQP. Di sini:
- "guest" adalah nama pengguna (username) pertama.
- "guest" adalah kata sandi (password) pertama.
- "localhost:5672" adalah alamat server AMQP yang diakses. "localhost" merujuk ke mesin yang sama dengan yang melakukan permintaan, dan "5672" adalah port standar untuk koneksi AMQP.

### My screen showing the RabbitMQ interface when I run cargo run multiple times on the publisher after using threads. Here, it can be seen that the queue reaches 11 because I ran cargo run 4 times.
![alt text](assets/images/image.png)
> Ketika publisher mengirim pesan dengan cepat ke RabbitMQ, antrian terus bertambah setiap kali pesan baru dikirim. Sementara itu, subscriber mengkonsumsi pesan dengan kecepatan yang lebih lambat karena adanya penundaan yang disengaja selama 1 detik per pemrosesan pesan. Penundaan pemrosesan ini memungkinkan pesan-pesan untuk menumpuk dalam antrian.

#### My screen when I ran cargo run 4 times on the publisher and cargo run 3 times on separate consoles for the subscriber. It can be seen that the spike in the message queue has reduced, indicating faster processing than before because the requests received in the queue will be divided and assigned to 3 subscribers.
![alt text](assets/images/image-1.png)
![alt text](assets/images/image-2.png)
![alt text](assets/images/image-3.png)
![alt text](assets/images/image-4.png)
![alt text](assets/images/image-5.png)

#### Improvement
Ada beberapa perbaikan yang bisa dilakukan pada kode ini:

1. Menghindari penggunaan unwrap() karena penggunaannya dalam kode produksi tidak disarankan. unwrap() dapat menyebabkan program panic jika Result adalah Err. Sebagai alternatif, kita dapat menangani kesalahan secara elegan menggunakan match atau if let

2. Menggunakan konstanta untuk string yang diulang. Jika kita memiliki string yang digunakan beberapa kali (seperti amqp://guest:guest@localhost:5672), lebih baik mendefinisikannya sebagai konstanta di bagian atas file.