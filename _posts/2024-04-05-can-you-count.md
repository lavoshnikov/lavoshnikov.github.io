---
layout: post
title:  "Can you count?"
date:   2024-04-05 00:00:00 +0000
categories: sql
---

Let's have a little sequel quiz today, inspired by what I have seen in a real interview. \
It will be about COUNT(),our favorite hard-worker among aggregate functions. \
Close your IDE or CLI you are using, and try answering yourself first before checking the right answer.

### Quiz

Imagine we have a table like this:
{% highlight sql %}
| num  | 
| ---- | 
|  1   |
|  2   |
|  3   |
|  4   |
| NULL | 
| NULL |
{% endhighlight %}

1. What will you get if you run `SELECT COUNT(*)` from this table?

2. What will you get if you run `SELECT COUNT(num)` from this table? 

3. What will you get if you run `SELECT COUNT('num')` from this table? 

4. What will you get if you run `SELECT COUNT(null)` from this table? 

5. What will you get if you run `SELECT COUNT(#)` from this table? 

<details>
	<summary>
    Click to see the answer #1:
    </summary>
{% highlight sql %}
| count(*) | 
| -------- | 
|     6    |
{% endhighlight %}
</details>
<details>
	<summary>
    Click to see the answer #2:
    </summary>
{% highlight sql %}
| count(num) | 
| ---------  | 
|      4     |
{% endhighlight %}
</details>

<details>
	<summary>
    Click to see the answer #3:
    </summary>
{% highlight sql %}
| count('num') | 
| ------------ | 
|       6      |
{% endhighlight %}
</details>

<details>
	<summary>
    Click to see the answer #4:
    </summary>
{% highlight sql %}
| count(null) | 
| ----------- | 
|      0      |
{% endhighlight %}
</details>

<details>
	<summary>
    Click to see the answer #5:
    </summary>
{% highlight sql %}
-- Error: Parser Error: syntax error at or near ")"
-- LINE 1: select count(#) from nums;
{% endhighlight %}
</details>

### Explanation

Well, first one was pretty obvious, wasn't it? `COUNT(*)` will give you the count of all rows in the table, in this case: 6. \
Pro tip: `COUNT(1)` ,`COUNT(0)` ,`COUNT(-1)` will also give you all rows count: 6. 

`COUNT(num)` counts all non-NULL values in the columns, hence: 4 

`COUNT('num')` will also be 6 because `'num'` is a string constant, so same output is produced as in `COUNT(1)`. 

`COUNT(NULL)` will return 0, as NULLs are ignored. \

`COUNT(#)` is a syntax error.

### Try it yourself
This code snippet can help you reproduce the quiz and play with it yourself:

{% highlight sql %}
create table nums (num int);
insert into nums values (1),(2),(3),(4),(null),(null);
{% endhighlight %}

This is what you get in DuckDB (see my [previous post](https://sequel.blog/tools/2024/04/02/getting-started.html) for installation):  

![DuckDB launched in CLI](/assets/2024-04-05-can-you-count.png)








