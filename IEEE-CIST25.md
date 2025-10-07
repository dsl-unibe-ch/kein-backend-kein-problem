# Leveraging Code-Sharing Platforms for Textual Digitization

<img src="img/university-of-bern-bern.png" alt="unibe logo" class="bg" style="width: 200px; left:0; top:-10px;"/>

<img src="img/logo_cist25.jpg" alt="IEEE CiSt'25 logo" class="bg" style="width: 100px; right:0; top:-10px;"/>

<p class="bg bt-left"><a href="mailto:peter.daengeli@unibe.ch">Peter Daengeli</a>, <a href="mailto:sebastian.flick@unibe.ch">Sebastian Flick</a></p>
<p class="bg bt-right"><a href="https://dsl.unibe.ch" target="_blank">Data Science Lab</a>, <a href="https://dh.unibe.ch" target="_blank">Digital Humanities</a>, University of Bern</p>

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

[https://dsl-unibe-ch.github.io/ieee-cist25](https://dsl-unibe-ch.github.io/ieee-cist25)

![qr-code](img/qr.png)

---

## Keeping projects alive is hard

|||
|:--:|:--:|
|[![legacy-Parzival-Screenshot](img/intro-legacy-parzival.png)](https://parzival.unibe.ch/parzdb/index.php) | ![vulnerabilities of our worst codebase](img/intro-vulnerabilities.png)|

<style>
  .slide img {
    max-height: 500px;        
    }
</style>
---

## Using code-sharing platforms

### to organise planning, development, and deployment

---

## Code-sharing platforms

![Code-sharing platforms](img/code-sharing-platforms-2.png)

---

## Five areas of application

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

### Creation of issues

|||
|:--:|:--:|
|Problem|Projects are spread over long stretches of time and tasks are created by multiple people|
|Approach|We create issues that have due dates and responsible people attached to them.|
|CSP (Github)|Github issues|

---

[![issues in the parzival project](img/project-management-issue.png)](https://github.com/DHBern/presentation_parzival/issues/108)
---
  
<div class="footer" data-marked="1">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Kanban Boards

|||
|:--:|:--:|
|Problem|Keeping overview over larger numbers of issues and people working on them is hard|
|Approach|We create kanban boards|
|CSP (Github)|Github kanban boards|

---

![github project of parzival](img/project-management-kanban.png)
---
  
<div class="footer" data-marked="1">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data generation: targeted IIIF manifests

|||
|:--:|:--:|
|Problem|Projects often combine image resources from various providers|
|Approach|We generate "meta" manifests that point to these resources. These manifests are used for a) further processing and b) presentation.|
|CSP (Github)|Manifest generation from YAML files by commit.|

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

### Data generation: import to transcription platforms

|||
|:--:|:--:|
|Problem|Uploading images to e.g. Transkribus is often laborious (getting images, uploading, keeping track of file names/IDs, granting access, etc).|
|Approach|Making use of the previously generated IIIF manifests to automate the whole workflow.|
|CSP (Github)|By opening an issue and specifying manifests and a target collection, the Github action fetches IIIF images and uploads them to Transkribus.|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Uploading IIIF images to Transkribus by Github issue](img/data-generation-transkribus-upload.png)]() | ![Result of the Transkribus upload](img/data-generation-transkribus-upload-done.png)|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data generation: export from transcription platforms and data transformation according to project needs

|||
|:--:|:--:|
|Problem|Exporting transcriptions from Transkribus may be tricky as the platform uses differing file names and the built-in transformations do not cover project needs.|
|Approach|Making use of project IDs and the previously generated IIIF manifests to export and transform transcriptions according to project guidelines.|
|CSP (Github)|By opening an issue and specifying a document ID, the Github action fetches the transcriptions, references the correct image file names, and applies customised structural transformations.|

---
  
<div class="footer" data-marked="2">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Exporting transcriptions from Transkribus by Github issue](img/data-generation-transkribus-export.png)]() | ![Result of the manifest generation](img/data-generation-transkribus-export-done.png)|


---
  
<div class="footer" data-marked="3">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Data management: versioning of textual data

|||
|:--:|:--:|
|Problem|TEI files are stored on a server during manual editing and annotation. It is not trivial to keep track of modifications and project progress without putting a significant burden on editors.|
|Approach|Automated revision control (Git) to track changes and have an additional backup.|
|CSP (Github)|At specified intervals (of e.g. 6 hours), all files with changes are fetched and saved to the Github repository in a scheduled action.|

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

### Data provision: targeted generation of static assets

|||
|:--:|:--:|
|Problem|Specific data representations are required for presentational outputs. At the same time, we are not able to keep customised dynamic systems running over time.|
|Approach|Pre-generation of intermediate and distribution formats of transcriptions, annotations, and other project resources.|
|CSP (Github)|Providing results of generation pipelines (XProc, XSLT) as Github Page ("static API").|

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

## As static as possible

|||
|:--:|:--:|
|Problem|Running backend servers and databases have significant maintenance and security implications and costs|
|Approach|static websites are safe, fast and low-maintenance|
|CSP (Github)|Github Actions & Pages|
---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Frontend development

|||
|:--:|:--:|
|Problem|occult & niche oldschool coding practices make onboarding and recruiting hard|
|Approach|The use of modern javascript frameworks and standards allows for rapid development of high quality|
|CSP (Github)|Github Action allow static website generation|

---

![svelte-machine](img/svelte-machine-desktop.COMO42Ha.avif)

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### Web hosting as GitHub Page

|||
|:--:|:--:|
|Problem|hosting generated pages on custom virtual machines is high maintenance|
|Approach|We use Github pages to have save, fast hosted static websites|
|CSP (Github)|Github pages|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

#### _building_ the frontend with _Actions_

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

</div>

---
Thank you for your attention!
