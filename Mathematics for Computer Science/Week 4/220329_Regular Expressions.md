## Regular Expressions

* Rethinking Regular Languages
  * We currently have several tools for showing a language L is regular :
    * Construct a DFA for L.
    * Construct an NFA for L
    * Combine several simpler regular languages together via closure properties

* Consider a language L = { w contains aa as a substrings }
  * Difficult to manipulate with verbal descriptions
* Regual Expressions are a way of describing a language via a string representation
  * Easy to apply language operators
  * Shortened to regex
* Wide applicability
  * JavaScript : for data validation
  * UNIX grep and flex tools : search files and build compilers
  * Used to clean and scrape data for largescale analysis projects.
* Conceptually, regular expressions are strings describing how to assemble a larger language out of smaller pieces.

