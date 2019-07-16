---
test: true
vim: ts=3:nowrap
title: Krn example
permalink: /test-krn.html
---

<ul>
<li>Krn example</li>
</ul>

<div class="d-none" id="source">
{% include test.krn %}
</div>

<script>
var myData = document.getElementById("source").innerText.trim()
    .split("\n")
    .map(function(l) { return l.trim(); })
    .filter(function(l) { return l.length > 0; })
    .map(function(l) { return l.split("\t"); }),
   cols = myData.reduce(function(p, row) { return Math.max(row.length, p); }, 0),
   merge = myData.reduce(function(m, row, i) {
     if (row.length > 0 && row[0].substring(0, 2) === "!!") {
       m.push({
         row: i,
         col: 0,
         colspan: cols,
         rowspan: 1
       });
     } else {       
       var p = 0, e;
       while ((e = row.indexOf("", p)) > 0) {
         s = e - 1;
         e++;
         while (e < row.length && row[e] === "") e++;
         m.push({
          row: i,
          col: s,
          colspan: e - s,
          rowspan: 1
         });
         p = e;
       };
     };
     return m;
    }, []);

var container = document.querySelector('#example');

var options = {
	data: myData,
  minCols: cols,
  mergeCells: merge,
/*	rowHeaders: false,
	colHeaders: false,
	filters: false,
	dropdownMenu: true, */
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>
