# Chapter 21: The Curious Case of Graph Algorithms in Map-Reduce Framework

As we continue our journey to explore the use of online algorithms in Map-Reduce frameworks, we now turn our attention to graph algorithms. Graphs are an important data structure that are used to model relationships between objects. Many problems in computer science, network analysis, social network analysis, and bioinformatics can be modeled using graphs.

With the rise of big data, it has become increasingly important to develop distributed algorithms that can operate on large-scale graphs. Map-Reduce is a popular framework that allows us to process large data sets by distributing the computations across a cluster of computers. 

In this chapter, we will explore the use of Map-Reduce for solving various graph problems such as shortest path, connected components, and page ranking. We will also discuss the challenges involved in designing distributed graph algorithms, and how Map-Reduce can help us overcome them.

But first, let us solve the mystery of the disappearance of the famous mathematician and graph theorist, Professor Moriarty. In doing so, we will encounter various graph problems that can be solved using Map-Reduce algorithms. Our investigation will take us through the dark alleys of London, as we follow the clues left by the elusive Moriarty. So come along, dear reader, and let us embark on this exciting journey. 

*(Note to the reader: If you are unfamiliar with the basics of graph theory and Map-Reduce, we recommend that you first read Chapters 19 and 20 of this book respectively, before proceeding with this chapter).*
# Chapter 21: The Curious Case of Graph Algorithms in Map-Reduce Framework

Sherlock Holmes had just returned to his Baker Street flat after an exhausting day of solving crimes when a frantic knock on the door interrupted his thoughts. It was Dr. Watson, who had just received a letter from their old friend, Professor Moriarty. The letter was cryptic and filled with strange symbols and numbers. Watson was concerned, as Moriarty was a renowned mathematician and the message seemed to hint at something ominous.

Holmes put on his thinking cap and set to work deciphering the message. He realized that the symbols and numbers were actually a coded map of London, and that Moriarty had hidden something of great value at a particular location. The problem was that the map was incomplete, and there were several possible locations that matched the available clues.

As he pondered over the problem, Holmes realized that this was a classic graph problem - finding the shortest path from one point to another on a map. He decided to use Map-Reduce to design a distributed algorithm that would allow him to solve the problem efficiently.

Using Python code, Holmes began by constructing a graph of London, with each street intersection represented as a vertex, and each road between two intersections represented as an edge. He then used the Map-Reduce framework to compute the shortest path between the two points on the map.

```
# Constructing the graph of London
G = nx.Graph()
G.add_edges_from(london_streets)

# Defining the Map-Reduce job to compute shortest path
def initialize(graph):
    d = {}
    p = {}
    for node in graph:
        d[node] = float('Inf')
        p[node] = None
    return d,p

def relax(node, neighbor, graph, d, p):
    if d[neighbor] > d[node] + graph[node][neighbor]['weight']:
        d[neighbor] = d[node] + graph[node][neighbor]['weight']
        p[neighbor] = node
    return d, p

def shortest_path(graph, source, dest):
    d, p = initialize(graph)
    d[source] = 0
    for i in range(len(graph)-1):
        for u in graph:
            for v in graph[u]:
                d, p = relax(u, v, graph, d, p)
    path = []
    while dest is not None:
        path.append(dest)
        dest = p[dest]
    return path[::-1]

# Running the Map-Reduce job to find shortest path
start_node = london_map[start_location]
end_node = london_map[end_location]
shortest_path = shortest_path(G, start_node, end_node)
```

As he ran the Map-Reduce job, Holmes waited with bated breath for the results. Within a few minutes, he had his answer. The shortest path led to a small alleyway near Charing Cross Station. He and Watson quickly headed there and found Moriarty, safe and sound, waiting for them with a twinkle in his eye.

Moriarty explained that he had been working on a complex algorithm for solving the shortest path problem on large-scale graphs, and had wanted to test it out in the real world. He had included a few deliberate errors in his map to make things more challenging for Holmes.

Holmes was fascinated by Moriarty's work, and the two of them spent the evening discussing various graph algorithms and how they could be implemented using Map-Reduce. Watson, meanwhile, was just happy that the mystery had been solved, and that everyone was safe.

And thus, the case of the missing mathematician was solved, thanks to the power of online algorithms and Map-Reduce!
Certainly!

To solve the mystery of Professor Moriarty's whereabouts, Sherlock Holmes realized that he needed to find the shortest path between two points on a map of London. He chose to use Map-Reduce to implement this as a distributed algorithm, which would allow for efficient processing of large-scale graphs. Here's how he did it, using Python code:

1. Constructing the Graph

Holmes began by constructing a graph of London, with each street intersection represented as a vertex, and each road between two intersections represented as an edge. He used the `networkx` library in Python to build and manipulate the graph.

2. Defining the Map-Reduce Job to Compute Shortest Path

Next, Holmes defined the Map-Reduce job to compute the shortest path between two points on the graph. He first initialized a dictionary `d` to store the distance of each vertex/node from the source vertex/node, and a dictionary `p` to store the parent of each vertex/node in the shortest path.

He then defined a function `relax()` to relax an edge in the graph if a shorter path was found. This function updates the `d` and `p` dictionaries accordingly. Finally, he defined the `shortest_path()` function, which initializes the `d` and `p` dictionaries for each vertex/node, and runs `relax()` for each edge in the graph using a double nested loop. 

3. Running the Map-Reduce Job to Find Shortest Path

With the Map-Reduce job defined, Holmes then ran it to calculate the shortest path between the two points on the map. He first mapped each node of the graph to a number, to make it easier to compare them. He did this using a dictionary `london_map` that mapped each node to a unique number. 

He then passed the graph, `london_map`, and the start and end locations, to the `shortest_path()` function. The function computed the shortest path from the start location to the end location using the Map-Reduce algorithm, and returned the path.

Holmes and Watson then followed this path to the alleyway where Moriarty was hiding.

And thus, using the power of online algorithms and Map-Reduce, Holmes was able to solve the mystery of Moriarty's whereabouts!