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
