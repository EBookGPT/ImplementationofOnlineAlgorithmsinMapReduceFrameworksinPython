# Chapter 22: Social Network Analysis using Map-Reduce and Python

Greetings dear readers! Welcome to the 22nd chapter of our book on Implementation of Online Algorithms in Map-Reduce Frameworks in Python. We hope that you have found the previous chapter on Graph Algorithms in Map-Reduce Framework informative and useful.

In this chapter, we will focus on Social Network Analysis using Map-Reduce and Python. Social Network Analysis is a powerful technique used to analyze social structures and relationships between individuals or entities. It has widespread applications in various fields such as marketing, epidemiology, sociology, etc.

We will demonstrate how to use Map-Reduce Framework to analyze and understand social networks. We will explore various algorithms such as finding influencers, identifying communities, and detecting anomalies in social networks. Moreover, we will implement these algorithms in Python using Map-Reduce Frameworks.

So, are you curious to find how we can solve a mystery in social networks using Map-Reduce and Python? If yes, let's jump into the world of Social Network Analysis!
# Chapter 22: Social Network Analysis using Map-Reduce and Python

## The Mystery

Sherlock Holmes, the greatest detective of all time, received a peculiar case from his client, Mr. John. Mr. John owned a chain of fast-food restaurants and was worried about the decreasing sales. He suspected that one of his employees was sharing confidential information about their new product line with their competitor, which might be the cause of reduced sales.

Mr. John had data from the company's email server, which included metadata such as sender, receiver, date, and time. Sherlock and his assistant, Dr. Watson, decided to analyze the email data to uncover the culprit. After analyzing the data, they realized that they needed to identify the communication pattern between the employees to catch the culprit.

Sherlock decided to employ the technique of Social Network Analysis to investigate the case further. He decided to use Map-Reduce Framework to analyze the email data and identify the potential suspects.

## The Resolution

Sherlock and Watson began by implementing the Map-Reduce Framework in Python to analyze the email traffic between the employees. They mapped the sender and receiver of each email, and the reducer function counted the number of emails exchanged between two employees.

```
# Mapper function for Social Network Analysis
def mapper(email_data):
    sender, receiver = email_data.split(',')
    yield (sender + "," + receiver)


# Reducer function for Social Network Analysis
def reducer(key, value):
    count = sum(value)
    yield key, count
```

After executing the Map-Reduce job, they obtained a list of employees and the number of emails exchanged between them. Then, they applied the algorithm for finding the influencers in the social network. The algorithm identified the employees who were communicating with a large number of other employees.

```
# Algorithm for identifying influencers in the Social Network
def find_influencers(email_data, influencers_threshold):
    influencers = {}
    for key, value in email_data.items():
        if value >= influencers_threshold:
            influencers[key] = value
    return influencers
```

Using the above algorithm, Sherlock and Watson identified the employees who were communicating with a large number of other employees. They deduced that the employee who was communicating with the competitor was probably among them.

Next, they employed the algorithm for identifying the communities in the social network. The algorithm clustered together employees who were communicating with each other more frequently compared to others.

```
# Algorithm for identifying communities in the Social Network
def find_communities(email_data):
    communities = {}
    for key, value in email_data.items():
        sender, receiver = key.split(",")
        if sender not in communities:
            communities[sender] = {sender}
        if receiver not in communities:
            communities[receiver] = {receiver}
        communities[sender].add(receiver)
        communities[receiver].add(sender)
    return [list(communities[community]) for community in set(map(str, communities.values()))]
```

Using the above algorithm, they identified the communities within the email network, which helped them narrow down the suspects.

Finally, Sherlock and Watson applied the algorithm for detecting anomalies in the social network. The algorithm identified the employees who were deviating from the usual pattern of communication within the network.

```
# Algorithm for detecting anomalies in the Social Network
def detect_anomalies(email_data, mean_value, std_dev_value):
    anomalies = {}
    for key, value in email_data.items():
        if value > mean_value + (2 * std_dev_value):
            anomalies[key] = value
    return anomalies
```

Using the above algorithm, Sherlock and Watson identified the employee who was communicating with the competitor and sharing confidential information. They presented the findings to Mr. John, who immediately took action and terminated the employee.

Thus, Sherlock successfully solved the mystery with the help of Social Network Analysis using Map-Reduce Framework and Python.

We hope you enjoyed this mystery and learned something new about the application of Social Network Analysis in real-life scenarios.
# Chapter 22: Social Network Analysis using Map-Reduce and Python

In our Sherlock Holmes mystery, we used Social Network Analysis and Map-Reduce Framework to investigate the communication pattern between employees in a company to identify a possible culprit. In this section, we will explain the code snippets used to solve the mystery.

## Map-Reduce Framework

We implemented a Mapper and Reducer function for the Social Network Analysis. The Mapper function extracted the sender and receiver information from each email record and passed it to the Reducer function.

```python
# Mapper function for Social Network Analysis
def mapper(email_data):
    sender, receiver = email_data.split(',')
    yield (sender + "," + receiver)


# Reducer function for Social Network Analysis
def reducer(key, value):
    count = sum(value)
    yield key, count
```

The Reducer function counted the number of emails exchanged between two employees and returned a list of employees and the number of emails exchanged between them.

## Finding Influencers

We then employed an algorithm to identify the influencers in the social network, which would help us narrow down the list of suspects. The algorithm identified the employees who were communicating with a large number of other employees.

```python
# Algorithm for identifying influencers in the Social Network
def find_influencers(email_data, influencers_threshold):
    influencers = {}
    for key, value in email_data.items():
        if value >= influencers_threshold:
            influencers[key] = value
    return influencers
```

We defined a threshold for the number of employees that an employee should be communicating with, beyond which they would be considered as influencers.

## Finding Communities

We then applied an algorithm to cluster together employees who were communicating with each other more frequently. This algorithm would help us identify the groups within the company, which would be helpful in further narrowing down the suspects.

```python
# Algorithm for identifying communities in the Social Network
def find_communities(email_data):
    communities = {}
    for key, value in email_data.items():
        sender, receiver = key.split(",")
        if sender not in communities:
            communities[sender] = {sender}
        if receiver not in communities:
            communities[receiver] = {receiver}
        communities[sender].add(receiver)
        communities[receiver].add(sender)
    return [list(communities[community]) for community in set(map(str, communities.values()))]
```

This algorithm used the same mapper and reducer functions as before, but clustered together the employees who communicated with each other more frequently.

## Detecting Anomalies

Finally, we applied an algorithm to detect anomalies in the social network, which would help us identify the employee who was deviating from the usual pattern of communication within the network.

```python
# Algorithm for detecting anomalies in the Social Network
def detect_anomalies(email_data, mean_value, std_dev_value):
    anomalies = {}
    for key, value in email_data.items():
        if value > mean_value + (2 * std_dev_value):
            anomalies[key] = value
    return anomalies
```

This algorithm calculated the mean value and standard deviation of the number of emails exchanged between each employee and then identified the employee who was communicating with someone excessively.

With the help of these algorithms and Map-Reduce Framework, we could visualize the network of communication among employees and deduce the possible culprit who might have been communicating with a competitor.