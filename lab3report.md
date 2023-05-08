# Researching Commands

The command I chose is ```grep```. 

---
### 4 Interesting Command-line Options/Alternate ways to use the Command:
---
1. ```grep -i``` : Searches for pattern while ignoring uppercase and lowercase. 

To find this command, I used ChatGPT and [this link to wikibooks.](https://en.wikibooks.org/wiki/Grep)

##### **Example 1**
```
$ grep -i "DOWNREGULATED"  technical/biomed/rr74.txt
```
```
        metabolite levels, if NOS was downregulated in the systemic
        NOS was downregulated, but did observe a decrease in
```
This searches for the string "DOWNREGULATED" in rr74.txt but ignores the fact that it is written in uppercase. This still prints out the lines with "downregulated" in lowercase. This is useful because without -i, it can leave out a lot of lines that have the information you wanted to find. 

##### **Example 2**
```
$ grep -i "buckinghamshire, england"  technical/biomed/rr73.txt
```
```
            Little Chalfont, Buckinghamshire, England).
```
This searches for the string which is the name of a country location which should be capitalized, but -i ignores uppercase/lowercase so the command still returns the line with this string. This is useful because without -i, it can leave out a lot of lines that have the information you wanted.

---
2. ```grep -n``` : Searches for and displays matching lines with line numbers. 

To find this command, I used ChatGPT and [this link to wikibooks.](https://en.wikibooks.org/wiki/Grep)

##### **Example 1**
```
$ grep -n "synthase" technical/biomed/rr74.txt
```
```
418:        eNOS = endothelial nitric oxide synthase; iNOS =
419:        inducible nitric oxide synthase; nNOS = neuronal nitric
420:        oxide synthase; NO = nitric oxide; NOS = nitric oxide
421:        synthase; PBS = phosphate-buffered saline; PCR = polymerase
```
This searches for the string "synthase" in the rr74.txt file and prints the lines. It also displays the line numbers where the string is found. This is useful because if we ever have a huge text file and want to find a line number, this makes it easy. 

##### **Example 2**
```
$ grep -n "temperature" technical/biomed/rr73.txt
```
```
327:        temperature for 1 hour, then exposed to primary
```
This searches for the string "temperature" in the rr73.txt file and prints the line. It also displays the line number where "temperature" is found. This is useful because if we ever have a huge text file and want to find a line number, this makes it easy. 

---
3. ```grep -e``` : Specifies one/multiple search patterns. 

To find this command, I used ChatGPT and [this link to wikibooks.](https://en.wikibooks.org/wiki/Grep)

##### **Example 1**
```
$ grep -e "Introduction" technical/biomed/rr73.txt
```
```
        Introduction
```
This prints all lines where "Introduction" can be found in rr73.txt. This is useful because we are able to search for multiple patterns in one command instead of writing many commands. 

##### **Example 2**
```
$ grep -e "Intro" -e "Three-dimensional" technical/biomed/rr73.txt
```
```
        Introduction
        Three-dimensional (3D) collagen gel culture has been
```
This finds multiple patters which are "Intro" and "Three-dimensional" in rr73.txt. This is useful because we are able to search for multiple patterns in one command instead of writing many commands. 

---
4. ```grep -h``` : Searches for pattern within multiple files. 

To find this command, I used ChatGPT and [this link to wikibooks.](https://en.wikibooks.org/wiki/Grep)

##### **Example 1**
```
$ grep -h "Conclusion"  technical/biomed/rr73.txt technical/biomed/rr74.txt    
```
```
        Conclusion
        Conclusion
```
This command searches for the string "Conclusion" in both rr73.txt and rr74.txt and prints their lines. This is useful because we can search through multiple files in one command instead of writing multiple commands. 

##### **Example 2**
```
$ grep -h "medium"  technical/biomed/rr73.txt technical/biomed/rr74.txt
```
```
          9]. For long-term co-culture, the medium was changed
          medium.
          medium, as identified at the molecular weights of 72 kDa
          incubation time, MMP-2 present in culture medium
```
This searches for "medium" and prints each line where medium is found in both rr73.txt and rr74.txt files. It kept checking one file and then the other file to print all of the lines with the string. This is useful because we can search through multiple files in one command instead of writing multiple commands. 


