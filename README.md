# KFE-GrepNew

Page 120

Let us show now how one can read and write text files, what is a very common task. This can be done in various ways, so consider the program below as an example, not necessarily the best in all situations. Note that when dealing with text files, one should always specify the encoding of all input/output files.

Listing 77

KFE-GrepNew/GrepNew.java

The program creates the file grep_alice.txt containing

Line 1429: `It's a Cheshire cat,' said the Duchess, `and that's why.
Line 1437: I didn't know that Cheshire cats always grinned; in fact, I
Line 1561: the Cheshire Cat sitting on a bough of a tree a few yards off.
Line 1567: `Cheshire Puss,' she began, rather timidly, as she did not at
Line 2234: be a grin, and she said to herself `It's the Cheshire Cat: now I
Line 2270: `It's a friend of mine--a Cheshire Cat,' said Alice: `allow me
Line 2317: When she got back to the Cheshire Cat, she was surprised to

Here, we used classes from the java.nio package, which is newer than java.io and usually recommended. Objects of class Path represent the names of files in the current file system (not necessarily existing ones). We can create such objects by calling the static factory method get and passing (absolute or relative) name of a file. Then one can check if such a file exists, whether it is readable, executable, what its size or last modification time is, etc.

Note also the form of the try clause. Here, we used again the try-with-resources construct. Before the opening brace, in round parentheses, we create objects represent-ing “resources” — in this case streams. These could be also other types or resources, like data base connections; what is important is that they have to be closeable (in other words, they have to implement the Closeable interface). If there are more than one, as here, we separate them by a semicolon. As we remember, the benefit of this form of the try clause is that we don’t have to bother with closing the resources — they will be automatically closed whether an exception has occurred or not. Moreover, this form inserts variables declared in parentheses to the scope of the try clause, but not to the outer scope, keeping the outer scope unpolluted by variables that are not needed there.

In the loop reading the file, we call readLine on the BufferedReader object. In this way, we can read the file line by line not bothering about detecting the LF character 121 ourselves. When the end of file is reached, readLine returns null, otherwise it returns the next line as a string (with the LF character chopped off ).
