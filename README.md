# Word-Composition-Problem

# Problem Statement
Write a program 
1. Reads provided files (Input_01.txt and Input_02.txt) containing alphabetically sorted words list (one
word per line, no spaces, all lower case)
2. Identifies & display below given data in logs/console/output file
o longest compounded word
o second longest compounded word
o time taken to process the input file 

Note: A compounded word is one that can be constructed by combining (concatenating) shorter words
also found in the same file .

# Input01

For example, if the file contained:
Input_01.txt is a small word list, consisting following words:


       cat
       cats
       catsdogcats
       catxdogcatsrat
       dog
       dogcatsdog
       hippopotamuses
       rat
       ratcatdogcat
       
Answer:
1. Longest Compound Word: ratcatdogcat
2. Second Longest Compound Word: catsdogcats
Note:
Hippopotamuses is the longest word but that is not the answer as it is not a compounded word



Approach
========

There are various methods to approach the solution but I am gonna use various techniques like Dynamic programming , Hashing , Rabin karp Algo etc .

Here are the steps I took:


Let’s illustrate the process in Details

# Step 1
First we take input with getline function . After taking strings as a input we call Rabin karp function and generate a particular hash values for every strings and Create a map and update the value to 1 in map Example - Map[hash_value]=1 .

# Step 2
Next we sort the Strings according to their Size and If we find to strings Equal then we sort according to lexicographically, Then we scan the string from the bottom and takes every particular strings.

# Step 3
Now we created a Memeset and passess the values according to the actual Arguments.
Now call the recursion function and set a boolean function accoding to boolean output we find longest composite word.




Algorithm 
========

The most important algorithm we use are Rabin karp and we use dynamic programming with Recursion.
Rabin karp is used to find the hash value for every string,
After sorting we scanned the string from the bottom and we call the recursion function and passes val and check composite words 


   
   


Time Complexity
========

The complexity of this algorithm is O(n*(l*l)) ,where n is the size no of strings in Input file and l is the length of longest string present in Input file.







