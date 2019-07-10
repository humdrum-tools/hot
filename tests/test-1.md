---
test: true
vim: ts=3:nowrap
title: Basic usage
permalink: /test-1.html
description: |
   This example shows how to create a table given some data in a
   two-dimensional array.  Also note that a license must be given, and that
   the non-commercial license is "non-commercial-and-evaluation".
---

<ul>
<li> <a target="_blank" href="https://handsontable.com/docs/7.1.0/tutorial-quick-start.html">Source page for example</a></li>
<li> <a target="_blank" href="https://handsontable.com/docs/7.1.0/tutorial-license-key.html">Adding license key</a></li>
<li> Note that changes to cells in the table will alter the myData variable.
<li> The first dimension of the data is a row, then the cells are columns (like Humdrum file)
<li> Adding a column will insert nulls into the given array position in the original array.
<li> This example does not allow adding rows.
</ul>

<script>
var myData = [
	['', 'Ford', 'Tesla', 'Toyota', 'Honda'],
	['2017', 10, 11, 12, 13],
	['2018', 20, 11, 14, 13],
	['2019', 30, 15, 12, 13]
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	rowHeaders: true,
	colHeaders: true,
	filters: true,
	dropdownMenu: true,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>



