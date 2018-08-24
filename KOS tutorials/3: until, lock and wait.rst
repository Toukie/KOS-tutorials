Until, lock and wait
====================

The ``wait`` command pretty straight forward: ::

  wait 10.
 print "done waiting".


It will take 10 seconds before ``done waiting`` shows up.
Using ``wait 0`` will let the script wait for one physics tick, this can be handy for
when you're doing stuff with maneuvers. Maneuvers don't show up instantly but show up
after one physics tick. More about maneuvers in part ???.

The ``until`` command will keep looping a piece of code until the given value has been met.
Before we can talk about until loops let's first talk about ``time:seconds`` and the ``lock`` command. ::

  print time:seconds.


will print the current time in seconds. Let's say the time is 1 minute.
It would print ``60``. You can also set the current time as a variable: ::

  set CurrentTime to time:seconds.

The variable ``CurrentTime`` will stay 60 seconds. Using the ``set`` command will look at
a value and pick that value to stay the  same, even if the value it was set to changes.
For instance, printing ``CurrentTime`` would give 60. Not only at ``time:seconds`` = 60,
also at any other time like ``time:seconds`` = 4000. Eventhough ``time:seconds`` is 4000,
``CurrentTime`` is still 60.

The ``lock`` command updates constantly the variable, for example: ::

  lock TimeSecondsPlusTen to time:seconds + 10.

If you print ``TimeSecondsPlusTen`` at 60 seconds it will show 70, if you print
``TimeSecondsPlusTen`` at 4000 seconds it will show 4010.

Using until, lock and wait in an example
_________________________________________

If we now combine all the command we can make the following piece of code: ::

  set Adder to 0.
  lock Multiplier to Adder * 2.
  set TimePlusFive to time:seconds + 5.

  until time:seconds > TimePlusFive {
    print Multiplier.
    set Adder to Adder + 1.
    wait 1.
  }

So an easy way to read the until loop is to cover what ever is inside of the curly brackets
and say: until ``time:seconds`` is bigger than our current time plus 5 seconds, print
``Multiplier``, increase the value of ``Adder`` and wait 1 second.

The outcome of this piece of code is: ::

  0
  2
  4
  6
  8
  10

Wait until
__________

You can also use the ``wait until`` command, this blocks all other code until the
conditions have been met. ::

  set TimePlusFive to time:seconds + 5.
  wait until time:seconds > TimePlusFive.
  print "done waiting".

It will take 5 seconds for ``done waiting`` to show up.
