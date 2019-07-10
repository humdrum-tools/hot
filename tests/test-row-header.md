---
test: true
vim: ts=3:nowrap
title: Basic usage
permalink: /test-row-header.html
description: |
   This example shows how to create header titles for both columns and rows by using an array of labels in 
   the "colHeaders" and "rowHeaders" parameters instead of "true".
---

<ul>
<li> <a target="_blank" href="https://handsontable.com/docs/7.1.0/tutorial-quick-start.html">Source page for example</a></li>
<li> Add the parameter `colHeaders` with a list of the names for each column.
</ul>

<script>
var myData = [
	[10, 11, 12, 13],
	[20, 11, 14, 13],
	[30, 15, 12, 13]
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	rowHeaders: ['2017', '2018', '2019'],
	colHeaders: ['Ford', 'Tesla', 'Toyota', 'Honda'],
	filters: true,
	dropdownMenu: true,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>



