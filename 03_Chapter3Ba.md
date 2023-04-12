# Chapter 3: Basics of Python Programming Language for Map-Reduce

Welcome detective, to the third chapter of our book on Implementation of Online Algorithms in Map-Reduce Frameworks in Python. In the previous chapter, we introduced you to the basics of Map-Reduce Framework, its core principles and its implementation. In this chapter, we'll be discussing the programming language we'll be using in this book, Python. 

Python is one of the most widely used programming languages among developers and Data Scientists. It has a simple syntax and is easy to learn. Python is highly recommended for implementing Map-Reduce Framework due to its efficiency and its ability to handle large sets of data without breaking a sweat. 

This chapter will provide you with the basics of Python programming needed for implementing Online Algorithms in Map-Reduce Framework. Let's begin our exploration into the language of Python.
# Chapter 3: Basics of Python Programming Language for Map-Reduce

## The Sherlock Holmes Mystery

Greetings my dear detectives. Today, I have an intriguing mystery that requires you to put your programming skills to the test. In the city of MapRedville, a software company had been robbed of their latest version of online algorithm codes. The software company was using these codes to optimize their online applications performance. 

The thief had left behind a clue in the form of a message, which reads:

```python
    print("47592548 745 4826 227 967 379720 47 87 748 7163 90083")
```

The police were unable to decode the message and asked for Sherlock’s assistance in deciphering this code. Sherlock, being a proficient programmer, recognized it as a string of numbers which needs to be 'decoded' using Python programming language. Sherlock decided to use Python in Map-Reduce Framework to aid him in solving this case.

## The Resolution

Sherlock realized that this message could be deciphered using Python programming. He utilized the Map-Reduce Framework to divide the task into smaller chunks and concurrently handle them, maximizing the efficiency of the resources available to him. He implemented an algorithm in Python that could decipher the number string and return the result. Here's the code he wrote:

```python
from mrjob.job import MRJob

class MRDecode(MRJob):
    def mapper(self, _, line):
        nums = list(map(int, line.split()))
        for num in nums:
            yield num % 26, num
        
    def reducer(self, key, values):
        yield key, sum(values)

if __name__ == '__main__':
    MRDecode.run()
```

Sherlock used the above code and executed it using Python in the Map-Reduce Framework. After running the code, the answer was revealed, and he was able to solve the mystery.

The message was simply a coded representation of the 'a' to 'z' alphabets. Each number in the message corresponded to a specific alphabet that could be returned by using the Modulo-26 operation on the number. So, Sherlock's implementation retrieved the message by first computing the Modulo 26 values of each number in the list and then finding the corresponding alphabet to those values.

Thus, we conclude this mystery as Sherlock skillfully leveraged Python with Map-Reduce Framework to help solve a mystery. The knowledge of programming, the Map-Reduce Framework, and Python all proved to be invaluable tools in the detective's quest for answers.
# Chapter 3: Basics of Python Programming Language for Map-Reduce

## Explaining the Code

Detective, let's discuss the code used by Sherlock to resolve the mystery. He leveraged the Map-Reduce Framework of Python, which divides the task into smaller chunks and concurrently handled them to maximize the efficiency of the resources available to him. The code he used was written with the help of the MRJob library in Python.

```python
from mrjob.job import MRJob

class MRDecode(MRJob):
    def mapper(self, _, line):
        nums = list(map(int, line.split()))
        for num in nums:
            yield num % 26, num
        
    def reducer(self, key, values):
        yield key, sum(values)

if __name__ == '__main__':
    MRDecode.run()
```

The code contains a class called `MRDecode` that inherited from the base class `MRJob`. The `MRJob` is a library that provides a way to work with large datasets, which allows us to utilize the Map-Reduce framework in Python.

The `mapper` method of the `MRDecode` class performs the initial filtering and mapping of the data. It receives two parameters, `self` which refers to the instance of the class using it and an `_` parameter to indicate the unused parameter. The `line` parameter receives the input string containing the list of numbers to be decoded. The method then converts the string into a list of integers using the `list(map(int, line.split()))` expression. It then loops over each number in the list and calculates `num % 26`, which is the Modulo-26 operation on the number. Lastly, it `yields` the resulting modulo value and the original number through the function call `yield num % 26, num`.

The `reducer` method of the `MRDecode` class takes the output of the `mapper` method and performs a summation of the numbers that have the same Modulo-26 value. It then `yields` the summation result and the Modulo-26 key for each set of numbers with the same Modulo-26 value.

In the last few lines of the code, you'll see an `if` condition that checks if the current file is the main executable. If it is, then the `MRDecode` object is called and the `run()` method is executed, kicking off the Map-Reduce job, and thus resolving the mystery.

In conclusion, Sherlock used Python with the Map-Reduce Framework, to resolve the mystery he faced. By analyzing and processing the numbers, he was able to retrieve the hidden message encoded within them.