---
title: Finster Soundtrack
markdown: true
---

# Finster Soundtrack

## by the Mad Scientists

Extracted from the [Demo](/demos/finster/) by Bloody.  
Two files are missing(!):  
* RELAX.CMF
* ATMOS.CMF


### .CMF                                         

* [DEEP.mp3]({{ audioDir }}/finster/CMF/DEEP.mp3)
* [DEEPER.mp3]({{ audioDir }}/finster/CMF/DEEPER.mp3)
* [EVIL.mp3]({{ audioDir }}/finster/CMF/EVIL.mp3)
* [GHOSTS.mp3]({{ audioDir }}/finster/CMF/GHOSTS.mp3)
* [HISCORE.mp3]({{ audioDir }}/finster/CMF/HISCORE.mp3)
* [MYSTICA.mp3]({{ audioDir }}/finster/CMF/MYSTICA.mp3)
* [SNOW.mp3]({{ audioDir }}/finster/CMF/SNOW.mp3)
* [SPACE01.mp3]({{ audioDir }}/finster/CMF/SPACE01.mp3)
* [TRIUMPH.mp3]({{ audioDir }}/finster/CMF/TRIUMPH.mp3)
* [TWELVE.mp3]({{ audioDir }}/finster/CMF/TWELVE.mp3)
* [WALK.mp3]({{ audioDir }}/finster/CMF/WALK.mp3)
* [WALKING.mp3]({{ audioDir }}/finster/CMF/WALKING.mp3)


### .MOD 

* [BASEKICK.mp3]({{ audioDir }}/finster/MOD/BASEKICK.mp3)
* [INTRO01.mp3]({{ audioDir }}/finster/MOD/INTRO01.mp3)
* [LIV1ED2.mp3]({{ audioDir }}/finster/MOD/LIV1ED2.mp3)
* [LIVTIME3.mp3]({{ audioDir }}/finster/MOD/LIVTIME3.mp3)
* [SPACE02.mp3]({{ audioDir }}/finster/MOD/SPACE02.mp3)



<style>
  article {
   padding-bottom: 50px;
   display: grid;
    max-width: 100%;
    padding-right: 20px;
    padding-left: 20px;
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
