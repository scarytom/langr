Learning a Language
===================

__Introduction__
These exercises are taken from an article by Larry O’Brien entitled '15 Exercises to Know A Programming Language', and are intended to provide a framework for truly getting to know a new programming language

__Part 1 - Calculations__

1) Write a program that takes as its first argument one of the words ‘sum,’ ‘product,’ ‘mean,’ or ‘sqrt’  and for further arguments a series of numbers. The program applies the appropriate function to  the series.

Educational goals of exercise 1:
 * Requires basic control flow, basic operators, and the math library. (Complex numbers available?)
 * What are arrays like?
 * What about parsing / implicit conversion?
 * Are functions first-class (availability of Map() and Apply())?
 * Error handling: What happens on invalid data?

2) Write a program that calculates a Haar wavelet on an array of numbers. The Haar transform works as follows: calculate the average and difference-from-the-average of pairs of input values. Gather averages as the first part of the returned array, “detail coefficients” as the second. Recurse until the first value is the average is the entire series (steps required = log base 2(array length)).

For instance:
   Haar([8, 5]) ->  [6.5, 1.5]
   6.5 = (8+5)/2
   1.5 = 8 – (8+5)/2)

   Haar([8, 5, 7, 3) -> [5.75, 1.75, 0.75, -0.25]
   Step 1 -> [6.5, 5, 1.5, 2]
   1st and 3rd values as prior example, 2nd and 4th transform applied to 7 and 3
   Step 2 -> Recurse, using [6.5, 5] and [1.5, 2] as bases. (N.B.: Average([8,5,7,3]) == 5.75)

Educational goals of exercise 2:
 * How are functions declared and organized?
 * What about recursion? What happens when I pipe in a megabyte of data? (Is tail-recursion available?)
 * How does the environment support unit-testing?
 * Exception handling: what if the array has an odd-numbered length?
 * Data representation — what about rounding errors on very small coefficients?

3) Write a program that takes as its arguments a the name of a bitmapped image (Start with images from the Waterloo Repertoire Grayset 2: http://links.uwaterloo.ca/greyset2.base.html) . Apply the Haar wavelet to the pixel values. Save the results to a file.

Educational goals of exercise 3:
 * File manipulation and binary I/O.
 * Standard (?) library.
 * Type-strictness (what’s involved in treating a pixel value as a number?)
 * Emerging sense of program structure / refactoring.

4) Using the outputs of the previous exercise file, write a GUI program that reconstitutes the original bitmap (N.B.: The Haar wavelet is lossless).

Educational goals of exercise 4:
 * GUI behavior, including events, file manipulation, and behavior with long-running calculation (async calcs?).

5)  Write a GUI program that can:
 i. Open bitmapped images in a variety of formats,
 ii. Apply the Haar partially (e.g., a “Do a step” button that applies the Haar transform but does not recurse).
 iii. Visualize a partial Haar transform (i.e., scale the detail coefficients into the range 0-255 and display them as pixel values)
 iv. Clip to 0 coefficients whose absolute values are < x. (N.B.: This is a lossy-y transform that allows for great compression)
 v. Reconstitute a bitmap from values created by the above transform.
 vi. Displays the time it takes a bitmap to be transformed, clipped, and reconstituted.

Mental exercises: What could be reused if I wanted to do these exercises with sound? How would a plug-in model for wavelet functions work? How would a purely dynamic wavelet function (i.e., fill a textfield with code) work?

Educational goals of exercise 5:
 * Performance.
 * Non-trivial program structure.
 * Component model, dynamism.
 * Environment: debugging, iterative development, testing, version control, refactoring, etc.

__Part 2 - Data Structures__
 
6) Write a class (or module or what-have-you: please map OOP terminology into whatever paradigm appropriate) that only stores objects of the same type as the first object placed in it and raises an exception if a non-compatible type is added. Write a program that uses this class, outputting “Store 1 contains n instances of type t and then iterating over the stored objects,” and handles the exception. Now refactor the application so that the exception results in the creation of a new instance of your storage class and continues, so that the output would be “Store 1 contains n instance of type t, etc., Store 2 contains 1 instance of type u, etc.”

Educational goals of exercise 6:
 * class creation, component structure, type behavior, memory allocation, exception/resumption, environment support for refactoring.

7) Using the language’s idioms, implement a tree-based datastructure (splay, AVL, or red-black).

Educational goals of exercise 7:
 * In-memory data structures. Algorithm expression. Idioms. Memory and type issues.

8) Create a new type that uses a custom comparator (i.e., overrides “Equals”). Place more of these objects than can fit in memory into the datastructure created above as well as into standard libraries, put more objects into it than can fit in memory. Compare performance of the standard libraries with your own implementation.

Educational goals of exercise 8:
 * You should really have a “sense” of the program’s memory management by this point. Not complete knowledge, but enough sense to begin work.

9) Implement an iterator for your datastructure. Consider multithreading issues.

Educational goals of exercise 9:
 * Refactoring, expressiveness, design patterns, concurrency model.

10) Write a multithreaded application that uses your data structure, comparable types, and iterators to implement the type-specific storage functionality as described in Exercise 6. How do you deal with concurrent inserts and traversals?

Educational goals of exercise 10:
 * Understanding of data structures, Concurrency issues (locking, races, etc.).

__Part 3 - Libraries, Frameworks, and Mashups__

11) Write a program that outputs the current date and time to a Web page as a reversed ISO 8601-formatted value (i.e.: “2006-06-16T13:15:30Z” becomes “Z03:51:31T61-60-6002″). Create an XML interface (either POX or WS-*) to the same.

Educational goals of exercise 11:
 * “Hello, Web!”

12) Write a client-side program that can both scrape the above Web page and the XML return and redisplays the date in a different format.

Educational goals of exercise 12:
 * HTTP get, string parsing. 

13) Write a daemon program that monitors an email account. When a strongly-encoded email arrives that decrypts to a valid ISO 8601 time, the program sets the system time to that value.

Educational goals of exercise 13:
 * Encryption, Email, OS libraries, daemons

14) Write a program that connects to your mail client, performs a statistical analysis of its contents.
