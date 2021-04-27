
# HTML
Panduan ini mengasumsikan kamu sudah memahami secara baik **HTML** , dan mengharuskan kamu untuk menggunakan **HTML Semantic**.

>**Catatan**: Perbaiki panduan ini untuk memberikan informasi atau pemahaman yang lebih baik.

## Agenda

 - [Pengantar HTML *Semantic*](#pengantar-html-semantic)
 - [Penggunaan HTML *Semantic*](#penggunaan-html-semantic)
 - Struktur HTML 5
 - `css`.
 - `javascript`
 - `font`
 - `img` dan `picture` 
 - `anchor` (Navigasi link)
 - `video`
 - `music`
 - `iframe`
 - `svg`
 - .... 

## Pengatar HTML Semantic
*Semantic* HTML adalah penggunaan markup HTML untuk memperkuat makna dari  informasi halaman web, sebaliknya dari pada hanya untuk mendefinisikan presentasi atau tampilan yang umum.

> Baca informasi lebih terkait [**HTML Semantic**](https://www.w3schools.com/html/html5_semantic_elements.asp).

## Penggunaan HTML Semantic
Penggunaan Semantic HTML memberikan informasi yang lebih kaya bagi pengguna web serta perangkat lunak browser. Salah satu manfaatn *Semantic* HTML memberikan solusi yang baik bagi mereka yang mengalami [aksesibilitas](https://id.wikipedia.org/wiki/Aksesibilitas).

Contoh implementasi:

❌ Tidak disarankan

Tidak memberikan informasi yang deskriptif, informasi yang digunakan merupakan tag `input` yang penggunaanya (umumnya) sebagai memberikan masukan pengguna ke dalam aplikasi browser.
```html
<input type="button" value="Login ke aplikasi">
```


✅ Menggunakan HTML *Semantic*

Terlihat jelas maksud dan informasi dari penggunaannya. 
```html
<button type="button">
Login ke aplikasi
</button>
```
