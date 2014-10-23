scal
====

scal is a simple wrapper around *cal* tool, which is used for displaying calendars in the terminal (see man page of *cal* [here](http://man7.org/linux/man-pages/man1/cal.1.html)). 

scal can be used for displaying calendars for several months of a year (or different years). The description for the month(s)-year(s) is given as arguments to scal. For instance, `scal jan feb 2015, jan feb 2016` shows the calendars for January and February of 2015 and 2016. scal understands expressions like "april next year" and "last month", for instance, `scal next month` will display next month's calendar. scal also doesn't care (well, most of the time) about the order you put the year and the numeric value for the month: both `scal 1 2015` and `scal 2015 1` will display the calendar for January 2015.

scal needs the command line utility *cal* and [Ruby](https://www.ruby-lang.org) to run.

scal passes options of the form -o or --option to *cal*. 

What follows is a list of examples to illustrate what you can do with scal. 

### Examples

We will assume that the current month - year is October - 2014. 

* Use `scal april 2014` or `scal April 2014` or `scal 4 2014` or `scal apr 2014` or `scal 2014 april` ... to show the calendar for April 2014.

```sh
$ scal april 2014
     April 2014     
Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6 
 7  8  9 10 11 12 13 
14 15 16 17 18 19 20 
21 22 23 24 25 26 27 
28 29 30             
```

* Use `scal 10`  or `scal october` to show the calendar for October this year. 

```sh
$ scal 10
    October 2014    
Mo Tu We Th Fr Sa Su
       1  2  3  4  5 
 6  7  8  9 10 11 12 
13 14 15 16 17 18 19 
20 21 22 23 24 25 26 
27 28 29 30 31       
```

* You can actually write `scal october current year` or `scal october this year` to show the calendar for October this year.
 
```sh
$ scal october this year
    October 2014    
Mo Tu We Th Fr Sa Su
       1  2  3  4  5 
 6  7  8  9 10 11 12 
13 14 15 16 17 18 19 
20 21 22 23 24 25 26 
27 28 29 30 31       
```

* Use `scal next month` to show, well, the calendar for the next month. 

```sh
$ scal next month
    November 2014   
Mo Tu We Th Fr Sa Su
                1  2 
 3  4  5  6  7  8  9 
10 11 12 13 14 15 16 
17 18 19 20 21 22 23 
24 25 26 27 28 29 30 
```

* It is possible to see calendars for multiple months.   

```sh
$ scal april june
    April 2014     
Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6 
 7  8  9 10 11 12 13 
14 15 16 17 18 19 20 
21 22 23 24 25 26 27 
28 29 30             
                     
     June 2014     
Mo Tu We Th Fr Sa Su
                   1 
 2  3  4  5  6  7  8 
 9 10 11 12 13 14 15 
16 17 18 19 20 21 22 
23 24 25 26 27 28 29 
30                   
```

* Use a comma to separate different years.  

```sh
$ scal april may june 2014, april may june 2015
    April 2014
     ...
     
    May 2014
     ...
     
    June 2014
     ...
     
    April 2015
     ...
     
    May 2015
     ...
     
    June 2015
     ...
```

### Quirks (features?)

* Assuming it is October 2014 now, `scal next month next year` will show the calendar for November 2015, and `scal last month next year` will show September 2015. 

```sh
$ scal next month next year
    November 2015   
Mo Tu We Th Fr Sa Su
                   1 
 2  3  4  5  6  7  8 
 9 10 11 12 13 14 15 
16 17 18 19 20 21 22 
23 24 25 26 27 28 29 
30
```

```sh
$ scal last month next year
   September 2015   
Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6 
 7  8  9 10 11 12 13 
14 15 16 17 18 19 20 
21 22 23 24 25 26 27 
28 29 30     
```

* Both `scal 2 2014` and `scal 2014 2` show the calendar of February 2014, because 2014 must clearly represent the year here. How about `scal 2 12` and `scal 12 2`?  Well, in such cases (if there is ambiguity on whether a number represents a year or a month), if there are only two numbers, then the second number represents the year. So `scal 12 2` shows the calendar for December 2 (year 2). 

```sh
$ scal 12 2
     December 2     
Mo Tu We Th Fr Sa Su
             1  2  3 
 4  5  6  7  8  9 10 
11 12 13 14 15 16 17 
18 19 20 21 22 23 24 
25 26 27 28 29 30 31
```

* Note that when we use `scal 13 2`, 13 cannot be the representation of a month so it must be the year 13. `scal 13 2` shows the calendar for February 13. 

```sh
$ scal 13 2
     February 13    
Mo Tu We Th Fr Sa Su
       1  2  3  4  5 
 6  7  8  9 10 11 12 
13 14 15 16 17 18 19 
20 21 22 23 24 25 26 
27 28
```

* If we have multiple numbers larger than 12, they all must represent years. But scal takes only the last one (in the order they are given) into consideration. So `scal feb 2014 2015 2016` shows the calendar for February 2016 and `scal feb 2015 2016 2014` shows the calendar for February 2014.

```sh
$ scal feb 2014 2015 2016
    February 2016   
Mo Tu We Th Fr Sa Su
 1  2  3  4  5  6  7 
 8  9 10 11 12 13 14 
15 16 17 18 19 20 21 
22 23 24 25 26 27 28 
29
```

```sh
$ scal feb 2015 2016 2014
    February 2014   
Mo Tu We Th Fr Sa Su
                1  2 
 3  4  5  6  7  8  9 
10 11 12 13 14 15 16 
17 18 19 20 21 22 23 
24 25 26 27 28
```

* To see February of 2014, 2015, and 2016, you can use `scal feb 2014, feb 2015, feb 2016`. 

```sh
$ scal feb 2014, feb 2015, feb 2016
    February 2014   
Mo Tu We Th Fr Sa Su
                1  2 
 3  4  5  6  7  8  9 
10 11 12 13 14 15 16 
17 18 19 20 21 22 23 
24 25 26 27 28       
                     
    February 2015   
Mo Tu We Th Fr Sa Su
                   1 
 2  3  4  5  6  7  8 
 9 10 11 12 13 14 15 
16 17 18 19 20 21 22 
23 24 25 26 27 28    
                     
    February 2016   
Mo Tu We Th Fr Sa Su
 1  2  3  4  5  6  7 
 8  9 10 11 12 13 14 
15 16 17 18 19 20 21 
22 23 24 25 26 27 28 
29
```
