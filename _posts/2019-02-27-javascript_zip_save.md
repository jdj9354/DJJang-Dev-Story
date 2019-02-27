---
layout: post
title:  "JSZip library - Javascript zip save"
comments: true
categories: javascript
date:   2019-02-27 14:02:00 +0900
---

> ## JSZIP to compress files in javascript

We can make zip data easily using JSZIP.
Import the JSZIP and make it file download using anchor tag.

Here is example code for JSZIP file download

```HTML
<HTML>
<HEAD>
<script type="text/javascript" 
		src="jszip.js"></script>
</HEAD>

<BODY>

	<input type="button" onclick="create_zip()" value="Create Zip"></input>

</BODY>
<SCRIPT>

function create_zip() {
	var zip = new JSZip();
	zip.add("hello1.txt", "Hello First World\n");
	zip.add("hello2.txt", "Hello Second World\n");
	content = zip.generate();

	var link = document.createElement("a");
	link.download = 'captue.zip';
	link.href = "data:application/zip;base64," + content;

	document.body.appendChild(link);
	link.click();

	// Cleanup the DOM
	document.body.removeChild(link);
	delete link;
}

</SCRIPT>
</HTML>
```