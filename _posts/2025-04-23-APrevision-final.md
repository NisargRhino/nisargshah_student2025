---
layout: post
comments: True
title: AP CSA Personal Blog - All FRQs & MCs (2019–2024)
permalink: csa/frqs/all/fullreview
---

## 📅 Year: 2019


### 🧪 FRQ #1: APCalendar
**Solution:**
```java
public static int numberOfLeapYears(int year1, int year2) {
    int count = 0;
    for (int year = year1; year <= year2; year++) {
        if (isLeapYear(year)) {
            count++;
        }
    }
    return count;
}

public static int dayOfWeek(int month, int day, int year) {
    int firstDay = firstDayOfYear(year);
    int nthDay = dayOfYear(month, day, year);
    return (firstDay + nthDay - 1) % 7;
}
```
**Feedback:** ✅ Great use of helper methods. Consider edge cases for modular arithmetic.


### 🧪 FRQ #2: StepTracker
**Solution:**
```java
public class StepTracker {
    private int minSteps;
    private int totalSteps;
    private int days;
    private int activeDays;

    public StepTracker(int min) {
        minSteps = min;
        totalSteps = 0;
        days = 0;
        activeDays = 0;
    }

    public void addDailySteps(int steps) {
        totalSteps += steps;
        days++;
        if (steps >= minSteps) {
            activeDays++;
        }
    }

    public int activeDays() {
        return activeDays;
    }

    public double averageSteps() {
        if (days == 0) return 0.0;
        return (double) totalSteps / days;
    }
}
```
**Feedback:** ✅ Solid use of counters and conditions. Good default handling for division by zero.


### ✅ MC Review 2019
**Question:**
```java
What is the output of the following Java snippet?

int[] a = {1, 2, 3, 4};
for (int i = 0; i < a.length; i++) {
    a[i] = a[i] * 2;
}
System.out.println(Arrays.toString(a));
```
**Answer:** `[2, 4, 6, 8]`  
**Explanation:** The loop modifies each array element by multiplying by 2. Arrays.toString prints the updated array.


### OTHER FRQS 2021-2024 and 2019 

## all my frqs were done in a text format order because that replicates the AP exam. 


# FRQ 1- Methods and Control Structures

![My Screenshot]({{ site.baseurl }}/images/image11.png)

# FRQ 2- Classes

![My Screenshot]({{ site.baseurl }}/images/image18.png)

# FRQ 3- Array/ArrayList

![My Screenshot]({{ site.baseurl }}/images/image19.png)

# FRQ 4- Inheritance

![My Screenshot]({{ site.baseurl }}/images/image20.png)





✅ Explanation for this problem
scoreGuess: Loops through all possible starting indices where the guess could be a substring.

substring(i, i + guess.length()) checks each section of the same length as guess.

count * length² rewards longer matches more heavily.

findBetterGuess: Uses scoreGuess() to compare guesses, uses compareTo() as a tiebreaker (alphabetical order).

🛠️ Feedback
Solid solution. Could optimize with .indexOf() in a loop for clarity.

Be cautious of off-by-one errors in substring ranges.



# Extra practice through code bat

- Code bat is a software that I used to practice key concepts from Units 1-10. I did each unit(ex. recursion, arrays, strings etc)

![My Screenshot]({{ site.baseurl }}/images/image12.png)

![My Screenshot]({{ site.baseurl }}/images/image13.png)

![My Screenshot]({{ site.baseurl }}/images/image14.png)


![My Screenshot]({{ site.baseurl }}/images/image15.png)


## Still need to complete AP-1, array-lists and some stuff in 2d arrays. 


# MC preparation

## Done on Barrons 2024 AP CSA Review book

### I completed all of the MCQs that were on barrons, and annotated all of them. Each MC per chapter has 20-25 questions, and I am averaging around an 85-90%.


![My Screenshot]({{ site.baseurl }}/images/image16.png)


![My Screenshot]({{ site.baseurl }}/images/image17.png)



# Feedback
✅ MCQ 1: Array Traversal Logic
Question: A loop iterates through an array of integers, summing the values. Which of the following best describes the result?

Correct Answer: The sum of all integers in the array.

Explanation: This is a classic accumulator pattern, where each element is added to a running total.

Feedback: Watch out for off-by-one errors in the loop bounds or mistakenly initializing the sum to a non-zero value. Always double-check that you're adding, not multiplying or assigning.

✅ MCQ 2: Inheritance and Overriding
Question: A subclass overrides a method from a superclass. What determines which method is executed?

Correct Answer: The type of the object at runtime.

Explanation: Java uses dynamic method dispatch for overridden methods, meaning the version corresponding to the object’s actual type (not the reference type) is used.

Feedback: Many students confuse this with overloading. Overloading is resolved at compile-time, while overriding is resolved at runtime.

✅ MCQ 3: Boolean Logic
Question: Which expression evaluates to true only when one of the conditions is true, but not both?

Correct Answer: The exclusive OR (XOR) condition.

Explanation: XOR logic returns true if exactly one operand is true. If both are false or both are true, the result is false.

Feedback: Be careful with || versus XOR. || is inclusive and will return true even if both sides are true. XOR is stricter.

✅ MCQ 4: ArrayList Behavior
Question: What happens when you modify an ArrayList while iterating over it with a for-each loop?

Correct Answer: It throws a ConcurrentModificationException.

Explanation: The enhanced for-loop uses an internal iterator. Modifying the list structurally while using it this way causes runtime errors.

Feedback: Use an index-based for loop if you need to remove or modify elements during iteration.

✅ MCQ 5: Constructors and Overloading
Question: What happens if a class has no constructor explicitly defined?

Correct Answer: Java provides a default no-argument constructor.

Explanation: This constructor simply allocates memory and initializes default values (e.g., 0, null).

Feedback: Once you define any constructor (even one with parameters), Java will no longer generate a default one. You must define it manually if needed.





## 🧾 Final Summary: Concepts Learned (2019–2024)
- Array traversal and modification
- Conditionals and loops
- Object instantiation and constructors
- Encapsulation and class structure
- Logical problem decomposition
- Understanding randomness, scheduling, and game simulations



```python

```
