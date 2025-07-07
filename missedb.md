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

<!-- 스타일 및 라이브러리 -->
<link href="https://unpkg.com/gridjs/dist/theme/mermaid.min.css" rel="stylesheet" />
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<script src="https://unpkg.com/gridjs/dist/gridjs.umd.js"></script>

<h2>MISSE-DB Table</h2>

<!-- 컬럼 선택 영역 -->
<div id="column-selector">Loading columns...</div>

<!-- 엑셀 다운로드 버튼 -->
<button id="download-btn">Download Selected Table (.xlsx)</button>

<!-- 테이블 표시 -->
<div id="excel-table">Loading Excel data...</div>

<script>
let headers = [];
let data = [];
let selectedIndices = [];

function renderCheckboxes(headers) {
  const container = document.getElementById("column-selector");
  container.innerHTML = "<strong>Select columns:</strong><br>";

  headers.forEach((col, i) => {
    const checkbox = document.createElement("input");
    checkbox.type = "checkbox";
    checkbox.value = i;
    checkbox.id = "col_" + i;
    checkbox.checked = true;

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
  // 선택된 컬럼 인덱스 확인
  selectedIndices = headers.map((_, i) => {
    const cb = document.getElementById("col_" + i);
    return cb && cb.checked ? i : null;
  }).filter(i => i !== null);

  const selectedHeaders = selectedIndices.map(i => headers[i]);
  const selectedData = data.map(row => selectedIndices.map(i => row[i]));

  // 기존 테이블 제거 후 다시 그리기
  document.getElementById("excel-table").innerHTML = "";
  new gridjs.Grid({
    columns: selectedHeaders,
    data: selectedData,
    search: true,
    sort: true,
    pagination: { enabled: true, limit: 10 }
  }).render(document.getElementById("excel-table"));
}

function downloadExcel() {
  const selectedHeaders = selectedIndices.map(i => headers[i]);
  const selectedData = data.map(row => selectedIndices.map(i => row[i]));
  const sheetData = [selectedHeaders, ...selectedData];

  const ws = XLSX.utils.aoa_to_sheet(sheetData);
  const wb = XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb, ws, "MISSE-DB");

  XLSX.writeFile(wb, "missedb-selected.xlsx");
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

document.getElementById("download-btn").addEventListener("click", downloadExcel);
</script>

