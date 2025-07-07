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

The data are a result of NASA’s **MISSE program**, aimed at quantifying the durability of polymers under harsh space conditions such as:

- Ultraviolet radiation  
- Atomic oxygen  
- Extreme thermal cycling

---

This webpage is intended to evolve into the first **integrated database** that consolidates material responses to a range of space environmental factors.Once expanded, it will serve as a reliable resource for:

- **Space materials development**  
- **Design of spacecraft and structural components**
- **Mission planning and long-duration durability assessments**

<h2>MISSE-DB Table</h2>

<!-- 컬럼 선택 영역 -->
<div id="column-selector">Loading columns...</div>

<!-- 테이블 렌더링 영역 -->
<div id="excel-table">Loading Excel data...</div>

<!-- 라이브러리 불러오기 -->
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<link href="https://unpkg.com/gridjs/dist/theme/mermaid.min.css" rel="stylesheet" />
<script src="https://unpkg.com/gridjs/dist/gridjs.umd.js"></script>

<script>
let headers = [];
let data = [];

function renderCheckboxes(headers) {
  const container = document.getElementById("column-selector");
  container.innerHTML = "<strong>Select columns to display:</strong><br>";
  headers.forEach((col, i) => {
    const checkbox = document.createElement("input");
    checkbox.type = "checkbox";
    checkbox.value = i;
    checkbox.checked = true;
    checkbox.id = "col_" + i;

    checkbox.addEventListener("change", updateTable);

    const label = document.createElement("label");
    label.htmlFor = checkbox.id;
    label.textContent = col;

    container.appendChild(checkbox);
    container.appendChild(label);
    container.appendChild(document.createElement("br"));
  });
}

function updateTable() {
  const selectedIndices = headers
    .map((_, i) => document.getElementById("col_" + i))
    .filter(cb => cb.checked)
    .map(cb => parseInt(cb.value));

  const filteredHeaders = selectedIndices.map(i => headers[i]);
  const filteredData = data.map(row => selectedIndices.map(i => row[i]));

  document.getElementById("excel-table").innerHTML = ""; // reset
  new gridjs.Grid({
    columns: filteredHeaders,
    data: filteredData,
    search: true,
    sort: true,
    pagination: {
      enabled: true,
      limit: 10
    }
  }).render(document.getElementById("excel-table"));
}

fetch("{{ site.baseurl }}/assets/data/missedb.xlsx")
  .then(res => res.arrayBuffer())
  .then(buffer => {
    const wb = XLSX.read(buffer, { type: "array" });
    const sheet = wb.Sheets[wb.SheetNames[0]];
    const json = XLSX.utils.sheet_to_json(sheet, { header: 1 });

    headers = json[0];
    data = json.slice(1);

    renderCheckboxes(headers);
    updateTable();
  });
</script>
