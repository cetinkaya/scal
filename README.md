scal
====

scal is a simple wrapper around cal (calendar) tool. It needs ruby to run. 

scal can be used to show several months of a year (or different years) at the same time. What follows is a list of examples to illustrate what you can do with it. We will assume the current month - year is October - 2014. 

* Use "scal april 2014" or "scal April 2014" or "scal 4 2014" or "scal apr 2014" or "scal 2014 april" ... to show calendar for April 2014.

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

* Use "scal 10"  or "scal october" to show the calendar for October of this year. 

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

* You can actually write "scal october current year" or "scal october this year" to show the calendar for October current year.
 
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

* Use "scal next month" to show, well, the calendar for the next month. 

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
    ...

```

