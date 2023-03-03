# List

## Learning Goals

- Explain the List interface.
- Explain an ArrayList and how it differs from an Array.
- Review commonly used methods of the ArrayList.

## List in Java

`List` is an interface in Java that implements the `Collection` interface and
provides a way to store an ordered collection. A list is something that has
certain capabilities, but Java does not provide a base class for lists. In
other words, there is no "default" implementation of a "list" functionality.
Instead, there are specific implementations of the `List` interface that provide
implementations that are optimized for certain use cases:

1. `ArrayList`: this implementation focuses on the access speed for its data.
2. `LinkedList`: this implementation focuses on the insertion and manipulation
   (moving) speed for its data.
3. `Stack`: this implementation focuses on the ability to push elements on a
   stack and pop them from a stack in a last-in, first-out (LIFO) access pattern.
4. `Vector`: this implementation is focused on making the underlying collection
   "thread safe", which means it can more easily be used by multiple "running
   instances of your program" at the same. This is a topic that will be covered
   in a later unit.

The most important aspect of all these implementations is that because they all
implement the `List` interface, we could use them interchangeably for list
functionality. But because their implementations vary, it's good to understand
what use cases they are better suited for. We will go more in depth about each
of these types of lists in either this lesson or in another module.

The most important aspects of a `List` in Java are:

1. A list is an ordered data structure, which means that each element is added
   at a specific location and can be accessed using an index, which represents
   its position in the collection.
2. Lists allow duplicate values.
3. A list is dynamically sized, which means it can continue to grow as you add
   elements to it.
4. A list is part of the Java Collections framework, which gives it several
   capabilities that we will go over below.

In this section, we will focus on general `List` functionality, and we will use
the most commonly used `List` implementation, `ArrayList`, in our examples. But
all the examples we will be going through will work with any of the `List`
implementations.

## ArrayList in Action

To use a `List` in Java, we must choose a specific implementation - in this case,
we will choose an ArrayList. An **ArrayList** is a class that implements the
`List` interface and supports the addition and removal of elements, unlike an
array. To make use of the `List` data structure, we need to import it. The
`List` interface and the `ArrayList` class both live in the `java.util` package:

```java
import java.util.List;
import java.util.ArrayList;

public class ListExample {
    public static void main(String[] args) {
       List myList = new ArrayList();
       myList.add("a name");
       myList.add(2);
       myList.add(2.3);
       for (Object item: myList) {
          System.out.println(item);
       }
       myList.add("a fourth item");
       System.out.println(myList.get(3));
    }
}
```

As we can see, we were able to create a list without specifying how many items
it would hold, and we were able to keep adding to the list without having to worry
about re-sizing it. This differs from the arrays that we learned about earlier
since arrays are a fixed size.

We can refer to any item on the list by its index: `myList.get(<index>);`. Note
that, as with arrays, indexes on lists start with the number 0.

Did you notice that we were able to add objects of any kind to this list? This is
not necessarily a good thing:

1. Although it's convenient to be able to put anything in the list, it makes
   using any of those values difficult because we don't know their type. This
   means we can't be sure what we're allowed to do with them and what we're not.
2. This is not "type safe", which means the compiler has no way to tell if we're
   adding something to the list that wasn't meant to be there.

Let's specify what type of items we want in the list to make it type safe:

```java
import java.util.List;
import java.util.ArrayList;

public class ListExample {
    public static void main(String[] args) {
       List<String> myStringList = new ArrayList<String>();
       myStringList.add("first string");
       myStringList.add("second string");
       myStringList.add("third string");
       for (String myString: myStringList) {
          System.out.println(myString);
       }
    }
}
```

This `String` list will now only accept `String` objects and the compiler will
be not accept any other values. We can also see that we can iterate through a
`List` the same way we would iterate through an array.

### ArrayList Constructors

Another way we could have written the above example is to define the list as an
`ArrayList` from the start like so:

```java
ArrayList<String> myStringList = new ArrayList<String>();
```

If we know about how many items we will be putting in our array list, we could
also specify the `ArrayList` size like so:

```java
ArrayList<String> myStringList = new ArrayList<String>(3);
```

In the above line of code, we are saying we are expecting there to be about 3
items in the `ArrayList`. Specifying the initial capacity helps with the
performance when running the code - but is not a requirement.

The ArrayList constructor can also take in a different collection and create an
ArrayList from it.

```java
import java.util.ArrayList;
import java.util.Arrays;

public class ListExample {
    public static void main(String[] args) {
        ArrayList<String> myStringList = new ArrayList<String>(Arrays.asList(
                "first string",
                "second string",
                "third string"
        ));
        System.out.println(myStringList); // -> [first string, second string, third string]
    }
}
```

## Commonly Used Methods

Here are the key methods of the `ArrayList` class:

| Method                         | Return Type                                  | Description                                         |
|--------------------------------|----------------------------------------------|-----------------------------------------------------|
| `add(Element item)`            | boolean                                      | Adds an item to a list                              |
| `get(int index)`               | element at the given index                   | Gets a certain item from a list based on its index  |
| `set(int index, Element item)` | element previously stored at the given index | Updates an item from a list                         |
| `remove(int index)`            | element that is removed at the given index   | Removes an item from a list                         |
| `clear()`                      | void                                         | Removes all items from a list                       |
| `size()`                       | int                                          | Gets the current size of the list                   |
| `contains(Element item)`       | boolean                                      | Checks to see if a list contains a specific item    |
| `isEmpty()`                    | boolean                                      | Checks to see if a list is empty or has a size of 0 |

