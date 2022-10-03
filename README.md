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

There are various methods to approach the solution but I use "Tries" Data structure.

Here are the steps I took:


Let’s illustrate the process with an example, the first word is cat and we add it to the trie. Since it doesn’t have a prefix, we continue. Second word is cats, we add it to the trie and check whether it has a prefix, and yes it does, the word cat. So we append the pair <’cats’, ‘s’> to the queue, which is the current word and the suffix. The third word is catsdogcats, we again insert it to the trie and see that it has 2 prefixes, cat and cats. So we add 2 pairs <’catsdogcats’, ‘sdogcats’> and <’catsdogcats’, ‘dogcats’> where the former suffix correspond to the prefix cat and the latter to cats. We continue like this by adding <’catxdogcatsrat’, ‘xdogcatsrat’> to the queue and so on. And here’s the trie formed by adding example the words in the problem definition:


After building the trie and the queue, then we start processing the queue by popping a pair from the beginning. As explained above, the pair contains the original word and the suffix we want to validate. We check whether the suffix is a valid or compound word. If it’s a valid word and the original word is the longest up to now, we store the result. Otherwise we discard the pair. The suffix may be a compound word itself, so we check if the it has any prefixes. If it does, then we apply the above procedure by adding the original word and the new suffix to the queue. If the suffix of the original popped pair is neither a valid word nor has a prefix, we simply discard that pair.


Algorithm 
========

Step 1 - 
 * The algorithm first scan the file line by line and create a trie by using the words in the file.
 * Before inserting each word into the trie, it will check if the word has any prefixes. If yes, it will create
   word-suffix pairs and add them into a queue. 


Step 2 -
 * Then, the algorithm will pop a pair from the queue to see if the suffix in the word-suffix pair is a word 
   in the file. If yes, the word is a compound word. Then, it will update the number of compound words, and
   if it also is longer than the previous compound word, it will update the variables of longestCompoundWord
   and secondLongestCompoundWord as well. 
   
Step 3 -
 * If the suffix in the word-suffix pair is not a word in the file, it will check if the suffix has any prefixes.
 * If yes, it will create new word-suffix pairs and add them into the queue. Otherwise, it will just discard the pair
    and pop a new pair from the queue and repeat the process until the queue is empty.
    
Step 4 -
 * The algorithm runs in linear, O(kN),  where N is the number of words in the input file, and k is the maximum 
   number of words in a compound word.
   
   


Time Complexity
========

The complexity of this algorithm is O(kN) where N is the number of words in the input list, and k the maximum number of words in a compound word. The number k may vary from one list to another, but it’ll generally be a constant number like 5 or 10. So, the algorithm is linear in number of words in the list, which is an optimal solution to the problem.







