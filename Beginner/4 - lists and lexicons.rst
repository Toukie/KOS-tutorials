==================
Lists and lexicons
==================

::

  set Value1 to 0.
  set Value2 to 5.
  set Value3 to 10.
  set Value4 to 15.
  set Value5 to 20.

Let's say we want to put these values in a list we want to edit later we can put them into a list by typing the following: ::

  set ValueList to list(Value1, Value2, Value3, Value4, Value5).
  print ValueList.

This will show: ::

  [0] = 0
  [1] = 5
  [2] = 10
  [3] = 15
  [4] = 20

As you can see the list goes from 0-4 instead of 1-5. So if you'd want to access ``Value3`` you'd need to look for ``[2]``.
This can be done as follows: ::

  print ValueList[2]. // shows 10

But let's say you want to print every item in the list you could do: ::

  print ValueList[0]. // shows 0
  print ValueList[1]. // shows 5
  print ValueList[2]. // shows 10
  print ValueList[3]. // shows 15
  print ValueList[4]. // shows 20

But the problem with this is that you have to know how big the list is and it'd take up a lot space when dealing with big lists. ::

  for Whatever in ValueList {
    print Whatever.
  }

  for Value in ValueList {
    print Value.
  }

Both pieces of code do **EXACTLY** the same.
This checks each item in a given list (now called ``Whatever``) and does what the curly brackets contains.
(For each item in the list called ``ValueList``, which we call ``Whatever``, do whatever is inside of the brackets).

In this case it prints: ::

  0
  5
  10
  15
  20

You can also use variables to check an item in a list: ::

  set x to 3.
  print ValueList[x]. // shows 15

Does the same as: ::

  print ValueList[3]. // also shows 15

Lexicons
________

Lexicons are in a way the same as lists but they have some crucial differences.
Lexicons can store a pair of information, for example: ::

  set MyLexicon to lexicon("MyValue1", 100, "MyValue2", 200, "MyValue3", 300).

The following piece of code acts **EXACTLY** the same as the piece of code above but is easier to read: ::

  set MyLexicon to lexicon(
    "MyValue1", 100,
    "MyValue2", 200,
    "MyValue3", 300
  ).

::

  print MyLexicon["MyValue1"]. // shows 100
  print MyLexicon["MyValue2"]. // shows 200
  print MyLexicon["MyValue3"]. // shows 300

NOTE: print ``MyLexicon[100]``. will NOT work.
