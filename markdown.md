# The Algorithms

## Basic Algorithm
    Basic search is a brute force search that moves through every element of the string until it finds an instance of the key. The algorithm starts by aligning the first element of the key to the first element of the text. At each position of the string, the algorithm checks to see if the elements match. If the elements match for the length of the key, the algorithm has found a match. Otherwise, it moves to the next element in the string to compare it to the key once again. This process repeats until all of the instances of the key have been found.

    - Upside:
            This method has some upsides. It is extremely reliable, and easy to implement.
    - Downside:
            Since it makes a comparison at each element in the string, and does not reposition when a mismatch is found, it is very inefficient for large strings and/or keys. These negatives are so severe that it really is only used as a learning tool for people new to algorithms in general. 

## KMP(Knuth Morris Pratt)
    The Knuth-Morris-Pratt (KMP) algorithm optimizes string matching by utilizing a Longest Prefix Suffix (LPS) table, which is a preprocessed array indicating the length of the longest proper prefix that is also a suffix for each position in the key. The LPS table efficiently guides the search process, allowing the algorithm to skip unnecessary comparisons when a mismatch occurs. The preprocessing algorithm initializes the LPS table by iteratively comparing characters in the key and updating the table accordingly. During the search phase, KMP compares the key to the string while intelligently skipping elements based on the LPS values, significantly reducing the number of comparisons compared to a basic approach

    - Upside:
        In essence, KMP enhances the efficiency of string matching by strategically considering the inherent patterns within the key.

    - Downside:
        it is not the most efficient search algorithm in our project. 

## Boyer Moore
    This algorithm employs two efficient preprocessing methods: the Bad Character Heuristic and the Good Suffix Heuristic. The Bad Character Heuristic focuses on handling mismatches by shifting the key strategically to the last instance of the "bad character" found in the string. If the bad character isn't present in the key, the comparison window is moved to the character following the bad character, avoiding unnecessary comparisons. The bad character array, sized for all ASCII values, facilitates this process by storing the rightmost occurrences of characters in the key. On the other hand, the Good Suffix Heuristic also addresses mismatches by recording the character following the mismatched one, known as the good suffix. It then locates the next instance of the good suffix in the string, comparing only the characters preceding it in both the string and the key. The good suffix array guides this process, indicating the number of characters to skip to check for the good suffix in the string. The Boyer-Moore algorithm intelligently combines the insights from both heuristics, optimizing the shift of the comparison window based on the greater value derived from the Bad Character and Good Suffix Heuristics. 

    - Upside:
        This approach minimizes unnecessary comparisons, enhancing the efficiency of string search operations.

# Implementation
    For our implementation we decided to recreate the CTRL + F / Command + F function. We wanted to recreate a real life example of when the string search algorithms would be used. 

	To create the CTRL + F function we implemented the different string search functions into one file. There are 3 different string search methods in the program , the basic function , the Knuth-Morris-Pratt function and the Boyer-Moore function. To run the program it takes in a file name and key in the command line. The main function then calls the “callFunction” function.

    This function allows for some leeway on the function name that the user typed in. This acts kind of like a switch statement but you can't use a switch with strings so this is the work around. 
 	The function then asks the user to enter which string search function they want to use and prints out the amount of times the key was found and the row and column of the key.  The functions did require some edits so that they would be useful for our implementation of CTRL + F.  The string search functions are void functions.  In the functions there is a vector called indexes created. Whenever there is a match the index is added to the index vector. At the end of the function the size of the vector is printed out and every index in the vector list is printed out. With the index we are able to find the row and column of where the key is. However there is a limitation to this part of the function. It means that in the txt files the max amount of characters in a line is going to be 80 and each line requires 80 characters. So the empty spaces are filled with spaces in the test cases.
    
# Control Find
![alt text](https://cdn.osxdaily.com/wp-content/uploads/2022/03/control-f-ipad-1-chrome-610x260.jpg)

For this project we looked at the Knuth-Morris-Pratt and Boyer-Moore string searching algorithm and make a function that acts similarly to the CTRL + F function  on windows and the Command + F function of Mac. 

## How to compile

    The code for this function is in the controlF.cpp file and the test cases are in the testCase file. 
    ```console
    $ g++ -std=c++11 controlF.cpp -o search
    ```

    ```bash
    $ ./search test.txt "key"
    ```

    The function will then ask which search algortihm to use for the searh


Whether you write your book's content in Jupyter Notebooks (`.ipynb`) or
in regular markdown files (`.md`), you'll write in the same flavor of markdown
called **MyST Markdown**.
This is a simple file to help you get started and show off some syntax.

## What is MyST?

MyST stands for "Markedly Structured Text". It
is a slight variation on a flavor of markdown called "CommonMark" markdown,
with small syntax extensions to allow you to write **roles** and **directives**
in the Sphinx ecosystem.

For more about MyST, see [the MyST Markdown Overview](https://jupyterbook.org/content/myst.html).

## Sample Roles and Directives

Roles and directives are two of the most powerful tools in Jupyter Book. They
are kind of like functions, but written in a markup language. They both
serve a similar purpose, but **roles are written in one line**, whereas
**directives span many lines**. They both accept different kinds of inputs,
and what they do with those inputs depends on the specific role or directive
that is being called. 

Here is a "note" directive:

```{note}
Here is a note
```

It will be rendered in a special box when you build your book.

Here is an inline directive to refer to a document: {doc}`markdown-notebooks`.


## Citations

You can also cite references that are stored in a `bibtex` file. For example,
the following syntax: `` {cite}`holdgraf_evidence_2014` `` will render like
this: {cite}`holdgraf_evidence_2014`.

Moreover, you can insert a bibliography into your page with this syntax:
The `{bibliography}` directive must be used for all the `{cite}` roles to
render properly.
For example, if the references for your book are stored in `references.bib`,
then the bibliography is inserted with:

```{bibliography}
```

## Learn more

This is just a simple starter to get you started.
You can learn a lot more at [jupyterbook.org](https://jupyterbook.org). 
