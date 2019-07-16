---
test: true
vim: ts=3:nowrap
title: Seting the column position of object lists.
permalink: /test-object-order.html
description: |
   This example show how to set the order of parameters from a list of objects, particularly when
   there is no input data.
---

* [Source webpage of example](https://handsontable.com/docs/7.1.0/tutorial-data-sources.html).
* `startRows` and `startCols` are not working (one row instead of 5), and there are already 4 columns from the `columns` parameter.

<script>
var myData = [];

var container = document.querySelector('#example');

var options = {
	data: myData,
	dataSchema: {id: null, name: {first: null, last: null}, address: null},
	startRows: 5,
	startCols: 4,
	colHeaders: ['ID', 'First Name', 'Last Name', 'Address'],
	columns: [
		{data: 'id'},
		{data: 'name.first'},
		{data: 'name.last'},
		{data: 'address'}
	],
	minSpareRows: 1,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>


