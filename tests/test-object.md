---
test: true
vim: ts=3:nowrap
title: Loading object lists
permalink: /test-object.html
description: |
   This example shows how to create a spreadsheet from a list of objects.
---

* [Source webpage of example](https://handsontable.com/docs/7.1.0/tutorial-data-sources.html).
* The first row defines the order of the columns.
* If the subsequent rows have extra parameters, they will be ignored
* If the first row contains parameters that the other rows do not, then they will not add the extra parameter
* If empty rows are added, they will add extra parameters set to null for all properties on the first row.

<script>
var myData = [
	{id: 1, name: 'Ted Right', address: '65 Maplewood Ave.'},
	{id: 2, name: 'Frank Honest', address: '1532 23nd St.'},
	{id: 3, name: 'Joan Well', address: '25 Tamra Pl.'},
	{id: 4, name: 'Gail Polite', address: 'Apt. 35b, 142 Main St.'},
	{name: 'Michael Fair', address: 'skid row', id: 5}
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	colHeaders: true,
	minSpareRows: 3,
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>


