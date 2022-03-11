# Lab Report 5: Different Bugs
by Andrew Cen

## How I Found The Tests
![script](https://acen23.github.io/cse15l-lab-reports/lib5/script.png)
- I first changed the script.sh to echo the file name for each iteration of the "do" loop. That way, I could see which file would be of importance.
- For each file, I had both implementations run and output to two different temporary text files named "results.txt" and "results2.txt".
- Finally, I used "diff" on both "results.txt" and "results2.txt" so that the script would output the differences between the two implementation outputs for that specific file.
- After running "bash script.sh", the files had their differences printed out, if any.

## Test For File 194.md
- For both implementations, these were the outputs (top output is the class implementation, bottom is personal implementation): ![194output](https://acen23.github.io/cse15l-lab-reports/lib5/194.png)
- The expected output should be a list with the url "my_(url)". Therefore, neither implementation has the correct output.
- The part of the code for the personal implementation that has the bug is here: ![194error](https://acen23.github.io/cse15l-lab-reports/lib5/194error.png) The implementation fails to parse links that do not have parentheses surrounding their urls. This syntax works as a link according to [commonmark](https://spec.commonmark.org/dingus/). The implementation should instead look out for urls following the colon after an open and closed bracket.

## Test For File 201.md
- For both implementations, these were the outputs: ![201output](https://acen23.github.io/cse15l-lab-reports/lib5/194.png)
- The expected output should be an empty list. Therefore, the personal implementation has the correct output.
- The part of the code for the class implementation that has the bug is here: ![201error](https://acen23.github.io/cse15l-lab-reports/lib5/201error.png) The implementation incorrectly parses links that have characters between the end bracket and open parentheses of a potential link. The implementation should instead add a check to see if the next char after the pair of brackets is an open parentheses before parsing as a valid link.