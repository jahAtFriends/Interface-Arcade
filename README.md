# Interface Arcade

## Overview of Interfaces
Recently, you have been studying interfaces in class. Interfaces enable us to specify the
_kinds_ of methods that a given class has without specifying how those methods work. Hence,
for example, the `Comparable` interface specifies that classes which implement it will
all have a `compareTo(some-object)` method which allows you to compare "this" object to another
returning a negative number indicating "less than," zero for "equal to," or a postive
number for "greater than."

Here is another example. Consider the `Talkative` interface (which I made up just now).

```java
/* 
 * Specifies that the instances of the implementing class has the faculty
 * of "speech." Speech is defined for the purposes of this interface as
 * as making a certain noise proper to the class and consistent accross
 * all members of the class. Hence, all cows should "moo" and all cats
 * should "meow," although subclasses of either of these may make their
 * own proper noise.
 */
public interface Talkative {
  /*
  * Causes an instance of a class to speak. Speaking may be achieved by
  * simply printing a line of text to the command line using System.out
  * or by some advanced method of playing a sound through system audio.
  * Either way, all instances of a class should make the same sound
  * without variation.
  */
  public void speak();
}
```

Notice that in this interface, there is only one method, but there is a _ton_ of
documentation. Why is that? Since the interface doesn't provide a method body
for the `speak()` method (in fact in place of brackets, the method declaration ends
in a semicolon), we need more information about what such a method would _do_.

All of that documentation is important because, after the code is written, it can be
used by anyone, and, unless the programmer wants to maintain a hotline where he can
be reached to explain his code, there needs to be a clear explanation about how his or
her code is expected to work. Interfaces allow us to do this in a uniform way as we will
know that, as long as the programmers did their job correctly, _any_ class which
implements the `Talkative` interface is going to have a `speak()` method that behaves
_exactly_ as specified.

Below is are two attempts at implementing the `Talkative` interface. One is correct, the
other is not.
  
[javadocs for this assignment](https://friendsbaltcs.github.io/docs/ACS/InterfaceArcade/).

## Project

Your two-player game should follow all of the specifications perfectly as your game will
_not_ be permitted to include method calls to run your game as a stand-alone program.
Rather, the methods will be called by a "user" or "third-party developer" (me) attempting
to create an arcade of all of your games. Everyone's program will be tested with the
_identical_ tester method (which you are not permitted to see ahead of time).

Still, it is a good idea to test your code yourself. Your project will be run for the first
time in front of the whole class, after which I will loudly announce your grade on the spot.
Good luck!
