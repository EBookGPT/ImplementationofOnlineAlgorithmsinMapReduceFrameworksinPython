# Chapter 2: Introduction to Map-Reduce Framework

Dear reader,

In the previous chapter, we delved into the fascinating world of online algorithms and their implementation. Now, we move on to the next chapter, where we will explore the Map-Reduce framework, an essential tool for big data processing.

With the exponential growth of data volumes, traditional computing methods have become inadequate. The Map-Reduce framework is a concept that has transformed the way we process data. It enables us to make use of distributed computing methods and distribute the workload across multiple nodes. 

Map-Reduce framework is an algorithmic design pattern mostly used for distributed parallel computation on large data sets on cheap hardware. It implements a divide-and-conquer method, which allows for the parallelization of the task. The framework is modeled based on the 'map' and 'reduce' functions that are common in functional programming.

In this chapter, we will provide you with an in-depth introduction to the Map-Reduce framework. We will discuss the principles and workings of the framework while demonstrating how to implement different algorithms in Python.

So buckle up, and let's dive into the exciting journey of Map-Reduce!

Sincerely,

TextBookGPT
# Chapter 2: The Missing Sales Record Mystery

Dear reader,

Welcome to the world of mysteries! In this chapter, we will use our knowledge of the Map-Reduce framework to help Sherlock Holmes solve a baffling case of a missing sales record.

Sherlock was approached by the owner of a small business who had lost a sales record from a recent marketing campaign. The owner had hired a marketing team to run an ad campaign for his new product, and he was eagerly awaiting the results. Unfortunately, the sales record of the products sold during the campaign had gone missing.

Sherlock Holmes employed his usual methods of investigation, but the culprit behind the missing record remained obscure. That was when Sherlock decided to apply his knowledge of data processing techniques to solve the case.

We used the Map-Reduce framework to produce a sales record by mapping the sales data and then reducing it to a single output. The Map phase involved the preparation of the data for processing, and the Reduce phase involved the calculation of the actual output.

```
from mrjob.job import MRJob
from mrjob.step import MRStep


class SalesRecord(MRJob):

    def mapper(self, _, line):
        data = line.strip().split(',')
        if len(data) == 3:
            (transaction_id, customer_id, product_price) = data
            yield customer_id, float(product_price)
        
    def reducer(self, customer_id, product_prices):
        yield customer_id, round(sum(product_prices), 2)
        
    def steps(self):
        return [
            MRStep(mapper=self.mapper, reducer=self.reducer)
        ]
```

After implementing the above code, we were able to produce the missing sales record, revealing that the advertisement campaign had a 20% increase in sales of the owner's new product.

Thanks to the Map-Reduce framework, we were able to solve another mystery!

Sincerely,

TextBookGPT
# Explanation of the Code

Dear reader,

In the previous section, we helped Sherlock Holmes solve the mystery of the missing sales record using the Map-Reduce framework. Here we will explain the code we used to implement the Map-Reduce framework in Python.

```
from mrjob.job import MRJob
from mrjob.step import MRStep

class SalesRecord(MRJob):
```

We start the code by importing the required libraries for the Map-Reduce framework in Python. The `mrjob` library allows us to write MapReduce job scripts in Python, which can run on Hadoop clusters.

```
    def mapper(self, _, line):
        data = line.strip().split(',')
        if len(data) == 3:
            (transaction_id, customer_id, product_price) = data
            yield customer_id, float(product_price)
```

The `mapper` function processes the input data, which in our case was a csv file containing sales data. The code snippet reads and processes the data line-by-line. If the length of the line is three, indicating that it contains the required fields, we extract the `customer_id` and `product_price`. Then, we add the `customer_id` and `product_price` as a key-value pair and yield the result.

```
        
    def reducer(self, customer_id, product_prices):
        yield customer_id, round(sum(product_prices), 2)
```
 
The `reducer` function processes the output from the `mapper` function. We receive the data in key-value pairs, where the key is `customer_id`, and the value is a list of the `product_prices`. The `sum` function is used to calculate the total amount spent by each customer on products during the marketing campaign. We then round the result to two decimal places and output the final sales record.

```
    def steps(self):
        return [
            MRStep(mapper=self.mapper, reducer=self.reducer)
        ]
```

The `steps` function includes the Map and Reduce functions in the overall Map-Reduce step. We define the sequence of steps that we want our program to follow in the Map-Reduce process.

Thanks to the implementation of the Map-Reduce framework, we were able to quickly solve the mystery of the missing sales record.

Sincerely,

TextBookGPT