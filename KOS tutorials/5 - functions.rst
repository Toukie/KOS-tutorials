=========
Functions
=========

Imagine you're driving in a manual shift car for with an instructor for the first time.
He helps you getting into first gear and tells you the following when you want to accelerate: ::

  Let go of the gas pedal.
  Press in the clutch pedal.
  Shift the gear stick from first to second.
  Let go of the clutch pedal.
  Press in the gas pedal.

After a while he tells you: ::

  Let go of the gas pedal.
  Press in the clutch pedal.
  Shift the gear stick from second to third.
  Let go of the clutch pedal.
  Press in the gas pedal.

Not long after that he tells you: ::

  Let go of the gas pedal.
  Press in the clutch pedal.
  Shift the gear stick from third to fourth.
  Let go of the clutch pedal.
  Press in the gas pedal.

Wouldn't it be easier if instead of telling you the entire procedure he'd tell you the following: ::

  Shift from first to second.
  And after a after he tells you:
  Shift from second to third.
  And not long after that he tells you:
  Shift from third to fourth.

As you can see you only need to know how to shift once (if you're a quick learner) and after that telling the whole process is
repetitive. The same goes for code in KOS, you might want to use a piece of code more than once without typing it out everytime.
This is called a ``function`` and functions often have ``parameters`` (similar to starting conditions).

Keep in mind that the following piece of code is pseudo-code and is not actual working code but an example of what functions
are like: ::

  Function ShiftGearFirstToSecond {
    Let go of the gas pedal.
    Press in the clutch pedal.
    Shift the gear stick from first gear to second gear.
    Let go of the clutch pedal.
    Press in the gas pedal.
  }

Your instructor could now say ``ShiftGearFirstToSecond()`` and you'd know how to go from the first gear to the second.
But this is only about going from the first gear to the second and not from the second gear to the third.
To do that you'd need to have blank spaces for you to fill in with your desired gears. ::

  Function ShiftGear {
    Let go of the gas pedal.
    Press in the clutch pedal.
    Shift the gear stick from ____ to ____.
    Let go of the clutch pedal.
    Press in the gas pedal.
  }

On paper this sounds like a great idea but if your instructor tells you ``ShiftGear()`` ``first gear``, ``second gear``. But you're not sure where to
put ``first gear`` and where to put ``second gear``. Wouldn't it be handy if you made rule that the first word your instructor says is the
gear you start in and the second word he says is the gear you end in? Well luckily there's a way to apply that rule.
This is were ``parameters`` come into play, all functions get called using ``()`` after the function name and inside of the brackets
you put the parameters. ::

  Function ShiftGear {
    Parameter StartGear.
    Parameter EndGear.

    Let go of the gas pedal.
    Press in the clutch pedal.
    Shift the gear stick from StartGear to EndGear.
    Let go of the clutch pedal.
    Press in the gas pedal.
  }

As you can see we replaced the blank spaces with variables (parameters are also variables).
So to go from first gear to second gear you'd use:
``ShiftGear(first, second)``.
To go from second to third you'd use:
``ShiftGear(second, third)``.
To go from third to second you'd use:
``ShiftGear(third, second)``.

A working example of a function
_______________________________

Here's an example of a simple function which works in KOS: ::

  Function OneThroughFivePrint {
    print 1.
    print 2.
    print 3.
    print 4.
    print 5.
    }

Functions can have any name but avoid making functions and variables the same name as this will very likely cause problems.
A function will do anything that's inside of the curly brackets. To use this function type the following: ::

 OneThroughFivePrint().

This will show: ::

  1
  2
  3
  4
  5

A more complex function
________________________

Here's an example of a more complex function which has a parameter and will also work in KOS:

Let's say we're in a perfectly circular orbit around kerbin, we can use the following formula:
``velocity = (2 * pi * radius) / orbital period``
(https://en.wikipedia.org/wiki/Circular_motion#Formulas)

Ignore how ``ship:orbit:period`` works for now, that will be discussed in the next chapter. ::

  Function VelocityCalculator {
    Parameter OrbitHeight.

    set KerbinRadius to 600000.
    set TotalRadius to OrbitHeight + KerbinRadius.
    set OrbitalPeriod to ship:orbit:period.
    print (2 * 3.1416 * TotalRadius) / OrbitalPeriod.
  }

If you're in a 400 km circular orbit and type: ::

  VelocityCalculator(400000).

Will show your orbital velocity.

Now what if you want to use the velocity for other calculations, is that possible? Yes of course that's possible!
The ``return`` command is very helpful is these situations. The ``return`` function returns a value, piece of text, boolean etc and ends
the function it is in. ::

  Function VelocityCalculator {
    Parameter OrbitHeight.

    set KerbinRadius to 600000.
    set TotalRadius to OrbitHeight + KerbinRadius.
    set OrbitalPeriod to ship:orbit:period.
    return (2 * 3.1416 * TotalRadius) / OrbitalPeriod.
    // everything after the return command will be skipped because a return command ends a function.
    print "this will be skipped".
  }

  set CurrentVelocity to VelocityCalculator(400000).
  print CurrentVelocity.

Will show your orbital velocity for a circular orbit at 400 kilometers.
