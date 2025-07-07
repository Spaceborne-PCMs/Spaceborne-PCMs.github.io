---
title: MISSE-DB
layout: template
filename: missedb
permalink: /missedb
---

# MISSE-DB (Database)

**MISSE-DB (Database)** serves as a comprehensive archive of **polymer material exposure data** from the **Materials International Space Station Experiment (MISSE 1–8)** missions, which tested various samples on the exterior of the International Space Station (ISS).

For each material sample, the database provides detailed information including:

- **Deployment and retrieval dates**  
- **Total exposure duration** in the ISS space environment (up to 3.96 years)  
- **Erosion yield values** (e.g., 9.14E-24 cm³/atom)

The data are a result of NASA’s **MISSE program**, aimed at quantifying the durability of polymers under harsh space conditions such as ultraviolet radiation, atomic oxygen, and extreme thermal cycling

---

This webpage is intended to evolve into the first **integrated database** that consolidates material responses to a range of space environmental factors.Once expanded, it will serve as a reliable resource for:

- **Space materials development**  
- **Design of spacecraft and structural components**
- **Mission planning and long-duration durability assessments**

<!-- 스타일 및 라이브러리 -->
<link href="https://unpkg.com/gridjs/dist/theme/mermaid.min.css" rel="stylesheet" />
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<script src="https://unpkg.com/gridjs/dist/gridjs.umd.js"></script>

<h2>MISSE-DB Table</h2>

<!-- 다운로드 버튼 -->
<a href="{{ site.baseurl }}/assets/data/missedb.xlsx" download class="btn">
  Download Original Excel (.xlsx)
</a>

<!-- 테이블 표시 -->
<div id="excel-table">Loading Excel data...</div>

<script>
fetch("{{ site.baseurl }}/assets/data/missedb.xlsx")
  .then(res => res.arrayBuffer())
  .then(buffer => {
    const wb = XLSX.read(buffer, { type: "array" });
    const sheet = wb.Sheets[wb.SheetNames[0]];
    const json = XLSX.utils.sheet_to_json(sheet, { header: 1, raw: false });

    const headers = json[0];
    const data = json.slice(1);

    new gridjs.Grid({
      columns: headers,
      data: data,
      sort: true,
      pagination: {
        enabled: true,
        limit: 15
      }
    }).render(document.getElementById("excel-table"));
  });
</script>

