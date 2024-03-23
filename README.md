# advprog-modul6

### Commit 1

`let buf_reader = BufReader::new(&mut stream);`

Membuat BufReader object yang digunakan untuk melakukan read operations

```
let http_request: Vec<String> = buf_reader
    .lines()
    .map(|result| result.unwrap())
    .take_while(|line| !line.is_empty())
    .collect();
```

Memisahkan tiap line, kemudian mengubahnya menjadi vector

Fungsi handle_connection membaca lines dari TCP stream sampai menemukan empty line, lalu mengubah lines-lines yang sudah di read menjadi vector, lalu kemudian melakukan print vector tersebut ke console. Hal ini dilakukan untuk melakukan read headers dari sebuah HTTP request.

### Commit 2

<img width="960" alt="image" src="https://github.com/reyhanwiyasa/advprog-modul6/assets/119433464/34e4196f-20a0-4593-8864-75d645c3e7c0">

Menambahkan variabel status_line pada fungsi `handle_connection` yang menunjukan status line HTTP, yaitu "HTTP/1.1 200 OK". Variabel ini memberikan informasi kepada user bahwa permintaan berhasil (kode status 200). Lalu, akan dikirimkan file HTML statis sebagai respons `(hello.html)`. Respons dibaca menggunakan `fs::read_to_string` dan dimasukkan ke dalam variabel contents. Panjang konten dari file HTML dihitung menggunakan `contents.len() `untuk menentukan ukuran respons. Respons disusun menggunakan `format!` untuk mencakup status line, panjang konten, dan isi konten.

### Commit 3

<img width="960" alt="image" src="https://github.com/reyhanwiyasa/advprog-modul6/assets/119433464/195b56d0-564b-4661-b795-7c160c6b9a77">

- Respons HTTP dibagi berdasarkan permintaan yang diterima dari user menggunakan conditional if-else. Jika permintaan adalah `GET / HTTP/1.1`, server akan mengirimkan respons `HTTP 200 (OK)` bersama dengan konten dari file `hello.html`. Namun, jika permintaan tidak dikenali, server akan mengirimkan respons `HTTP 404 (Not Found)` bersama dengan konten dari file `404.html`.

- Alasan melakukan refaktor: condition if-else sebelum dilakukan refactoring cenderung menghasilkan duplikasi. Setelah melakukan refactor, kita lebih mudah melihat perbedaan dari kedua kasus if-else, dan memudahkan kita untuk melakukan perubahan kedepannya
