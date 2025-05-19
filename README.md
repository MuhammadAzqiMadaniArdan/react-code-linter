# React + Vite

<div style="text-align:'center'">
<h1>Code Format</h1> 
eslint,husky,prettier,lint-staged
</div>

<hr />
<h2>0.Materi Awal dan apa yang perlu diperhatikan dalam penulisan code menurut Attlasian (ada 4 tapi poin yang diambil disini 2)</h2>

Code Convention
->Penulisan Kode di setiap perusahaan -> Penulisannya gimana

Code Linter
->Memeriksa code secara otomatis yang sudah di diva / ditetapkan oleh perusahaan di code convention nya

contoh code Linter : menggunakan ESLINT

</h2>1.Install ESlint</h2>

-instalasi
cmd = npm init @eslint/config@latest

-pengisian saat configurasi install
lint : javascript
use ESlint : to check syntax and find problems (opsi 2)
Type of Module : JavaScript Modules
Framework : menyesuaikan yang sedang digunakan
Typescript : yes jika pakai | no jika tidak pakai
Code run : browser
install plugin : yes
package manager use : npm (menyesuaikan)

-ignore Eslint di eslint.config.js

menggunakan globalIgnores dibawah pluginReact:
	globalIgnores(['node_modules/', 'public/']),


-Tambahkan rules masing masing disimpan di eslint.config.js didalam objek pertama setelah extends

format rapih react :
       rules: {
            'no-console': ['error'],
            'prefer-const': ['error'],
            'camelcase': ['error'],
        },

-jalankan perintah
npm run lint -> menjalankan perintah lint

catatan : setelah konfigurasi keluar dari vscode dulu dan masuk lagi untuk hasil konfig ESlint


<h2>2.Prettier</h2>

-install
npm install --save-dev --save-exact prettier

-buat file .prettierignore
berisi folder yang tidak dapat diakses
contoh :
Ignore artifacts:

build
coverage
node_modules
public

-buat file .prettierrc.json
isi sesuai dengan format prettier yang diinginkan
contoh default : 
{
    "tabWidth": 4,
    "semi": false,
    "singleQuote": true
}

tambahkan trailingcomma jika mau : trailingComma: "es5"
maksudnya adalah
menambahkan koma diakhir suatu objek dengan validasi rules valid dari ES5
contoh :
✅ ditambahkan koma
const obj = {
  a: 1,
  b: 2, // ← trailing comma diizinkan
};

const arr = [
  1,
  2,
  3, // ← trailing comma
];

❌ Tidak ditambahkan koma:

function example(a, b) {
  // Tidak ada trailing comma di parameter function
}

apa itu ES5 ini dia :
ES5 adalah versi stabil JavaScript yang mendefinisikan banyak fitur penting dan aman digunakan di semua browser.

Karena ES5 adalah versi terakhir yang didukung oleh semua browser modern lama (termasuk IE11). Jadi saat Prettier menggunakan "trailingComma": "es5", itu berarti:

🔸 Tambahkan trailing comma hanya di tempat yang valid menurut standar ES5, agar tetap compatible dan aman di semua browser lama.


-cli di package.json
di scripts tambahkan ini :
        "format": "prettier . --write",

-jalankan Prettier
npm run format

<h2>3.Lint Staged</h2>

-instalasi
npm i lint-staged@12.3.2

-setelah install tambahkan ini di package.json dibawah scripts object
"lint-staged": {
        "*.{js,jsx,ts,tsx}": "eslint"
    },

<h2>4.Git Repo</h2>
- init dan buat remote ke GitHub
- git init dan git remote add origin nama_repo

<h2>5.Install Husky</h2>

npm install --save-dev husky 
npx husky init

-config precommit
di dalam folder .husky/precommit 
hapus npm test menjadi npx lint-staged

-Ubah package.json lint-staged menjadi seperti dibawah :

    "lint-staged": {
        "*.{js,jsx,ts,tsx}": [
            "eslint . --fix",
            "prettier . --write"
        ]
    },

Keterangan : agar saat di commit maka akan auto fix dari eslint dan membuat kode mengikuti rules dan guide prettier

<h2>6.Kenapa ? / WHY ?</h2>
Kenapa Harus di format dan melakukan pengkodean dengan rapih

-Terdapat suatu case ada AT&T sebuah produk digital yang pernah down selama 9 jam down di production karena ada code yang buggy dan mengganggu operasional ehingga merugikan perusahaan

<h2>7.Docs</h2>

husky : https://typicode.github.io/husky/
lint : https://www.npmjs.com/package/lint-staged/v/12.3.2
prettier : https://prettier.io/docs/configuration
eslint : https://eslint.org/docs/latest/rules/

<hr />

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.
