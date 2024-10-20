---
title: Orpheus Docs
markdown: true
---

![Orpheus Title Sketch by Mike]({{ imagesRoot }}/documents/orpheus/orpheus.jpg)

# Orpheus Documents

## by Mike Hoge

All of these documents, most of them handwritten, were part of the folders we received from Mike and were digitised by us. We thus cannot say when these documents were written precisely. But they all have been written in ~1995-1996. 

Document                                                            | Filename                | Size
--------------------------------------------------------------------|-------------------------|---------
~~Zusammenfassung zum Orpheus Konzeot~~                             | (lost)                  | - 
[Konzept Fragment: Graphiken]({{ mediaLinkBase }}/orpheus/OrpheusConceptSummary.pdf) | ConceptSummary.pdf | 12.2 MB
[Animations]({{ binDir }}/orpheus/OrpheusAnimations.pdf)            | Animations.pdf          | 1.8 MB
[Interface]({{ binDir }}/orpheus/OrpheusInterface.pdf)              | Interface.pdf           | 6.3 MB
[Der Rote Faden V1]({{ binDir }}/orpheus/OrpheusRoterFaden.pdf)     | RoterFaden.pdf          | 1.6 MB
[Orpheus-B-Scribbles]({{ binDir }}/orpheus/Orpheus-B-Scribbles.pdf) | Orpheus-B-Scribbles.pdf | 26.4 MB
[Fight Controls]({{ binDir }}/orpheus/OrpheusFightControls.pdf)     | FightControls.pdf       | 8.0 MB
[Werdegang eines SC's]({{ binDir }}/orpheus/OrpheusProgression.pdf) | PlayerProgression.pdf   | 6.0 MB
[Gildensystem V1]({{ binDir }}/orpheus/OrpheusGuilds-V1.pdf)        | OrpheusGuilds-V1.pdf    | 12.5 MB
[Gildensystem V2]({{ binDir }}/orpheus/OrpheusGuilds-V2.pdf)        | OrpheusGuilds-V2.pdf    | 26 MB
[NPCs per Guild]({{ binDir }}/phoenix/PhoenixNSCsPerGuild.pdf)      | NSCsPerGuild.pdf        | 8 MB


### Transcripts

* [NPCs per Guild]({{ absLinkBase }}/documents/orpheus/NSCsPerGuild) (Flosha)


<!--<img class="cover" src="{{ mediaLinkBase }}/orpheus/orpheus-2.jpg" alt="Orpheus Aufzeichnungen">-->


<style>
  article {
   padding-bottom: 50px;
   display: grid;
    max-width: 100%;
    padding-right: 20px;
    padding-left: 20px;
  }

  article p {
    max-width: 700px;
  }

  article img {
    max-width: 700px;
  }

  article table {
    border-collapse: collapse;
    margin: 0 auto;
    max-width: 90vw;
    display: block;
    overflow-x: auto;
    width: 100%;
  }

  article td, 
  article th {
    border: 1px solid currentColor;
    padding: 2px 10px;
  }

  article th {
    background: #ac876d47;
  }

  article tr.link td {
    cursor: pointer;
  }

  article tr.link:hover td {
      background: #ac876d24;
  }

  article tr.missing td {
    opacity: 0.5;
  }

  /* @flosha indicated he prefers horizontal scrolling here than dropping columns */
  /* @media (max-width : 750px) {
    article td:nth-child(3),
    article th:nth-child(3) {
      display: none;
    }
  }

  @media (max-width : 500px) {
    article td:nth-child(1),
    article th:nth-child(1),
    article td:nth-child(5),
    article th:nth-child(5) {
      display: none;
    }
  } */
</style>

<script>
  const table = document.querySelector("article table");
  table.classList.add("js");
  const rows = Array.from(table.querySelectorAll("tr"));
  for(let row of rows) {
    const isMissing = row.querySelector("del") != null;
    if (isMissing) {
      row.classList.add("missing");
      continue;
    }
    const link = row.querySelector("a[href]");
    if (link == null) {
      continue;
    }
    row.classList.add("link");
    row.addEventListener("click", () => link.click());
  }
</script>
