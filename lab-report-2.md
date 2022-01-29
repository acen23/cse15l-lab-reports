# Lab Report 2: Debugging
by Andrew Cen

## List of Bugs:
1. 
- Code fix: ![change-1](https://acen23.github.io/cse15l-lab-reports/change1.png)
- Test file that failed: [test-file-1](https://github.com/msimitz/markdown-parse/blob/main/test-file-two.md)
- Output symptom: ![symptom-1](https://acen23.github.io/cse15l-lab-reports/symptom1.png)
- The symptom showed a list of names in the list of links, which wasn't supposed to be counted. According to the test file, this should have counted as regular text, *not* as another link. To make the code ignore regular text with similar syntax, we made the program first check to see if the end bracket and open parentheses are adjacent, before reading it as a link.

2. 
- Code fix: ![change-2](https://acen23.github.io/cse15l-lab-reports/change2.png)
- Test file that failed: [test-file-2](https://github.com/msimitz/markdown-parse/blob/main/test-file-three.md)
- Output symptom: ![symptom-2](https://acen23.github.io/cse15l-lab-reports/symptom2.png)
- The symptom of an out of bounds exception showed that the program was trying to parse characters beyond the file's end. The test file had an unpaired open parentheses at the end of the file, so the program was trying to look for the end parentheses that didn't exist, thus causing it to go out of bounds. We fixed this bug by making the program check to see if any other bracket or parentheses existed in the file, before ending the parsing.

3. 
- Code fix: ![change-3](https://acen23.github.io/cse15l-lab-reports/change3.png)
- Test file that failed: [test-file-3](https://github.com/vdvo1029/markdown-parse/blob/main/test-file1.md)
- Output symptom: ![symptom-3](https://acen23.github.io/cse15l-lab-reports/symptom3.png)
- The symptom of another out of bounds exception showed that the program was once again trying to parse beyond the file's end. The test file consisted of just a pair of empty brackets, so the program was trying to look for an open parentheses adjacent to the end bracket, thus causing it to go out of bounds. We fixed this bug by making the program check to see if there were any characters left in the file before checking the next character for an open parentheses.