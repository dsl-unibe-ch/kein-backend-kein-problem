# Leveraging Code-Sharing Platforms for Textual Digitization


<style>
  .slide { background: url(img/dsl0.png) center; background-size: cover }
#  .content { filter: invert() }
  code { opacity: 0.8 }
</style>

---

[https://dsl-unibe-ch.github.io/ieee-cist25](https://dsl-unibe-ch.github.io/ieee-cist25)

![qr-code](img/qr.png) <!-- change qr code!>

---

## What's the Problem: status quo

Keeping projects alive is hard

[![legacy-Parzival-Screenshot](img/image.png)](https://parzival.unibe.ch/parzdb/index.php)

add TEIPB codebase, or some other old app with extensive codebase

<style>
    .slide img {
        max-height: 500px;        
    }
</style>
---
## ab ovo: The Schwarzenbach Project
---
## post rem: The Parzival Project
---
Data: Tustep
Code: php, html, css

The Code is 10+ years old --> PHP hasn't been updated in a few years. security issues grow.

There won't be much funding to keep it up to date.
---
Tustep --> TEI XML done by the project team
---
separation of concerns: two repositories

- Data repo
  - TEI XML
  - existDB & TEIPublisher configuration (incl. ODD)
  - static API for the frontend
  - github action to create API
- frontend repo
  - svelte code
  - Github action to build app
---
## _building_ for the future

```
# create XAR archive from src/teipb
- name: build
  run: |
    cd src/teipb
    ant xar-local
    pwd
    mv ./build/parzival-0.2.xar ../../dist/parzival-0.2.xar     
```
---

```
build_site:
    runs-on: ubuntu-latest
    services:
      existdb:
        image: existdb/existdb:6.2.0
        ports:
          - 8081:8080
```

```
steps:
- name: Install dependencies
  run: npm ci

- name: start docker
  env:
    EXISTDB_USER: 'admin'
    EXISTDB_PASS: ''
    EXISTDB_SERVER: 'http://127.0.0.1:8081'
  run: |
    npm run installXar

- name: build
  env:
    BASE_PATH: '/${{ github.event.repository.name }}'
    NODE_OPTIONS: '--max_old_space_size=9000'
  run: |
    npm run build
```
---
## As static as possible:
After the build there is no script on any server running. Everything is client-side.


