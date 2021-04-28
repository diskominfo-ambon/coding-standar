  
# HTML
Panduan ini mengasumsikan kamu sudah memahami secara baik **HTML** , dan mengharuskan kamu untuk menggunakan **HTML Semantic**.

>**Catatan**: Perbaiki panduan ini untuk memberikan informasi atau pemahaman yang lebih baik.

## Daftar isi

 - [Pengantar HTML *Semantic*](#pengantar-html-semantic)
 - [Penggunaan HTML *Semantic*](#penggunaan-html-semantic)
 - [Struktur HTML 5](#struktur-html-5)
 - [`CSS` dan `Javascript`](#css-dan-javascript)
 - [`Font`](#font)
 - [`img` dan `picture`](#img-dan-picture)
 - [`anchor`](#anchor)
 - [`music` dan `video`](#music-dan-video)
 - [`iframe`](#iframe)
 - .... 

## Pengantar HTML Semantic
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


## Struktur HTML 5
Gunakan struktur lengkap HTML 5 untuk mengoptimalkan rendering web yang lebih baik (browser pengguna) serta meningkatkan penggunaan SEO.

❌ Tidak disarankan
```html
<div>
<!-- konten web disini -->
</div>
```

✅ Lebih baik
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8"/> 
	<meta name="description"  content="deskripsi web">  
	<meta name="keywords"  content="web keyword pencarian">
	<title>Judul web</title>
</head>
<body>
<!-- konten web disini -->
</body>
</html>
```
> **Catatan**: Penting untuk menyertakan informasi *encoding charset* yang berguna dalam menentukan pengkodean karakter (menerjemahkan informasi) untuk dokumen HTML. Jika tidak disertakan maka akan diatur secara implisit oleh browser ke `UTF-8`.
> 
>Baca lebih lanjut [disini](https://id.wikipedia.org/wiki/Pengodean_karakter)




😼 Bonus

Gunakan tag `meta` *(jika perlu)* untuk memberikan informasi deskriptif bagi penggunaan dalam media sosial.

Contoh untuk meningkatkan informasi web bagi media **Facebook**.
> **Catatan**: Baca lebih lanjut [disini](https://developers.facebook.com/docs/sharing/webmasters/).
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8"/> 
	<meta name="description"  content="deskripsi web">  
	<meta name="keywords"  content="web keyword pencarian">
	<!-- informasi facebook -->
	<meta  property="og:url" content="url konten"  />  
	<meta  property="og:type"  content="jenis media"  /> 
	<meta  property="og:title"  content="informasi judul"  />
	<meta  property="og:description"  content="informasi dekripsi"  /> 
	<meta  property="og:image"  content="url gambar cover"  />
	<!-- end -->
	
	<title>Judul web</title>
</head>
<body>
<!-- konten web disini -->
</body>
</html>
```
Hasil:

![enter image description here](https://neilpatel.com/wp-content/uploads/2014/03/FB-my-full.png)

## CSS dan Javascript
Penggunaan gaya CSS maupun Javascript secara *inline* atau bersamaan dalam file HTML tidak disarankan dan dapat mengakibatkan pembagian sumber masalah yang tidak tepat.
> **Catatan**: Baca lebih lanjut mengenai [pembagian sumber masalah](https://en.wikipedia.org/wiki/Separation_of_concerns).

❌ Tidak disarankan

```html
<!-- Struktur HTML -->
<head>
<style>
	p {
		color: blue;
		font-size: 1.2rem;
	}
</style>
</head>
<body>
	<h1 style="color: red;">Halo dunia</h1>
	<p>Meoww.. 😺</p>
</body>
```


✅ Lebih baik
```html
<!-- Struktur HTML -->
<head>
	<!-- file CSS -->
	<link rel="stylesheet" href="file.css"/>
</head>
<body>
	<h1 class="title">Halo dunia</h1>
	<p class="subtitle">Meoww.. 😺</p>
</body>
```
```css
.title {
	color: red;
}

.subtitle {
	color: blue;
	font-size: 1.2rem;
}
```

Pengunaan yang lebih baik dengan memisahkan setiap masalah (dalam hal ini dalam penataan dokumen HTML) ke setiap file terpisah sehingga dapat meningkatkan keterbacaan, skalabilitas dan penggunaan kembali (dalam hal ini file CSS).


😸 Bonus

Terkadang mendapati kasus aplikasi yang menyimpan prefensi penggunanya ke dalam basis data dalam hal ini opsi Tema, yang memungkinkan pengguna untuk memilih tema yang akan mereka gunakan dalam aplikasi.

Contoh implementasi sederhana aplikasi yang menyediakan beberapa Tema (mode terang 🌕 dan gelap 🌒).


❌ Tidak disarankan
```php,html
<?php
// membuat koneksi.
$mysql = new MysqlConnection();

// tema yang dipilih, nilai ini didapatkan dari form.
$themeSelected = 'dark';

// ambil daftar tema dari basis data.
$theme = $mysql->table('themes')->select($themeSelected)->get();


?>

<!-- Struktur HTML -->
<head>
<style>
	body {
		background-color: <?php echo $theme->color; ?>
		font-size: 1.2rem;
	}
</style>
</head>
<body>
	<h1 style="color: <?= $theme-textColor ?>;">Halo dunia</h1>
	<p>Meoww.. 😺</p>
</body>

```


✅ Lebih baik
```php,html
<?php
// membuat koneksi.
$mysql = new MysqlConnection();

// tema yang dipilih, nilai ini didapatkan dari form.
$themeSelected = 'dark';

// ambil daftar tema dari basis data.
$theme = $mysql->table('themes')->select($themeSelected)->get();


?>

<!-- Struktur HTML -->
<head>
	<!-- file CSS -->
	<link rel="stylesheet" href="file.css"/>
</head>
<body class="<?= $theme->isDark ? 'is-dark' : 'is-light'  ?>">
	<h1 class="title <?= $theme->isDark ? 'is-dark' : 'is-light' ?>">Halo dunia</h1>
	<p>Meoww.. 😺</p>
</body>

```

```css
.title {
	color: red;
}

.subtitle {
	color: blue;
	font-size: 1.2rem;
}

// Tema yg tersedia.

.is-dark {
	background-color: black;
}
.is-light {
	background-color: white;
}
```
Perlu diingat agar dapat tetap menjaga perhatian pembagian masalah.

Selaras dengan penggunaan `CSS` diatas, penggunaan kode `Javascript` dapat dilakukan dengan hal yang serupa.

Contoh kode `Javascript`.

❌ Tidak disarankan
```html
<!-- Struktur HTML -->
<body>
	<p>Meoww.. 😺</p>
	
	<script type="text/javascript">
		const name = 'azman';
		
		alert(`Hai ${name}`);
	</script>
</body>
```

✅ Lebih baik

```html
<!-- Struktur HTML -->
<body>
	<p>Meoww.. 😺</p>
	
	<script src="app.js" type="text/javascript"></script>
</body>
```
```js
-> file app.js

const name = 'azman';

alert(`Hai ${name}`);
```

## Font
Pengguaan font dapat menggunakan [Google font](https://fonts.google.com/) dan menyertakannya dalam file HTML.
```html
...
<head>
	<link href="https://fonts.googleapis.com/css?family=Roboto:400,400i,600" rel="stylesheet">
</head>
<body>
.....
</body>
.....
```

## IMG dan Picture
Dalam menggunakan tag `img` alangkah baiknya juga menyertakan tag `alt`  untuk memberikan informasi mengenai gambar tersebut. Selain itu penggunaan tag `alt`  dapat membantu dalam meningkatkan penggunaan SEO.

```html
<img src="kucing.jpg" alt="gambar kucing imut"/>
```

Berbeda dengan tag `img` penggunaan tag `picture`  memberi pengembang web lebih banyak fleksibilitas dalam menentukan sumber daya gambar yang ingin dimuat. 

Penggunaan tag `picture` adalah untuk menentukan sumber daya yang ingin dimuat dalam desain responsif seperti mobile, tablet, desktop, dsb.  Sebaliknya alih-alih memiliki satu gambar (seperti penggunaan sebelumnya) yang diperbesar atau diperkecil berdasarkan semua viewport (layar pengguna) browser akan mencari elemen `source` pertama di mana atribut `media` cocok dengan lebar viewport (layar pengguna) saat ini, dan kemudian akan menampilkan gambar yang sesuai (ditentukan dalam atribut srcset). tag `img` dalam `picture` diperlukan sebagai opsi fallback jika tidak ada tag `source` yang cocok.

Keuntungan dengan menggunakan pendekatan ini adalah untuk meningkatkan penggunaan pengguna yang lebih baik dalam desain web responsif.

```html
<picture>  
	<source media="(min-width:650px)" srcset="kucing-650.jpg">  
	<source media="(min-width:465px)" srcset="kucing-465.jpg">
	
	<!-- tambahkan media lainnya -->
	  
	<img src="kucing.jpg" alt="gambar kucing imut" height="500" width="500">  
</picture>
```

## Anchor
Penggunaan navigasi yang baik dapat meningkatkan pengalaman pengguna yang lebih sehingga perlu diperhatikan pratik umum dalam menyediakan navigasi untuk halaman web.

Jika dimungkinkan pengalihan ke sumber lain gunakan atribut `target="__blank"`.
```html
<a href="https://google.com" target="__blank">Ke google yuk</a>
``` 

> **Catatan**: Baca lebih lanjut mengenai tag `a` [disini](https://www.w3schools.com/tags/tag_a.asp).

## Music dan Video
😭Belum tersedia.
