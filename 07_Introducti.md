# Introduction

Welcome to the seventh chapter of our book, where we delve into the world of Input and Output Splits in Map-Reduce. We have come a long way from understanding the basics of Map-Reduce and moving on to more complex stages of Map-Reduce programming.

In this chapter, we will understand the concept of Input and Output Splits in Map-Reduce and how they play an important role in optimizing Map-Reduce jobs. We will explore examples that will not only help us understand the concept in detail but also solve a mystery of a burglary in London with the help of the special guest, Doug Cutting.

So, without any further ado, let's begin our journey of understanding Input and Output Splits in Map-Reduce with the help of a thrilling Sherlock Holmes mystery.
# The Case of the Burgled Data

It was a quiet evening in London, when a small software development company reported that their production database had been burgled. The burglars had left no trace of their break-in and had, in fact, taken away the data from the database without leaving a trace. The database contained sensitive information about the company’s clients and the company’s business operations. The local police were baffled and couldn't seem to find any leads. So, our favorite detective, Sherlock Holmes, was called upon to solve this case.

Sherlock Holmes and his trusted partner, Dr. John Watson, arrived at the company’s office to begin their investigation. After a thorough examination of the crime scene, Holmes came to the conclusion that the burglars had used a sophisticated algorithm to extract the data from the company’s database. 

Holmes deduced that the burglars had used a Map-Reduce framework to steal the data, and that they had done so by exploiting the input and output splits of the Map-Reduce framework. After further analysis, Holmes suspected that the burglars had used a technique called 'combining' to compress the output of the Map function before sending it to the Reduce function.

To confirm his hypothesis, Holmes called upon his friend and renowned computer scientist, Doug Cutting, the co-creator of Hadoop and an expert in Map-Reduce programming. Holmes knew that Doug Cutting would have some valuable insights that could help solve the case.

Doug Cutting arrived within an hour, and after examining the data the company had logged, he gave Holmes and Watson a rare glimpse into the inner workings of Map-Reduce.

He explained that in a Map-Reduce framework, the input data is broken down into smaller chunks or “splits”, and then processed by the Map function. The output of the Map function is then further processed by the Reduce function.

However, the output from the Map function can become very large, which can cause performance issues. To avoid this problem, a combining function can be applied to the Map output before it is sent to the Reduce function. This function compresses the output, allowing for much faster processing.

After listening to Doug's explanation, Holmes began working on a plan to catch the burglars. He realized that if he could identify the splits that were accessed by the burglars, he could then trace their data extraction process, and thus identify the burglars.

After analyzing the company's data logs and examining the Map-Reduce system architecture, Holmes finally understood how the burglars had stolen the data. They had identified the most vulnerable split to steal the company's data, and then used combining function to quickly extract and compress the data. Using this technique, they had managed to steal the entire database in a short amount of time.

With this information, Holmes worked with the police to track down the burglars and recover the stolen data. Needless to say, the case was solved, and the perpetrators were brought to justice.

And that concludes our seventh chapter, where we learned about Input and Output Splits in Map-Reduce, how they play a vital role in optimizing Map-Reduce jobs, and how they were exploited by the burglars in our Sherlock Holmes mystery. The mystery's resolution showcases how understanding Map-Reduce concepts can help in solving real-world problems.
## Explanation of the Code

To solve this mystery, we use Python code to simulate the Map-Reduce process and identify the vulnerable data split that the burglars exploited. We will start by creating a simulated version of the database that was burgled, containing fictitious records of customer transactions. 

```python
# Simulate the database records
database = [
    {'customer': 'John Smith', 'product': 'iPhone', 'price': 999},
    {'customer': 'Jane Doe', 'product': 'iPad', 'price': 799},
    {'customer': 'John Smith', 'product': 'MacBook', 'price': 1999},
    {'customer': 'Jane Doe', 'product': 'AirPods', 'price': 149},
    {'customer': 'Bob Johnson', 'product': 'iMac', 'price': 2499},
    {'customer': 'Alice Williams', 'product': 'MacBook Pro', 'price': 2799},
    {'customer': 'Bob Johnson', 'product': 'iPhone', 'price': 999},
    {'customer': 'Alice Williams', 'product': 'iMac', 'price': 2499},
    {'customer': 'Bob Johnson', 'product': 'iPad', 'price': 799},
    {'customer': 'Alice Williams', 'product': 'AirPods', 'price': 149}
]
```
Next, we define our Mapper function, which takes as input a split of the data and outputs a key-value pair for each record. In this case, our key is the customer name, and our value is the price of the product.

```python
# Mapper function
def mapper(record):
    key = record['customer']
    value = record['price']
    yield key, value
```

After defining the Mapper function, we will define a function that will split the data into smaller input splits to be processed by the Map function.

```python
# Input Split function
def input_split(database, num_splits):
    split_size = len(database) // num_splits
    splits = []
    for i in range(num_splits):
        splits.append(database[i * split_size:(i + 1) * split_size])
    return splits
```
This function takes the entire database and splits the records into smaller chunks based on the number of input splits specified in 'num_splits' parameter. It returns a list of the input splits that can be processed by the Map function.

Next, we will define a reduce function that takes as input the key-value pairs from each Map output and combines them into a single output. In this case, we will simply add the price values for each customer.

```python
# Reducer function
def reducer(key, values):
    total = sum(values)
    yield key, total
```
Finally, we will define a function that will apply a combining function on the output of the Map function to compress and optimize the output.

```python
# Combiner function
def combiner(values):
    total = sum(values)
    yield total
```
Once the input and output split functions, Mapper, Reducer, and Combiner functions have been defined, we combine them with our simulated database to simulate the Map-Reduce process.

```python
# Simulation of MapReduce
def simulate_MapReduce(database, num_splits):
    input_splits = input_split(database, num_splits)
    map_outputs = []
    for split in input_splits:
        map_outputs.extend(map(mapper, split))
    sorted_map_outputs = sorted(map_outputs)
    combine_outputs = []
    for key, group in itertools.groupby(sorted_map_outputs, key=lambda x: x[0]):
        combine_outputs.extend(combiner([x[1] for x in group]))
    sorted_combine_outputs = sorted(combine_outputs)
    reduce_output = []
    for key, group in itertools.groupby(sorted_combine_outputs, key=lambda x: x[0]):
        reduce_output.extend(list(reducer(key, [x[1] for x in group])))
    return reduce_output
```
The simulation function takes the database and the number of input splits as its inputs. It then creates these input splits, applies the Map function, sorts the output of the Map function, applies the Combiner function, sorts the output of the Combiner function, and finally applies the Reduce function to get the desired output.

By analyzing the output of this function, we can identify the vulnerable input split and optimize our Map-Reduce job accordingly.

With the help of the simulation code and Doug Cutting's insights into Map-Reduce processes, Sherlock Holmes was able to solve the mystery and identify the vulnerable input split that the burglars exploited to steal the data.