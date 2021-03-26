# Setup Node JS Web App

### Part 1





#### Setup Environment

1. Setup Visual Code Studio.

   Setup Extention VCS disini: https://github.com/vanbumi/Modern-JavaScript/blob/main/Modern-JavaScript/Fundamental-JavaScript/SetupVSC/01-visualstudio-setup.md

2. Setup GIT.



#### Instal & Setup Node JS

1. Download NodeJS disini: https://nodejs.org Pilih yang LTS version.
2. Setup database, ada 2 pilihan 
   1. Mongodb database : Cara setup lihat di tutorial RemondsApp mediocademy - bit.ly/courses-mediocademy
   2. MySQL, Cara setup menyusul.
3. Setup heroku.com (pilihan) untuk deployment app nodejs.



#### Setup Project

##### 1. Setup Express

website: https://expressjs.com/



Buat folder project di PC anda:

```
mkdir nodewebapp
```

Buka dengan VCS

Buka Terminal, lakukan perintah sbb :

```
npm init -y
```

Install Express js

```
npm install --save express
```

Buka Visual Code, buat file baru app.js

Update kode nya sbb:

```javascript
const express = require('express')
const app = express()
const port = 5000

// Setup server
app.listen(port, () => {
	console.log(`Server berjalan di port ${port}`)
})
```

Buka Terminal dan jalan kan server Node dengan perintah:

```javascript
node app.js
```

Buka browser localhost:5000

Hasilnya Cannot GET /

Karena kita belum buat route untuk menampilkan halaman web.



#### Setup Routing

Setup halaman index : 

```javascript
app.get('/', (req, res) => {
  res.send('Halaman Index')
})
```

Setup halaman About:

```javascript
app.get('/about', (req, res) => {
  res.send('Halaman About')
})
```



#### Install Nodemon

Nodemon digunakan untuk start server node js otomatis, setiap kali update kode di halaman2 project.

Stop server node js dulu dengan Ctrl + c dan lakukan perintah :

```
npm intall -g nodemon
```



Sekarang jalan kan server dengan perintah:

```
nodemon
```

Buka browser localhost:5000

dan Buka browser localhost:5000/about

selesai



#### Setup Templete Engine

Template Engine kita butuhkan untuk render View dari Server/Backend supaya bisa di lihat oleh visitor.

Ada banyak Templete Engine, yang akan kita gunakan adalah **Handlebars** - https://handlebarsjs.com/

Kita gunakan Handlebars yang sudah terintegrasi dengan Expressjs - https://github.com/ericf/express-handlebars



**Install Express-Handlebars**

```
npm install express-handlebars --save
```

Kembali ke file app.js update kode nya:

Tempatkan kode ini dibawah ```express = require('express')```

```javascript
var exphbs  = require('express-handlebars');
```

Tempatkan kode nya dibawah ```const app = express()```

```javascript
app.engine('handlebars', exphbs());
app.set('view engine', 'handlebars');
```

Dan rubah Index Route nya menggunakan ```render``` bukan lagi ```send``` :

```javascript
app.get('/', (req, res) => {
    res.render('home');
});

// Dan

app.get('/', (req, res) => {
    res.render('about');
});
```

Buat folder "views"  di root project.

Dibawah folder  "views" buat file baru : "home.handlebars". 

Dan

Dibawah folder  "views" buat foder baru : "layouts"

Dan

Dibawah folder  "layouts" buat file baru : "main.handlebars"

Dan

Dibawah folder  "layouts" buat file baru : "about.handlebars"

Struktur file nya seperti dibawah ini :

```
├── app.js
└── views
    ├── home.handlebars
    ├── about.handlebars
    └── layouts
        └── main.handlebars
```



Update file main.handlebars seperti dibawah :

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Node Web App App</title>
</head>
<body>

    {{{body}}}

</body>
</html>
```



Update file homs.handlebars seperti dibawah :

```html

<h1>Selamat Datang di Node Web App</h1>

```

Update file about.handlebars seperti dibawah :

```html
<h1>Halaman About</h1>
```

Buka browser localhost:5000

Dan 

localhost:5000/about

selesai



#### Setup BootstrapJS

Gunakan versi 4 bootsrap (v4.6)

Copy CDN bootsrap -https://getbootstrap.com/docs/4.6/getting-started/introduction/

CSS link CDN

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css" integrity="sha384-B0vP5xmATw1+K9KRQjQERJvTumQW0nPEzvF6L/Z6nronJ3oUOFUFpCjEUQouq2+l" crossorigin="anonymous">
```

Dan 

JavaScript link CDN

paste di file main.handlebars

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Node Web App App</title>
</head>
  
// start paste  
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css" integrity="sha384-B0vP5xmATw1+K9KRQjQERJvTumQW0nPEzvF6L/Z6nronJ3oUOFUFpCjEUQouq2+l" crossorigin="anonymous">
// end paste  
  
<body>

    {{{body}}}
  
  
 // start paste 
  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/js/bootstrap.min.js" integrity="sha384-+YQ4JLhjyBLPDQt//I+STsc9iw4uQqACwlvpslubQzn4u2UU2UFM80nGisd026JF" crossorigin="anonymous"></script>
// end paste
  
</body>
</html>
```

Reload browser lihat perubahan style nya.



Tambahkan : 

* Navbar, 
* Tambahkan Container diantara body tag ```<body>```

Dan tempatkan di file main.handlebars. Dan lakukan beberapa editing / refactor kode.

Hasilnya akan seperti ini :

```html

```



#### Membuat folder Partial.

> Partial akan membuat kode lebih rapih dan bersih dengan memisahkan beberapa kode ke file tersendiri.

Dibawah folder  "views" buat folder baru : "partials".

Dibawah folder  "partials" buat file baru : "_navbar.handlebars"

Pindahkan navbar dari main.handlebars ke file "_navbar.handlebars"  



Dan di file main.handlebars ganti dengan variable :

```
{{> _navbar}}
```

Reload browser dan hasilnya tetep sama.



Tambahkan Jumbotron Bootsrap pada file main.handlebars.

```html
<div class="jumbotron">
  <h1 class="display-4">Hello, world!</h1>
  <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
  <hr class="my-4">
  <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
  <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
</div>
```



Pada file about.handlebars tambahkan :

```html
<h1>About Us</h1>

<p>
Ini adalah Web App Node/ExpressJS untuk membuat static web page dengan Template Engine Handlebars Express.
</p>

<p>
  Version: 1.0.0
</p>
```

Selesai

Bersambung ke bagian ke 2 (Part 2)



