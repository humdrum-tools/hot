---
test: true
vim: ts=3:nowrap
title: Colorized kern example
permalink: /test-colorize.html
---

<style>
  .ace_gutter {background: #fbf1d3;color: #9191cf}
  .ace_print-margin {width: 1px;background: #e8e8e8}
  .ace_cursor {color: black}
  .ace_marker-layer .ace_selection {background: rgba(7, 54, 67, 0.09)}
  .ace_selection.ace_start {box-shadow: 0 0 3px 0px #FDF6E3;}
  .ace_marker-layer .ace_step {background: rgb(255, 255, 0)}
  .ace_marker-layer .ace_bracket {margin: -1px 0 0 -1px;border: 1px solid rgba(147, 161, 161, 0.50)}
  .ace_marker-layer .ace_active-line {background: #EEf3D5}
  .ace_gutter-active-line {background-color : #EDE5C1}
  .ace_marker-layer .ace_selected-word {border: 1px solid #073642}
  .ace_invisible {color: rgba(147, 161, 161, 0.50)}
  .ace_universal {color: green; background: rgba(255,0,0,0.25)}
  .ace_bibliographic {color: green}
  .ace_filter {color: limegreen}
  .ace_filter.ace_used {color: olive}
  .ace_exinterp {color: red}
  .ace_terminator {color: red}
  .ace_manip {color: magenta}
  .ace_interp {color: darkviolet}
  .ace_label {color: darkviolet; background: rgba(75,0,130,0.3)}
  .ace_comment {color: #2fc584}
  .ace_unknown {color: darkgoldenrod}
  .ace_comment.ace_global {color: blue}
  .ace_comment.ace_layout {color: orange}
  .ace_barline {color: gray; background: rgba(0, 0, 0, 0.06) !important}
  .ace_invalid.ace_space {background-color: blue}
  .ace_kern.ace_note {color: black; font-weight:bold}
  .ace_kern.ace_other {color: brown}
  .ace_kern.ace_duration {color: gray}
  .ace_dot {color: #bbb}
  .ace_fold {background-color: #268BD2;border-color: #586E75}
})

</style>

<style>
.handsontable {
	font-family: Monaco, Menlo, "Ubuntu Mono", Consolas, source-code-pro, monospace !important;
}

.wtHolder thead > tr th {
	text-align: left;
}

.handsontable td {
	border: 0;
}

</style>

<ul>
<li>Krn example</li>
</ul>

<div class="d-none" id="source">
{% include test.krn %}
</div>


<script>

function applyAceClasses() {
	var cells = document.querySelectorAll(".htCore tr td");
	for (var i=0; i<cells.length; i++) {
		applyAceClass(cells[i]);
	}
}

function applyAceClass(element) {
	if (!element) {
		return;
	}
	var text = element.textContent;
	if (text.match(/^\*\*/)) {
		element.classList.add("ace_exinterp");
	} else if (text.match(/^\*/)) {
		element.classList.add("ace_interp");
	} else if (text.match(/^\!\!\![^:]+:/)) {
		element.classList.add("ace_bibliographic");
	} else if (text.match(/^\!\!/)) {
		element.classList.add("ace_global");
	} else if (text.match(/^\!/)) {
		element.classList.add("ace_comment");
	} else if (text.match(/^=/)) {
		element.classList.add("ace_barline");
	} else if (text === ".") {
		element.classList.add("ace_dot");
	}
}


document.addEventListener("DOMContentLoaded", function() {
	observeHotContent();
});


//////////////////////////////
//
// observeHotContent --
//

function observeHotContent() {
	var content = document.querySelector("#example");
	if (!content) {
		return;
	}
	observer = new MutationObserver(applyAceClasses);
	observer.observe(content, { childList: true, subtree: true });
}


</script>

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
	rowHeaders: true,
	colHeaders: ['kern', '', 'kern', '', 'dynam'],
	filters: false,
	dropdownMenu: false,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>
