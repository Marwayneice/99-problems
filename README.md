# Ninety-Nine Java 8 Problems

This is an adaptation of the [Ninety-Nine Prolog Problems](https://sites.google.com/site/prologsite/prolog-problems) written by Werner Hett at the Berne University of Applied Sciences in Berne, Switzerland.

From the original source:

> The purpose of this problem collection is to give you the opportunity to practice your skills in logic programming. Your goal should be to find the most elegant solution of the given problems. Efficiency is important, but logical clarity is even more crucial. Some of the (easy) problems can be trivially solved using built-in predicates. However, in these cases, you learn more if you try to find your own solution.

> The problems have different levels of difficulty. Those marked with a single asterisk (\*) are easy. If you have successfully solved the preceding problems you should be able to solve them within a few (say 15) minutes. Problems marked with two asterisks (\*\*) are of intermediate difficulty. If you are a skilled Java programmer it shouldn't take you more than 30-90 minutes to solve them. Problems marked with three asterisks (\*\*\*) are more difficult. You may need more time (i.e. a few hours or more) to find a good solution.

I will use Java 8 features wherever it makes sense so that developers can learn how to use new features introduced in Java 8. If you are new to Java 8 then you can learn more about it by following my in-depth [Java 8 tutorial](https://github.com/shekhargulati/java8-the-missing-tutorial).

## Table of Contents

* [Lists](#lists)
* [Arithmetic](#arithmetic)
* [Logic and Codes](#logic-and-codes)
* [Binary Trees](#binary-trees)
* [Multiway Trees](#multiway-trees)
* [Graphs](#graphs)
* [Miscellaneous](#miscellaneous)

## Lists

In Java, lists are instances of `List<T>` sub-types. You could use `ArrayList<T>` or `LinkedList<T>`. `LinkedList` are better suited for writing functional programs because they provide you methods to get the first and last elements of a List. One of the method that you will miss when working with Java LinkedList is `tail`. `tail` gives you everything except the first element. You could easily implement `tail` as shown below.

```java
public static <T> List<T> tail(LinkedList<T> elements) {
    if (elements == null || elements.isEmpty()) {
        throw new NoSuchElementException();
    }
    if (elements.size() == 1) {
        return Collections.emptyList();
    }
    return elements.subList(1, elements.size());
}
```

> Java 8 does not support pattern matching so you have to use if-else in your code.

### [Problem 01 (*) Find the last element of a list](https://github.com/shekhargulati/99-java8-problems/blob/master/src/main/java/com/shekhargulati/ninety_nine_problems/lists/P01.java)

```java
@Test
public void shouldFindLastElementFromAListOfNumbers() throws Exception {
    assertThat(last(asList(1, 1, 2, 3, 5, 8)), is(equalTo(8)));
}
```

All JUnit test cases related to this problem are [here](https://github.com/shekhargulati/99-java8-problems/blob/master/src/test/java/com/shekhargulati/ninety_nine_problems/lists/P01Test.java).
