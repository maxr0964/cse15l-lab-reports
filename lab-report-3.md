# Lab Report 3 - Researching Grep
**Function 1 - Counting the Number of Matches**
* To count the number of matches, use <code>grep -c</code>
* For example, counting the number of matches for "Lucayans" in ./written_2:
```
grep -r -l -Z "Lucayans" written_2 | xargs -r -0 grep -c "Lucayans"
```
* This produces the following result:
```
2
```
* Another example is counting the number of <code>.txt</code> files in ./written_2:
```
find written_2 | grep -c ".txt"
```
* This produces the following result:
```
224
```

