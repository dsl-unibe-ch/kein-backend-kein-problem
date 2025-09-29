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
- frontend repo

---


