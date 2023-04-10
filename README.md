<p align="center">
  <a href="https://github.com/riimuru/gogoanime">
    <img src="https://avatars.githubusercontent.com/u/90430786?v=4" alt="Logo" width="150" >
  </a>

  <h3 align="center">Lucky Anime Rest API</h3>

  <p align="center">
    <samp>A free anime app restful API serving anime from <a href="https://luckyanimeku.netlify.app/">LuckyAnime</a></samp>
    <br />
    <a href="#routes"><strong>Explore the api »</strong></a>
    <br />
    <br />
    <a href="https://github.com/riimuru/gogoanime/issues/new?assignees=riimuru&labels=bug&template=bug-report.yml">Bug report</a>
    ·
    <a href="https://github.com/riimuru/gogoanime/issues/new?assignees=riimuru&labels=enhancement&template=feature-request.md">Feature request</a>
  </p>
  <p align="center">
    <a href="https://github.com/riimuru/gogoanime/actions/workflows/docker-build.yml">
      <img src="https://github.com/riimuru/gogoanime/actions/workflows/docker-build.yml/badge.svg" alt="stars">
    </a>
     <a href="https://github.com/riimuru/gogoanime/actions/workflows/codeql-analysis.yml">
      <img src="https://github.com/riimuru/gogoanime/actions/workflows/codeql-analysis.yml/badge.svg" alt="stars">
    </a>
    <a href="https://github.com/riimuru/gogoanime">
      <img src="https://img.shields.io/github/stars/riimuru/gogoanime" alt="stars">
    </a>
    <a href="https://discord.gg/qTPfvMxzNH">
      <img src="https://img.shields.io/discord/987492554486452315?color=7289da&label=discord&logo=discord&logoColor=7289da" alt="Discord">
    </a>
        <a href="https://github.com/consumet/extensions/blob/master/LICENSE">
      <img src="https://img.shields.io/github/license/consumet/extensions" alt="GitHub">
    </a>
  </p>
</p>


<h1> Table of Contents </h1>

- [Installation](#installation)
  - [Local](#local)
- [List Source](#list-source)
- [Routes](#routes)
  - [Get Recent Episodes](#get-recent-episodes)
  - [Get Popular Anime](#get-popular-anime)
  - [Get Anime Search](#get-anime-search)
  - [Get Genre List](#get-genre-list)
  - [Get Genre](#get-genre)
  - [Get Season List](#get-season-list)
  - [Get Season](#get-season)
  - [Get Anime Details](#get-anime-details)
  - [Get Streaming URLs](#get-streaming-urls)

## Installation

### Local

Run command berikut untuk mengclone repo ini, dan menginstall dependencies:

```sh
git clone https://github.com/miukyo/aniyoi-api.git
cd aniyoi-api
npm install #atau yarn install
```

Start server dengan command berikut:

```sh
npm start #atau yarn start
```

Server akan berjalan di http://localhost:3001

## List Source

Beberapa source mungkin tidak support dengan beberapa fitur. Dikarenakan kurangnya informasi pada website asli.

| Source            | Fitur yang bermasalah                                                                                                                                                                                |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <b>Kuronime</b>   | <ul><li>🟡 Mendapatkan Streaming URL mungkin agak lama karena link url di Enkripsi dan harus di Dekripsi dahulu dari playernya.</li><li>🔴 Source video selain local tidak di support</li></ul>        |
| <b>Kuramanime</b> | <ul><li>🔴 Anime Terbaru tidak menampilkan yang terbaru melainkan campur aduk.</li><li>🔴 Anime Popular juga sama dengan yang diatas.</li><li>🔴 Beberapa page hanya memiliki maximum 8 page.</li></ul> |
| <b>Nanime</b>     | <ul><li>🔴 Tidak support direct Streaming URL hanya bisa menggunakan embed.</li><li>🔴 Tidak ada Anime Popular.</li></ul>                                                                              |
| <b>Otaku Desu</b> Cancelled     | <ul><li>🔴 Slug URL Details Anime berbeda dengan Slug URL Episode</li></ul>                                                                              |


Jika kalian tau website anime subtitle anime yang bagus dan detail mohon kontak saya. Akan saya include di sini, Terima kasih!

## Routes

Contoh dibawah menggunakan [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), kamu juga bisa menggunakan library http lainnya.

### Get Recent Episodes

| Parameter    | Description                               |
| ------------ | ----------------------------------------- |
| `page` (int) | pilih page dari maximum page. Default : 1 |

```js
fetch("localhost:3001/{source}/recent")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "list": [
     {
      "slug": string,
      "title": string,
      "episode?": number, //(optional)
      "cover": string,
      "url": string,
      },
     {...}
   ],
   "maxPage": number,
   "page": number,
}
```

### Get Popular Anime

| Parameter    | Description                               |
| ------------ | ----------------------------------------- |
| `page` (int) | pilih page dari maximum page. Default : 1 |

```js
fetch("localhost:3001/{source}/popular")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "list": [
     {
      "slug": string,
      "title": string,
      "cover": string,
      "url": string,
      },
     {...}
   ],
   "maxPage": number,
   "page": number,
}
```

### Get Anime Search

| Parameter        | Description                               |
| ---------------- | ----------------------------------------- |
| `query` (string) | nama anime yang ingin dicari              |
| `page` (int)     | pilih page dari maximum page. Default : 1 |

```js
fetch("localhost:3001/{source}/search")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "list": [
     {
      "slug": string,
      "title": string,
      "cover": string,
      "url": string,
      },
     {...}
   ],
   "maxPage": number,
   "page": number,
}
```

### Get Genre List

| Parameter | Description |
| --------- | ----------- |
| -         | -           |

```js
fetch("localhost:3001/{source}/genre")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>


```ts
[
  {
    "slug": string,
    "title": string,
    "url": string,
  },
  {...},
]
```

### Get Genre

| Parameter              | Description                                             |
| ---------------------- | ------------------------------------------------------- |
| `page` (int)           | pilih page dari maximum page. Default : 1               |
| `:genre-slug` (string) | genre slug dapat didapatkan dalam respon **Genre List** |


```js
fetch("localhost:3001/{source}/genre/{genre-slug}")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "list": [
     {
      "slug": string,
      "title": string,
      "cover": string,
      "url": string,
      },
     {...}
   ],
   "maxPage": number,
   "page": number,
}
```

### Get Season List

| Parameter | Description |
| --------- | ----------- |
| -         | -           |

```js
fetch("localhost:3001/{source}/season")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>


```ts
[
  {
    "slug": string,
    "title": string,
    "url": string,
  },
  {...},
]
```

### Get Season

| Parameter               | Description                                               |
| ----------------------- | --------------------------------------------------------- |
| `page` (int)            | pilih page dari maximum page. Default : 1                 |
| `:season-slug` (string) | season slug dapat didapatkan dalam respon **Season List** |

```js
fetch("localhost:3001/{source}/season/{season-slug}")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "list": [
     {
      "slug": string,
      "title": string,
      "cover": string,
      "url": string,
      },
     {...}
   ],
   "maxPage": number,
   "page": number,
}
```

### Get Anime Details

| Parameter              | Description                                                   |
| ---------------------- | ------------------------------------------------------------- |
| `:anime-slug` (string) | anime slug dapat didapatkan dalam respon list seperti diatas. |

```js
fetch("localhost:3001/{source}/anime/{anime-slug}")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "slug": string,
  "title": string,
  "titleAlt?": string, //(optional)
  "synopsis?": string, //(optional | beberapa ada yang tidak memiliki sinopsis)
  "episodeTotal": number, //(anime ongoing di kuronime akan merespon "0")
  "episode": number,
  "season?": string, //(optional)
  "genre?": string[], //(optional)
  "cover": string,
  "url": string,
}
```

### Get Streaming URLs


| Parameter              | Description                                                      |
| ---------------------- | ---------------------------------------------------------------- |
| `:anime-slug` (string) | anime slug dapat didapatkan dalam respon list seperti diatas.    |
| `:anime-episode` (int) | pilih episode anime yang tersedia dalam respon **Anime Details** |


```js
fetch("localhost:3001/{source}/anime/{anime-slug}/{anime-episode}")
  .then((response) => response.json())
  .then((animelist) => console.log(animelist));
```

Output >>

```ts
{
  "episode": number,
  "video":  [
    {
      "quality": string,
      "url": string,
    },
    {...},
  ]
}
```




### Heroku
Host your own instance of the api on heroku using the button below.

[![Deploy on Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/riimuru/gogoanime/tree/main)

### Render
Host your own instance of the api on render using the button below.

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/riimuru/gogoanime-api)

### Railway
Host your own instance of the api on railway using the button below.

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template/Lg6DEp?referralCode=dv4TuD)
