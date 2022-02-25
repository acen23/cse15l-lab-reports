# Lab Report 3: Testing MarkdownParse
by Andrew Cen

## 1. Snippet 1
- For both implementations, the test case created was the same: ![snippet1test](https://acen23.github.io/cse15l-lab-reports/snippet-1-test.png)
- For our implementation, this was the output: ![snippet1output1](https://acen23.github.io/cse15l-lab-reports/snippet-1-output-1.png)
- For the reviewed implementation, this was the output: ![snippet1output2](https://acen23.github.io/cse15l-lab-reports/snippet-1-output-2.png)
- To make our program work correctly for Snippet 1, we'd have to only make a minor change. First, we'd have to make our program ignore all links with special markdown characters in front. In the first line, part of the link is considered a block quote, which negates the link effect. Second, we'd have to make our program acknowledge link titles with special characters still as working links, such as the last line.

## 2. Snippet 2
- For both implementations, the test case created was the same: ![snippet2test](https://acen23.github.io/cse15l-lab-reports/snippet-2-test.png)
- For our implementation, this was the output: ![snippet2output1](https://acen23.github.io/cse15l-lab-reports/snippet-2-output-1.png)
- For the reviewed implementation, this was the output: ![snippet2output2](https://acen23.github.io/cse15l-lab-reports/snippet-2-output-2.png)
- To make our program work correctly for Snippet 2, we'd possibly have to make a little more than 10 lines worth of change. For the second line of the file, the url includes a nested set of parentheses. Our program would have to pair each open parentheses with its closed match before deciding which pair of parentheses the link url is inside of. This could also interfere with tests involving unpaired parentheses, as our code would have a different way of parsing the parentheses now. Similarly, our program would have to do the exact same process for nested brackets, since the character right after the next closed bracket for the last line is not the expected open parentheses.

## 3. Snippet 3
- For both implementations, the test case created was the same: ![snippet3test](https://acen23.github.io/cse15l-lab-reports/snippet-3-test.png)
- For our implementation, this was the output: ![snippet3output1](https://acen23.github.io/cse15l-lab-reports/snippet-3-output-1.png)
- For the reviewed implementation, this was the output: ![snippet3output2](https://acen23.github.io/cse15l-lab-reports/snippet-3-output-2.png)
- To make our program work correctly for Snippet 3, we'd only need a minor change. The issue with the detection for the link on the first few lines and the link on the last few lines is that our program doesn't care if there are extra lines within the link titles or link urls. In order to account for this, we could just check for line break characters within the link title or link url.