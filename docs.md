# Setup Node JS Web App



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

---

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



#### Basic Routing

 

