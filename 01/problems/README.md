<!---
N.B: This file is formatted for displays larger than 80 columns (156 cols) to
properly format the Markdown table. In future, this might be redone in a LaTeX
image attached, but for now, this is how it is.
-->
### Exercise 1-1: Comparison of running times

For each function *f*(*n*) and time *t* in the following table, determine the
largest size *n* of a problem that can be solved in time *t*, assuming that the
algorithm to solve the problem takes *f*(*n*) microseconds.

### Solution

|               |1 second       |1 minute       |1 hour             |1 day              |1 month            |1 year                 |1 century             |
|:-------------:|--------------:|--------------:|------------------:|------------------:|------------------:|----------------------:|---------------------:|
|lg *n*         |2<sup>1e6</sup>|2<sup>6e7</sup>|2<sup>36e8</sup>   |2<sup>864e8</sup>  |2<sup>25920e8</sup>|2<sup>315360e8</sup>   |2<sup>31556736e8</sup>|
|sqrt(*n*)      |1e12           |36e14          |1296e16            |746496e16          |6718464e18         |994519296e18           |995827586973696e16    |
|*n*            |1e6            |6e7            |36e8               |864e8              |2592e9             |31536e9                |31556736e8            |
|*n* lg *n*     |62746          |2801417        |133378058          |2755147513         |71870856404        |797633893349           |68654697441062        |
|*n*<sup>2</sup>|1000           |7745           |60000              |293938             |1609968            |5615692                |56175382              |
|*n*<sup>3</sup>|100            |391            |1532               |4420               |13736              |31593                  |146677                |
|2<sup>*n*</sup>|19             |25             |31                 |36                 |41                 |44                     |51                    |
|*n*!           |9              |11             |12                 |13                 |15                 |16                     |17                    |
