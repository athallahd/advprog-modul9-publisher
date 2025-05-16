# # Module 9 Adpro Publisher Reflection

Nama: Athallah Damar Jiwanto <br>
NPM: 2306245024 <br>
Kelas: Advprog-B
<hr>

1. How much data your publisher program will send to the message broker in one run? <br>
Data yang dikirimkan sebanyak 5 data ke message broker dengan masing-masing message berupa instance dari struct `UserCreatedEventMessage` yang memiliki dua field: `user_id` dan `user_name`, yang bertipe `String`.

2. The url of: `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean? <br>
URL tersebut sama karena publisher maupun subscriber **terhubung ke broker yang sama**, yang berjalan di mesin lokal (`localhost`) pada port `5672`, dengan username dan password default `guest:guest`. Artinya **Publisher** akan mengirim pesan ke broker itu dan **Subscriber** akan menerima pesan dari broker yang sama, selama mereka mendengarkan queue yang sama. Dengan URL yang sama itu, komunikasi antar komponen dapat terjadi secara real-time melalui message broker tersebut.

## Message Broker: RabbitMQ
![rabbitmq](images/rabbitmqpublisher.png)

## Event Sending
![sending event](images/sendingevent.png)
Gambar menunjukkan sebuah proyek messaging dengan arsitektur publisher-subscriber menggunakan RabbitMQ sebagai message broker. Di sisi kiri terlihat program publisher (dalam Rust) yang sedang berjalan dan mengirimkan data ke message broker dengan perintah `cargo run`. Di sisi kanan terlihat program subscriber yang menerima pesan-pesan tersebut, menampilkan 5 `UserCreatedEventMessage` dengan ID dan nama pengguna. Terminal menampilkan output eksekusi di kedua sisi, menunjukkan komunikasi asinkron yang berhasil terjadi antara dua aplikasi melalui protokol `AMQP (Advanced Message Queuing Protocol)`.

## Monitor Spikes on Chart
![Spike Chart](images/spikingchart.png)
Dashboard menunjukkan grafik message rates dengan beberapa puncak (spike) aktivitas dalam interval waktu 17:22:40 hingga 17:23:30, dengan puncak tertinggi sekitar 6.0/s.