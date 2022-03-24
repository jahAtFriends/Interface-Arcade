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

```java
public class Cow implements Talkative {
  private weight;
  
  public Cow(String name) {
    this.name = name;
  }
  
  @Override
  public void speak() {
    if (this.weight <= 100) {
      System.out.println("moo.");
    else if (this.weight > 100) {
      System.out.println("MOOOOOOOO!!!!!");
    }
  }
}

```

```java
public class Cat implements Talkative {
  private String weight;
  
  public Cat(String name) {
    this.name = name;
  }
  
  @Override
  public void speak() {
    System.out.println("Meow");
  }
  
  public void speakByWeight() {
    if (this.weight <= 20) {
      System.out.println("meow.");
    else {
      System.out.println("zzzzzzz");
    }
  }
}
```

Which one of these two classes correctly implements the interface? For one, both of the
classes override the `speak()` method specified in the interface, so the code _will_
compile and run without any errors. However, notice that only _the second class_ obeys
the specifications in interfaces documentation which clearly indicates that the `speak()`
method must be consistent for all instances of the class. The `Cow` class outputs
different sounds depending on the weight of the cow.

This is discrepancy is an issue since those utilizing the `Cow` class expect the `speak()`
method to behave a certain way according to the interface when in reality it behaves in a
different way. This could lead to all sorts of unexpected erors. The power of interfaces
lies in this documentation since it enables programmers and programs to interact with each
other without the need to understand _all_ of the inner workings of each other's code.
  


## Project

In this project, you will demonstrate your ability to implement an interface by creating a
game which follows the model of the `TwoPlayerGame` interface. You can find the interface in
this repository, but more importantly you should read the 
[javadocs for this assignment](https://friendsbaltcs.github.io/docs/ACS/InterfaceArcade/).

Note a couple of salient elements of a two-player game:
- There are two players
- The players play the game on a shared surface (like a board)
- The players take turns
- When one player completes a single turn, it becomes the other's turn.
- The game can be played start to finish using only the methods in the interface (plus the constructor)

Now, in some sense, boxing is a game played by two people, but it is _not_ a `TwoPlayerGame`
since there really aren't any "turns" involved (unless it's a really bad match). You may
write the code for any game you'd like _as long as it obeys the specifications_.

You may (and should) write a `main()` method which calls the other methods that you write, but I will not use
this to play your game. I have already written code (which you will never get to see) that
can play any arbitrary `TwoPlayerGame()` that follows the specifications of the interface. So, __Follow them
very carefullly!__ At the end of the project, I will run your game using my code in front
of the whole class. If you did everything correctly, there will be no problems, otherwise
it will crash. Good luck!
