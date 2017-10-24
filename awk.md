#### From backreference idiomatic awk guide:
```
awk '{if ($0 ~ /pattern/) print $0}' file # can be simplified to below
awk '$0 ~ /pattern/ { print $0 }' file
awk '$0 ~ /pattern/ { print }' file # print implicitly prints $0
awk '$0 ~ /pattern/' file # if condition is matched default behavior is print
awk '/pattern/' file # regex implicitly compared to $0
```

#### Fun examples of the above ideas
```
awk '$0="Line #" NR $0 ":"' # adds line numbers
awk '!a[$0]++' # removes duplicate lines (returns false if undefined, then increments to val of 1 which will evaluate true and drop all other lines)
awk 'ORS=NR % 10 ? FS : RS' # concatenates every 10 lines into a row
```

#### Using AWK vars:
```
# awk groups files into records and 
NR # total number of records processed by AWK
awk 'NR==FNR && NR > 1 {a[$0]=1} NR!=FNR && !a[$0]' F1 F2 # print all lines from F2 NOT included in F1, except for the first line of F1 (which we consider a header)
```

#### Sources:
[Idiomatic AWK](http://backreference.org/2010/02/10/idiomatic-awk/)

[Arrays](http://kirste.userpage.fu-berlin.de/chemnet/use/info/gawk/gawk_12.html)

[Built-in variables](https://www.gnu.org/software/gawk/manual/html_node/Built_002din-Variables.html)
