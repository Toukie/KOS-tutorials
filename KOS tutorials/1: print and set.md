# Print and set

Before we can send ships to space we first need to know the basic features of KOS.
Let's begin with the `print` command. Type the following in your terminal and press `ENTER` to enter the piece of code. Keep in mind that ALL lines of code require a period
at the end of the line, there are some exceptions but more about that later.

```
print "hello world".  // shows: hello world
```

See those two forward slashes? That means that a comment has been made, anything
after the double slashes won't be read by the script so you don't have to worry
about what it says. Here's an example of what happens if you make something a comment:

```
// print "hello world 1".
print "hello world 2".
```

If you'd run these two lines of code you'd **ONLY** see:
`hello world 2`

You'd might be wondering why you'd want to use the forward slashes if the script doesn't read them.
The computer ignores them, but they're there to help leave explanations for the humans to see who might have to read your program.

To clear the screen type:

```
clearscreen.
```

Now say that we really like to use our hello world command but don't want to type
the entire sentence every time, we could use the set command.

```
set x to "hello world".
```

The `set` command 'sets' a certain value to the given variable. Everytime we refer
to `x` we will actually refer to `"hello world"`.

```
set x to "hello world".
print x. // shows: hello world
```

Of course we can choose other things to print other than `"hello world"`.
Keep in mind that 'normal' text requires `""` and variables you made using the
set command, numbers and booleans (true or false) don't need `""`.

```
set x to "hello world".
set y to true.
set z to 123.

print x.   // shows: hello world
print "x". // shows: x
print y.   // shows: true
print "y". // shows: y
print z.   // shows: 123
print "z". // shows: z
```

You can also replace a variable you've made:
```
set x to "hello world".
set x to "updated text".
print x. // shows: updated text

set x to "hello world".
print x. // shows: hello world
set x to "updated text".
print x. // shows: updated text
```
As you can see `hello world` doesn't exist anymore. If you'd want to print
both you could do:

```
set x to "hello world".
set y to x.
set x to "updated text".

print y. // shows: hello world
print x. // shows: updated text
```

Variables don't just have to be one letter you could also use a word as a variable, don't use spaces when naming variables.

```
set WhateverThisVariableIs to false.
print WhateverThisVariableIs. // shows: false
```
