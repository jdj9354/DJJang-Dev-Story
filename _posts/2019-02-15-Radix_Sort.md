---
layout: post
title:  "Radix Sort"
comments: true
categories: algorithm
date:   2019-02-15 05:50:00 +0900
---

> # Radix Sort

> ## What is Radix sort?
<pre>
Radix sort is a like Dictionary Search.
Radix sort sorts items based on number of digits. It sorts items from low digit.

Radix sort can implemented with Queue.
Sorting Process is very simple.

1. Prepare 10 Queues in order to insert.
2. From low digit, insert items into queue which is indexed on digit.
3. Pop items from the queue fron low digit sequentially.
4. Iterate step 2,3 Until digit value is reached to max value
</pre>

> ## Example

<pre>
Here is example
125,383,274,96,0,9,81,72

Insert into each queue based on first digit.
</pre>

|Queue|Data|
|---|---|
|0|0|
|1|81|
|2|72|
|3|383|
|4|274|
|5|125|
|6|96|
|7||
|8||
|9|9|

Pop : 0,81,72,383,274,125,96,9

<pre>
Second digit
</pre>

|Queue|Data|
|---|---|
|0|0,9|
|1||
|2|125|
|3||
|4||
|5||
|6||
|7|72,274|
|8|81,383|
|9|96|

Pop : 0,9,125,72,274,81,383,96

<pre>
Third digit
</pre>

|Queue|Data|
|---|---|
|0|0,9,72,81,96|
|1|125|
|2|274|
|3|383|
|4||
|5||
|6||
|7||
|8||
|9||

Pop : 0,9,72,81,96,125,274,383

> ## Time Complexity
Although Radix sort need additional Memory, its Time Complexity is very good.
In case of integer, it is very fast.

|Time Complexity|Space Complexity|
|---|---|
|O(kn)|O(k+n)

<pre>
n : The number of Elements
k : The number of bits require to present largest element
</pre>

> ## Radix sort for C/C++

```C++
#include <stdio.h>

void RadixSort(int data[], int N);

void main() {
	int data[8] = { 125,383,274,96,0,9,81,72 };
	int N = 8; //Number of elements
	
	RadixSort(data, N);

	for (int i = 0; i < N; i++)
		printf("%d\n", data[i]);
}

void RadixSort(int data[], int N) {
	int max = -1; //Max Value
	int digit = 1; //Digit


	//Find max Value
	for (int i = 0; i < N; i++) {
		if (data[i] >= max)
			max = data[i];
	}



	while (max / digit > 0) {

		//Create queue
		int** queue = new int*[10];
		for (int i = 0; i < 10; i++)
			queue[i] = new int[N];
		int queueIdx[10] = { 0, };

		//Insert into queue
		for (int i = 0; i < N; i++) {
			int idx = (data[i] / digit) % 10;

			queue[idx][queueIdx[idx]++] = data[i];
		}
		
		// Pop from queue
		int dataCount = 0;

		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < queueIdx[i];j++)
				data[dataCount++] = queue[i][j];
		}

		//RemoveQueue
		for (int i = 0; i < 10; i++)
			delete queue[i];
		delete queue;

		digit *= 10;
	}
}
```
