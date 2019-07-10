---
test: true
vim: ts=3:nowrap
title: Basic usage
permalink: /test-header.html
description: |
   This example shows how to create header titles by using an array of labels in 
   the "colHeaders" parameter instead of "true".
---

<ul>
<li> <a target="_blank" href="https://handsontable.com/docs/7.1.0/tutorial-quick-start.html">Source page for example</a></li>
<li> Add the parameter `colHeaders` with a list of the names for each column.
</ul>

<script>
var myData = [
	['2017', 10, 11, 12, 13],
	['2018', 20, 11, 14, 13],
	['2019', 30, 15, 12, 13]
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	rowHeaders: true,
	colHeaders: ['Year', 'Ford', 'Tesla', 'Toyota', 'Honda'],
	filters: true,
	dropdownMenu: true,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>



