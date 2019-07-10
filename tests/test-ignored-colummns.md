---
test: true
vim: ts=3:nowrap
title: Ignored columns
permalink: /test-ignored-columns.html
description: |
   This example shows how to ignore columns of input data when creating a spreadsheet.
---

* [Source webpage of example](https://handsontable.com/docs/7.1.0/tutorial-data-sources.html).
* This seems to be more "ignoring" rather than "hidden".
* Notice that the second column of `myData`, "Tesla", is not shown in the table.
* The column is hidden by skipping over that column position in the `columns` parameter list.
* The `minSpareRows` parameter will add extra rows to the end of the spreadsheet.
* The column remains in `myData`.

<script>
var myData = [
	['', 'Tesla', 'Nissan', 'Toyota', 'Honda', 'Mazda', 'Ford'],
	['2017', 10, 11, 12, 13, 15, 16],
	['2018', 11, 12, 13, 14, 16, 17],
	['2019', 12, 13, 14, 15, 17, 18],
	['2020', 13, 14, 15, 16, 18, 19],
	['2021', 14, 15, 16, 17, 19, 20]
];

var container = document.querySelector('#example');

var options = {
	data: myData,
	colHeaders: true,
	minSpareRows: 5,
	columns: [
		{data: 0},
		{data: 2},
		{data: 3},
		{data: 4},
		{data: 5},
		{data: 6}
	],
	licenseKey: 'non-commercial-and-evaluation'
};

var hot = new Handsontable(container, options);
</script>


