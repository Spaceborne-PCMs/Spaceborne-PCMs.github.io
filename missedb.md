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

## Data Table

<div id="excel-table">Loading Excel data..</div>

<!-- SheetJS JavaScript: Render Excel file -->
<script src="https://cdn.sheetjs.com/xlsx-0.20.0/package/dist/xlsx.full.min.js"></script>
<script>
  fetch("{{ site.baseurl }}/assets/data/missedb.xlsx")
    .then(res => res.arrayBuffer())
    .then(buffer => {
      const wb = XLSX.read(buffer, { type: "array" });
      const sheet = wb.Sheets[wb.SheetNames[0]];
      const html = XLSX.utils.sheet_to_html(sheet);
      document.getElementById("excel-table").innerHTML = html;
    });
</script>
