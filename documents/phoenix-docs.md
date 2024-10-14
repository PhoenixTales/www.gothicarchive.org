---
title: Phoenix Docs
markdown: true
---

![Phoenix Pitch Logo]({{ imagesRoot }}/documents/phoenix/phoenix-dark.jpg)

Incomplete collection of Phoenix documents written from 1997-07.1999.

* [Phoenix_Main.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix Main.doc) [18.07.1999] (only table of contents)
* [Phoenix_A1_Leveldesign.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_A1_Leveldesign.doc) [20.07.1999]
* [Phoenix_A2_ItemsObjectsEvents.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_A2_ItemsObjectsEvents.doc) [12.07.1999]
<!-- * Phoenix_A3_ItemsObjectsEvents.doc [10.07.1999] [Duplicate] -->

* [Phoenix_B1_AttributesTalentsActions.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_B1_AttributesTalentsActions.doc) [21.07.1999]
* [Phoenix_B2_Combat.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_B2_Combat.doc) [18.07.1999]
* [Phoenix_B3_Magic.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_B3_Magic.doc) [18.07.1999]
* [Phoenix_B4_Learning.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_B4_Learning.doc) [06.07.1999]

* Phoenix_C1_AI.doc [lost]
* [Phoenix_C2_Monsters.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_C2_Monsters.doc) [18.07.1999]

* Phoenix_D1_Story.doc [lost]
* [Phoenix_D2_TacticalElements.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_D2_TacticalElements.doc) [28.06.1999]

* [Phoenix_E1_MenuUI.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_E1_MenuUI.doc) [21.07.1999]
* [Phoenix_E2_Effects.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_E2_Effects.doc) [13.07.1999]
* [Phoenix_E3_Technical.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Phoenix_E3_Technical.doc) [06.07.1999]

* [Referenz_Items.doc]({{ binRoot }}/documents/phoenix/PhoenixDokumentationen/Referenz_Items.doc) [07.07.1999]

<script>
  // in online mode, add preview links using the anonymous google drive preview functionality
  if (window.location.hostname == "gothicarchive.org") {
    const docLinks = Array.from(document.querySelectorAll("a[href$='.doc']"));
    for(var docLink of docLinks) {
      const previewLink = document.createElement("a");
      previewLink.innerText = " (preview)";
      previewLink.href = "https://docs.google.com/gview?embedded=true&url=" + docLink.href;
      docLink.after(previewLink);
    }
  }
</script>
