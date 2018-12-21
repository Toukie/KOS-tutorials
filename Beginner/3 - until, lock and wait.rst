====================
Until, lock and wait
====================

The ``wait`` command is pretty straight forward: ::

  wait 10.
  print "done waiting".


It will take 10 seconds before ``done waiting`` shows up.
Using ``wait 0`` will let the script wait for one physics tick (a physics tick is the time it takes for KSP to update its physics), this can be handy for when you're doing stuff with maneuvers. Maneuvers don't show up instantly but show up
after one physics tick. More about maneuvers in a future tutorial.

The ``until`` command will keep looping a piece of code until the given value has been met. Here's a simple example of what you can do with an ``until`` command: ::

  set x to 0.
  until x > 100 {
    print x.
    set x to x + 1.
  }

This first sets ``x`` to 0 and until ``x`` is bigger than 100 it does whatever happens within the brackets.
In this case it prints ``x`` and then it increases ``x`` by 1. This loop repeats itself until ``x`` is bigger than 100.
Before we can talk about more complex until loops let's first talk about ``time:seconds`` and the ``lock`` command. ::

  print time:seconds.

Will print the current time in seconds. Let's say the in-game time is 1 minute.
It would print ``60``. You can also set the current in-game time as a variable: ::

  set CurrentTime to time:seconds.

The variable ``CurrentTime`` will stay 60 seconds. Eventhough the in-game time changes: ::

  set CurrentTime to time:seconds.
  print CurrentTime. // shows: 60
  wait 10.
  print CurrentTime. // shows: 60

As you can see, eventhough the in-game time has changed the variable ``CurrentTime`` is still 60. The ``set`` command does **NOT** constantly update the variable. If you want a constantly updating variable you have to use the ``lock`` command.
Here's an example of what the ``lock`` command can do: ::

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
and say: until ``time:seconds`` is bigger than our current time plus 5 seconds, repeat whatever I covered with my hand.
In this case that'd be: print ``Multiplier``, increase the value of ``Adder`` and wait 1 second.

The outcome of this piece of code is: ::

  0
  2
  4
  6
  8
  10

Wait until
__________

You can also use the ``wait until`` command, this pauses the current script until the
conditions have been met. ::

  set TimePlusFive to time:seconds + 5.
  wait until time:seconds > TimePlusFive.
  print "done waiting".

It will take 5 seconds for ``done waiting`` to show up.
Note: the ``wait until`` command only checks the condition once per physics tick.  Using ``wait until`` for a fraction of a physics tick will round up to the start of a new physics tick.
