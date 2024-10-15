---
title: Phoenix Docs
markdown: true
---

![Phoenix Pitch Logo]({{ imagesRoot }}/documents/phoenix/phoenix-dark.jpg)

Incomplete collection of Phoenix documents written from 1997-07.1999.

 Chapter | Topic                                                                                | File name                                 | Author | Date 
---------|--------------------------------------------------------------------------------------|-------------------------------------------|--------|------------
 A-1     | [Leveldesign]({{ binDir }}/Phoenix_A1_Leveldesign.pdf)                               | `Phoenix_A1_Leveldesign.doc`              | Mike   | 20.07.1999 
 A-2     | [Items, Objects, Events]({{ binDir }}/Phoenix_A2_ItemsObjectsEvents.pdf)             | `Phoenix_A2_ItemsObjectsEvents.doc`       | Mario  | 12.07.1999 
         |                                                                                      |                                           |        |            
 B-1     | [Attributes, Talents, Actions]({{ binDir }}/Phoenix_B1_AttributesTalentsActions.pdf) | `Phoenix_B1_AttributesTalentsActions.doc` | Alex   | 21.07.1999 
 B-2     | [Combat]({{ binDir }}/Phoenix_B2_Combat.pdf)                                         | `Phoenix_B2_Combat.doc`                   | Mike   | 18.07.1999 
 B-3     | [Magic]({{ binDir }}/Phoenix_B3_Magic.pdf)                                           | `Phoenix_B3_Magic.doc`                    | Alex   | 18.07.1999 
 B-4     | [Learning]({{ binDir }}/Phoenix_B4_Learning.pdf)                                     | `Phoenix_B4_Learning.doc`                 | Mike   | 06.07.1999 
         |                                                                                      |                                           |        |            
 C-1     | [~~AI~~]({{ binDir }}/Phoenix_C1_AI.pdf)                                             | ~~`Phoenix_C1_AI.doc`~~                   | Mike   | file lost
 C-2     | [Monsters]({{ binDir }}/Phoenix_C2_Monsters.pdf)                                     | `Phoenix_C2_Monsters.doc`                 | Alex   | 18.07.1999 
         |                                                                                      |                                           |        |            
 D-1     | [~~Story & Background~~]({{ binDir }}/Phoenix_D1_Story.pdf)                          | ~~`Phoenix_D1_Story.doc`~~                | Mike   | file lost
 D-2     | [Tactical Elements]({{ binDir }}/Phoenix_D2_TacticalElements.pdf)                    | `Phoenix_D2_TacticalElements.doc`         | Mike   | 28.06.1999 
         |                                                                                      |                                           |        |            
 E-1     | [Menu UI]({{ binDir }}/Phoenix_E1_MenuUI.pdf)                                        | `Phoenix_E1_MenuUI.doc`                   | Alex   | 21.07.1999 
 E-2     | [Effects]({{ binDir }}/Phoenix_E2_Effects.pdf)                                       | `Phoenix_E2_Effects.doc`                  | Kai    | 13.07.1999 
 E-3     | [Technical]({{ binDir }}/Phoenix_E3_Technical.pdf)                                   | `Phoenix_E3_Technical.doc`                | Stefan | 06.07.1999 
         |                                                                                      |                                           |        |            
 ???     | [Items reference]({{ binDir }}/Referenz_Items.pdf)                                   | `Referenz_Items.doc`                      | Mario  | 07.07.1999 

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