---
test: true
vim: ts=3:nowrap
title: Loading object lists
permalink: /test-object-function.html
description: |
   This example show how to use functions to fill columns in spreadsheet.
---

* [Source webpage of example](https://handsontable.com/docs/7.1.0/tutorial-data-sources.html).
* This example shows how to use a function to extract nested parameters into a flat list for each row.
* The mapped parameters will travel back to `myData` when changed in the spreadsheet.
* Changing in `myData` will cause them to be displayed in the spreadsheet (but need to refresh somehow).

<script>
var myData = [
	{id: 1, name: {first: "Ted", last: "Right"}, address: ""},
	{id: 2, address: ""}, // HOT will create missing properties on demand
	{id: 3, name: {first: "Joan", last: "Well"}, address: ""}
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	colHeaders: true,
	columns: function(column) {
		var columnMeta = {};
		if (column === 0) {
			columnMeta.data = 'id';
		} else if (column === 1) {
			columnMeta.data = 'name.first';
		} else if (column === 2) {
			columnMeta.data = 'name.last';
		} else if (column === 3) {
			columnMeta.data = 'address';
		} else {
			columnMeta = null;
		}
		return columnMeta;
	},
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>


