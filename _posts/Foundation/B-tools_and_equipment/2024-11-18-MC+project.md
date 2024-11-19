---
title: Project + Multiple choice 
comments: True
---

<style>
body {
    font-family: 'Arial', sans-serif;
    background-color: #000;
    color: #f2f2f2;
    line-height: 1.6;
    margin: 0;
    padding: 20px;
}

header {
    text-align: center;
    padding: 20px;
    color: #fff;
    background-color: #ff69b4;
    margin-bottom: 30px;
}

h1, h2, h3 {
    color: #ff69b4;
}

code {
    background: #222;
    color: #ff69b4;
    padding: 2px 6px;
    border-radius: 4px;
}

pre {
    background: #222;
    padding: 15px;
    border-radius: 8px;
    color: #ff69b4;
    overflow-x: auto;
}

a {
    color: #ff69b4;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}
</style>


## Introduction



# SCORE: 30/40

Main Idea questions, that I thought I need to review.

<img src="{{ site.baseurl }}/images/mcimage.png" alt="Random"

# Question 1: Interfaces and Polymorphism

One problem focused on implementing a `Vehicle` interface and a `Fleet` class. Here’s the relevant code:

```java
public interface Vehicle {
    /**
     * @return the mileage traveled by this Vehicle
     */
    double getMileage();
}

public class Fleet {
    private ArrayList<Vehicle> myVehicles;

    /**
     * @return the mileage traveled by all vehicles in this Fleet
     */
    public double getTotalMileage() {
        double sum = 0.0;

        for (Vehicle v : myVehicles) {
            sum += /* expression */;
        }

        return sum;
    }
}
```
# The question was to replace /* expression */ in the getTotalMileage method. The options included:

- getMileage(v)
- myVehicles[v].getMileage()
- Vehicle.get(v).getMileage()
- myVehicles.get(v).getMileage()
- v.getMileage()



## Correct Answer: v.getMileage()
Each element in myVehicles is a Vehicle object.
The getMileage() method is defined in the Vehicle interface.
This problem demonstrated how to iterate through a list of polymorphic objects and call their specific methods.


# Question 2: Checking If an Array Is Sorted
This problem required implementing a method to determine if an array is sorted in non-decreasing order. Here's the incomplete method
```java
/**
 * @param data an array of integers
 * @return true if the values in the array are sorted in non-decreasing order
 */
public static boolean isSorted(int[] data) {
    /* missing code */
}
```
The correct implementation was 
```java
for (int k = 1; k < data.length; k++) {
    if (data[k - 1] > data[k]) {
        return false;
    }
}
return true;
```
# Why?
Starting from the second element (index 1), the method compares each element with the previous one.
If any data[k-1] > data[k], the array is not sorted.
This logic ensures the array is checked sequentially without skipping elements.

# Question 3: Understanding the Book and AudioBook Classes
```java
public class Book {
    private int numPages;
    private String bookTitle;

    public Book(int pages, String title) {
        numPages = pages;
        bookTitle = title;
    }

    public String toString() {
        return bookTitle + " " + numPages;
    }

    public int length() {
        return numPages;
    }
}

public class AudioBook extends Book {
    private int numMinutes;

    public AudioBook(int minutes, int pages, String title) {
        super(pages, title);
        numMinutes = minutes;
    }

    public int length() {
        return numMinutes;
    }

    public double pagesPerMinute() {
        return ((double) super.length()) / numMinutes;
    }
}
```

```java
Book[] books = new Book[2];
books[0] = new AudioBook(100, 300, "The Jungle");
books[1] = new Book(400, "Captains Courageous");

System.out.println(books[0].pagesPerMinute());
System.out.println(books[0].toString());
System.out.println(books[0].length());
System.out.println(books[1].toString());
```
## Why will the code fail to compile?

### Options:

- A. Line 2 will not compile because variables of type Book may not refer to variables of type AudioBook.
- B. Line 4 will not compile because variables of type Book may only call methods in the Book class.
- C. Line 5 will not compile because the AudioBook class does not have a method named toString declared or implemented.
- D. Line 6 will not compile because the statement is ambiguous. The compiler cannot determine which length method should be called.
- E. Line 7 will not compile because the element at index 1 in the array named books may not have been initialized.
### Correct Answer: B

## Explanation:
books[0] is declared as type Book. Since pagesPerMinute() is only defined in the AudioBook class, it cannot be called on a variable of type Book. The compiler resolves the method calls based on the declared type of the variable, not the runtime type of the object it references.
This emphasizes the importance of type checking and polymorphism in Java.