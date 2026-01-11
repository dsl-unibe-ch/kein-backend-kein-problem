# Kein Backend, kein Problem! <br/>Wie bringen wir Inhalte lange ins Netz?

<div style="align-self: start;">
Universität Rostock, Ringvorlesung „Digital Humanities im Fokus: Methoden, Anwendungen und Perspektiven“, 12.01.2026
</div>
<img src="img/university-of-bern-bern.png" alt="unibe logo" class="bg" style="width: 200px; left:0; top:-10px;"/>


<p class="bg bt-left"><a href="mailto:peter.daengeli@unibe.ch">Peter Daengeli</a>, <a href="mailto:sebastian.flick@unibe.ch">Sebastian Flick</a></p>
<p class="bg bt-right"><a href="https://dsl.unibe.ch" target="_blank">Data Science Lab</a>, <a href="https://dh.unibe.ch" target="_blank">Digital Humanities</a>, Universität Bern</p>

<style>
  h1 {
    font: 2em var(--font-family) !important;
  }
  .bg {
    position: absolute;
    z-index: -1;
    font-size: 0.7em;
  }
  .bt-left {
    bottom: 0;
    left: 0;
  }
  .bt-right {
    bottom:0;
    right: 0;
  }
</style>

---
Link zu dieser Präsentation:
[https://dsl-unibe-ch.github.io/kein-backend-kein-problem](https://dsl-unibe-ch.github.io/kein-backend-kein-problem)

![qr-code](img/qr.png)

---

## Data Science Lab (DSL)

![Data Science Lab, Universität Bern](img/dsl-site.png)

https://dsl.unibe.ch | https://github.com/dsl-unibe-ch

---

## Struktur und Rollen

* Team von 4-5 KollegInnen
* Zuständig für den Bereich *Digital Humanities* (aka *DRUIDS*, "Digital Research, User Interfaces and Data Science for the Humanities")
* Übergreifende Koordination durch einen Domänenleiter

---

## Ausgewählte Kooperationen (Forschungsprojekte, Digitale Editionen, Supportfälle)

(dse-as, ceresa, rdl, parzival)

---

## Projekte am Leben zu erhalten ist schwierig

|||
|:--:|:--:|
|[![legacy-Parzival-Screenshot](img/intro-legacy-parzival.png)](https://parzival.unibe.ch/parzdb/index.php) | ![vulnerabilities of our worst codebase](img/intro-vulnerabilities.png)|

<style>
  .slide img {
    max-height: 500px;        
    }
</style>
---

## Code-sharing-Plattformen nutzen
<div style="display: flex;">
<div>

- Planung
- Development
- Deployment

</div>

![Code-sharing-Plattformen](img/code-sharing-platforms-2.png)

</div>

---

## Anwendungsgebiete

- Project management
- Data generation
- Data management
- Data provision
- Data publication

---
  
<div class="footer" data-marked="1">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Project management: Issues erstellen

|||
|:--:|:--:|
|Problem|Projekte haben eine lange Dauer und mehrere Mitarbeiter|
|Approach|Wir erstellen Issues, denen wir Fälligkeiten und verantwortliche Personen zuweisen.|
|CSP (GitHub)|GitHub **issues**|

---

[![issues in the parzival project](img/project-management-issue.png)](https://github.com/DHBern/presentation_parzival/issues/108)
---
  
<div class="footer" data-marked="1">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Project management: Kanban Boards

|||
|Problem|Die Übersicht über viele Issues und der daran arbeitenden Personen ist schwierig|
|Approach|Wir erstellen Kanban Boards|
|CSP (GitHub)|GitHub **kanban boards**|

---

![github project of parzival](img/project-management-kanban.png)
---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data generation: gezielte IIIF Manifeste

|||
|:--:|:--:|
|Problem|Projekte kombinieren häufig Bildressourcen von verschiedenen Anbietern|
|Ansatz|Wir erstellen „Meta“-Manifeste, die auf diese Ressourcen verweisen. Diese Manifeste werden a) zur weiteren Verarbeitung und b) zur Präsentation verwendet.|
|CSP (GitHub)|Manifest Generierung aus YAML-Dateien per **commit**.|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Generating IIIF manifests from YAML files by Git Commit](img/data-generation-iiif-manifests.png)]() | ![Result of the manifest generation](img/data-generation-iiif-manifest-index.png)|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data generation: import zu Transkriptionsplattformen

|||
|:--:|:--:|
|Problem|Das Hochladen von Bildern (z. B. zu Transkribus) ist oft mühsam — Beschaffung der Bilder, Upload, Nachverfolgung von Dateinamen/IDs, Zugriffsfreigaben usw.|
|Approach|Wir nutzen die zuvor erzeugten IIIF‑Manifeste, um den gesamten Workflow zu automatisieren.|
|CSP (GitHub)|Durch das Öffnen eines **issue** und die Angabe der Manifeste sowie einer Ziel‑Collection holt eine GitHub‑Action die IIIF‑Bilder und lädt sie zu Transkribus hoch.|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Uploading IIIF images to Transkribus by GitHub issue](img/data-generation-transkribus-upload.png)]() | ![Result of the Transkribus upload](img/data-generation-transkribus-upload-done.png)|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data generation: export aus Transkriptionsplattformen und Daten-Transformationen

|||
|:--:|:--:|
|Problem|Das Exportieren von Transkriptionen aus Transkribus kann knifflig sein, da die Plattform unterschiedliche Dateinamen verwendet und die eingebauten Transformationen nicht den Projektanforderungen entsprechen.|
|Approach|Nutzung von Projekt‑IDs und den zuvor erzeugten IIIF‑Manifests, um Transkriptionen gemäss den Projektvorgaben zu exportieren und zu transformieren.|
|CSP (GitHub)|Durch das Öffnen eines **issue** und die Angabe einer Dokument‑ID holt eine GitHub‑Action die Transkriptionen, ordnet die korrekten Bilddateinamen zu und wendet kundenspezifische strukturelle Transformationen an.|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Exporting transcriptions from Transkribus by GitHub issue](img/data-generation-transkribus-export.png)]() | ![Result of the manifest generation](img/data-generation-transkribus-export-done.png)|


---
  
<div class="footer" data-marked="3">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data management: Versionierung von Textdaten

|||
|:--:|:--:|
|||
|:--:|:--:|
|Problem|TEI-Dateien werden während der manuellen Bearbeitung und Annotation auf einem Server gespeichert. Änderungen und Projektfortschritt lassen sich nicht ohne erheblichen Mehraufwand für die Editierenden verfolgen.|
|Approach|Automatisierte Versionskontrolle (Git) zur Nachverfolgung von Änderungen und als zusätzliche Sicherung.|
|CSP (GitHub)|In festgelegten Intervallen (z. B. alle 6 Stunden) werden alle veränderten Dateien abgeholt und per **scheduled action** im GitHub-Repository gesichert.|
|Limitation|Commits bilden zeitliche Schnappschüsse ab, nicht Aufgaben oder Workflow‑Schritte.|

---
  
<div class="footer" data-marked="3">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Frequent data commits in scheduled action.](img/data-management-scheduled-backup.png)]() | ![Scheduled commits](img/data-management-backup-commits.png)|

---
  
<div class="footer" data-marked="4">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data provision: Generierung statischer Outputs

|||
|:--:|:--:|
|Problem|Für Präsentationsausgaben werden spezifische Datenrepräsentationen benötigt. Gleichzeitig sind wir nicht in der Lage, massgefertigte dynamische Systeme langfristig am Laufen zu halten.|
|Approach|Vorabgenerierung von Zwischen- und Distributionsformaten für Transkriptionen, Annotationen und andere Projektressourcen.|
|CSP (GitHub)|Bereitstellung der Ergebnisse der Generierungspipelines (XProc, XSLT) als **GitHub Page** („static API“).|

---
  
<div class="footer" data-marked="4">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Generation pipeline for static (intermediary) outputs.](img/data-provision-static-api.png)]() | ![Generated outputs ("static API").](img/data-provision-static-api-index.png)|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

## Data publication: as static as possible

|||
|:--:|:--:|
|||
|:--:|:--:|
|Problem|Der Betrieb von Backend‑Servern und Datenbanken verursacht hohen Wartungsaufwand, Sicherheitsrisiken und laufende Kosten.|
|Approach|Statische Websites sind sicher, schnell und wartungsarm.|
|CSP (GitHub)|GitHub **Actions** und **Pages**|
|Limitation|Für dynamische Funktionalitäten (Suche, IIIF usw.) nutzen wir universitätsweite Dienste.|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data publication: Frontend Entwicklung

|||
|:--:|:--:|
|Problem|Obskure, Nischen‑Programmierpraktiken erschweren Onboarding und Rekrutierung.|
|Approach|Der Einsatz moderner JavaScript‑Frameworks und Standards ermöglicht schnelle Entwicklung qualitativ hochwertiger Lösungen.|
|CSP (GitHub)|Statische Website‑Generierung mit GitHub **Actions** (geht weit über SSG‑Tools wie Jekyll hinaus).|

![svelte-machine](img/svelte-machine-desktop.COMO42Ha.avif)

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data publication: web hosting mit Github Pages

|||
|:--:|:--:|
|Problem|Das Hosten generierter Seiten auf eigenen virtuellen Maschinen ist mit höherem Wartungsaufwand verbunden.|
|Approach|Wir nutzen GitHub Pages, um sichere und schnelle statische Websites bereitzustellen.|
|CSP (GitHub)|GitHub **Pages**|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

#### Das Frontend _builden_ mit _Actions_

<div style="display: flex; ">

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
    EXISTDB_SERVER: 'http://127.0.0.1:8081'
  run: npm run installXar

- name: build
  env:
    BASE_PATH: '/${{ github.event.repository.name }}'
    NODE_OPTIONS: '--max_old_space_size=9000'
  run: npm run build
```

</div>

---
Vielen Dank für Ihre Aufmerksamkeit!
