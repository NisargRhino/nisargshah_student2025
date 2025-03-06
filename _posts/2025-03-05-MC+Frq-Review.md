---
layout: post
title: MC+FRQ
categories: ['DevOps']
permalink: /mc
menu: nav/tools_setup.html
toc: True
comments: True
---

## **MCQ Performance Review**
<img width="1791" alt="Image" src="https://github.com/user-attachments/assets/95ddb4b4-0937-4f9c-bc0d-d06153700b84" />

I'm fairly satisfied with this score, especially considering it was my first practice MCQ. For the questions I got wrong, I now understand most of my mistakes and what led to them. Moving forward, I aim to refine these areas and improve before the AP Exams.

### **Areas for Improvement**
<img width="1806" alt="Image" src="https://github.com/user-attachments/assets/2003e480-6e0b-43ed-9b59-d966cdbf0d07" />

- **Recursion:** Improper base case handling and failing to ensure each recursive call reduced the problem effectively.
- **2D Arrays:** Misinterpreted how row and column indices updated within loops, leading to incorrect element placements and variable misunderstandings.
- **Random Number Generation:** Failed to correctly generate independent random values for number cube rolls.
- **Loop Tracking:** Misinterpreted how `while` loops update the board in Question 31, leading to incorrect assumptions about `row--` and `col++`. 

## **Corrections**

### **Question 9: Number Cube Rolls**
![Image](https://github.com/user-attachments/assets/cf01dea9-0f26-4854-9ee5-52605a32bd17)
**Mistake:** I didn’t correctly simulate the independent rolls of two number cubes.
**Correction:** I need to ensure each cube gets a separate random value. Practicing random number generation will help reinforce this concept.

### **Question 16: Result Variable Misunderstanding**
![Image](https://github.com/user-attachments/assets/841f5a85-159c-4998-b335-d1ec2d476865)
**Mistake:** I assumed the variable stored the largest value when it actually stored the column index of the largest value.
**Correction:** I need to pay closer attention to what each variable represents within a method.

### **Question 31: Loop Misinterpretation**
![Image](https://github.com/user-attachments/assets/93e7e122-dc2e-4022-8ae2-c8f5ce969730)
**Mistake:** I misinterpreted how `while` loops updated the board and assumed 'X' placements followed a different pattern.
**Correction:** I should systematically track loop updates to ensure correct pattern recognition.

## **Free Response Questions (FRQ) Solutions**

### **2014 FRQ - Word Scrambler**
This class takes an array of words and creates a scrambled version by recombining word pairs.


```python

class WordScrambler:
    def __init__(self, wordArr):
        """Constructor initializes scrambledWords with mixed words from the given array."""
        self.scrambledWords = self.mixedWords(wordArr)

    def recombine(self, word1, word2):
        """Takes two words and combines them by taking the first half of the first word 
        and the second half of the second word."""
        mid1 = len(word1) // 2
        mid2 = len(word2) // 2
        return word1[:mid1] + word2[mid2:]

    def mixedWords(self, words):
        """Takes an array of words and forms a new array where each pair of words is recombined."""
        mixed = []
        for i in range(0, len(words), 2):
            mixed.append(self.recombine(words[i], words[i + 1]))
            mixed.append(self.recombine(words[i + 1], words[i]))
        return mixed

# Example Usage
words = ["apple", "banana", "cherry", "date"]
scrambler = WordScrambler(words)
scrambler.scrambledWords
    
```

### **2015 FRQ - Diverse Array**
This class determines whether a 2D array is diverse (i.e., all row sums are unique).


```python

class DiverseArray:
    @staticmethod
    def arraySum(arr):
        """Computes the sum of the elements in a one-dimensional array."""
        return sum(arr)

    @staticmethod
    def rowSums(arr2D):
        """Computes the row sums of a two-dimensional array."""
        return [DiverseArray.arraySum(row) for row in arr2D]

    @staticmethod
    def isDiverse(arr2D):
        """Determines if a 2D array is diverse, meaning no two rows have the same sum."""
        sums = DiverseArray.rowSums(arr2D)
        return len(sums) == len(set(sums))

# Example Usage
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
DiverseArray.isDiverse(matrix)  # Output: False (since two rows have the same sum)
    
```
