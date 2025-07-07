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

<!-- gridjs + SheetJS -->
<link href="https://unpkg.com/gridjs/dist/theme/mermaid.min.css" rel="stylesheet" />
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<script src="https://unpkg.com/gridjs/dist/gridjs.umd.js"></script>

<h2>MISSE-DB Table</h2>
<div id="excel-table">Loading Excel data...</div>

<style>
#excel-table {
  overflow-x: auto;
  width: 100%;
}

.gridjs-container {
  width: 100% !important;
  max-width: 100% !important;
  box-sizing: border-box;
}

.gridjs-wrapper {
  min-width: 1200px;  /* 원하는 최소 테이블 너비 */
}
</style>

<script>
fetch("{{ site.baseurl }}/assets/data/missedb.xlsx")
  .then(res => res.arrayBuffer())
  .then(buffer => {
    const wb = XLSX.read(buffer, { type: "array" });
    const sheet = wb.Sheets[wb.SheetNames[0]];
    const json = XLSX.utils.sheet_to_json(sheet, { header: 1, raw: false });

    const headers = json[0];
    const data = json.slice(1);

    const container = document.getElementById("excel-table");
    container.innerHTML = "";

    new gridjs.Grid({
      columns: headers,
      data: data,
      sort: true,
      pagination: {
        enabled: true,
        limit: 25
      }
    }).render(container);
  })
  .catch(error => {
    document.getElementById("excel-table").innerText = "Failed to load Excel file.";
    console.error("Excel fetch/render error:", error);
  });
</script>

<div class="download-container">
  <a href="{{ site.baseurl }}/assets/data/missedb.xlsx" download class="download-btn">
    ⬇️ Download Original Excel (.xlsx)
  </a>
</div>

<style>
.download-container {
  display: flex;
  justify-content: center;
  margin: 1em 0;
}
.download-btn {
  padding: 10px 18px;
  font-size: 16px;
  background-color: #007acc;
  color: white;
  border: none;
  border-radius: 6px;
  text-decoration: none;
}
.download-btn:hover {
  background-color: #005fa3;
}
</style>

