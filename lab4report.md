# Lab Report 4

**Step 4:** Logging into ieng6. 
I pressed ```<enter>``` after sshing and typing in my password. 
```
PS C:\Users\ltsamaan> ssh cs15lsp23bg@ieng6.ucsd.edu
```
```<enter>```
```
Password: 
Last login: Wed May 17 16:13:46 2023 from its-cseb260-25.ucsd.edu
quota: Cannot resolve mountpoint path /home/linux/staff/.snapshot/hourly.2023-05-11_1601: Stale file handle
Hello cs15lsp23bg, you are currently logged into ieng6-201.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   16:20:01   25  2.33,   2.66,   2.86 
ieng6-202   16:20:01   26  20.71,  21.33,  15.43
ieng6-203   16:20:01   37  12.87,  14.80,  16.31
```
---
**Step 5:** Cloning fork of repository. 
```
[cs15lsp23bg@ieng6-201]:~:504$ git clone https://github.com/ucsd-cse15l-s23/lab7
```
```<enter>```
```
Cloning into 'lab7'...
remote: Enumerating objects: 41, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 41 (delta 2), reused 6 (delta 2), pack-reused 35
Receiving objects: 100% (41/41), 372.81 KiB | 1.42 MiB/s, done.
Resolving deltas: 100% (14/14), done.
[cs15lsp23bg@ieng6-201]:~:505$ ls
Desktop    Downloads  Pictures  Templates  docsearch  perl5         tutor  
Documents  Music      Public    Videos     lab7       stringsearch  wavelet
```
---
**Step 6:** Run failing tests. 
```
[cs15lsp23bg@ieng6-201]:~:506$ cd lab7
```
```<enter>```
```
[cs15lsp23bg@ieng6-201]:lab7:507$ ls
```
```<enter>```
ListExamples.java  ListExamplesTests.java  lib  test.sh
```
[cs15lsp23bg@ieng6-201]:lab7:508$ vim test.sh 
```
```<enter>```

* To open vim to find the javac and java commands, I did vim test.sh. Then I highlighted the text and pressed ```<Ctrl> <c>```. To exit vim after copying, I pressed ```<esc> <:> < q> <!>``` to quit without saving changes. I copied them so I could paste them into terminal using ```<Ctrl> <v>```.
* 
![image](vim.PNG)
        
*Failure:*
```
[cs15lsp23bg@ieng6-201]:lab7:510$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
```
```<enter>```
```
[cs15lsp23bg@ieng6-201]:lab7:511$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```
```<enter>```
```
JUnit version 4.13.2
..E
Time: 0.549
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at java.base/java.util.Arrays.copyOf(Arrays.java:3512)
        at java.base/java.util.Arrays.copyOf(Arrays.java:3481)
        at java.base/java.util.ArrayList.grow(ArrayList.java:237)
        at java.base/java.util.ArrayList.grow(ArrayList.java:244)
        at java.base/java.util.ArrayList.add(ArrayList.java:454)
        at java.base/java.util.ArrayList.add(ArrayList.java:467)
        at ListExamples.merge(ListExamples.java:42)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```
---
**Step 7:** Fix code to make tests pass. 

*Corrected code in vim:*
```
[cs15lsp23bg@ieng6-201]:lab7:513$ vim ListExamples.java    
```
```<enter>```
```
  
  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }
```
* To change index1 to index2, I pressed ```<j>``` 42 times to get to the line with index1, ```<i>``` to change to insert mode, ```<l>``` 12 times to move right towards index1, ```<2>``` to type in 2, ```<backspace>``` to delete 1, ```<esc>``` to exit insert mode, and ```<:> <w> <q>``` to save and exit vim.      

---
**Step 8:** Show that the tests passed. 
        
I used arrow keys to access javac and java again to run the tests. They passed the tests!
```
[cs15lsp23bg@ieng6-201]:lab7:514$ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
```
```<enter>```
```
[cs15lsp23bg@ieng6-201]:lab7:515$ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```
```
JUnit version 4.13.2
..
Time: 0.021 

OK (2 tests)
```
---
**Step 9:** Commit and push changes to Github account. 
        
```
[cs15lsp23bg@ieng6-201]:lab7:514$ git commit -m "commit!"
```
```<enter>```
```
[cs15lsp23bg@ieng6-201]:lab7:514$ git push origin main
```
```<enter>```

