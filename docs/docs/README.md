# docs
Documentation of ednoflow


## entities
Current entities are
+ `Node` represents node in graph.
+ `Edge` represents an edge in the graph.
+ `Edge` represents a graph-based network consisting of nodes and edges.
+ `Agent` represents an agent that moves through the graph.


## node as city
```
from ednoflow.core.node import Node

city_a = Node(node_id="A", label="City A")
print(city_a)

# Node(node_id='A', label='City A')
```

## edge as street
```
from ednoflow.core.edge import Edge

city_b = Node(node_id="B", label="City B")
city_c = Node(node_id="C", label="City C")

road_bc = Edge(start_node=city_b, end_node=city_c, weight=15.0)
print(road_bc)

# Edge(start_node=B, end_node=C, weight=15.0)
```

## newtwork as set of cities and streets
```
from ednoflow.core.network import Network

road_ab = Edge(start_node=city_a, end_node=city_b, weight=10.0)

network = Network(network_id="net_1")
network.add_node(city_a)
network.add_node(city_b)
network.add_node(city_c)
network.add_edge(road_ab)
network.add_edge(road_bc)
print(network)

# Network(network_id='net_1', nodes=3, edges=2)
```

## neighboring cities
```
neighbors = network.get_neighbors("B")
print([node.node_id for node in neighbors])

# ['A', 'C']
```

## agent as car
```
from ednoflow.core.agent import Agent;

car_1 = Agent(agent_id="Car1", current_edge=road_ab)
print(car_1)

# Agent(agent_id='Car1', current_edge=(A -> B), position=0.00)
```

## agent move
```
car_1.move_along_edge(0.25)
print(car_1)

# Agent(agent_id='Car1', current_edge=(A -> B), position=0.25)
```

## agent transfer
```
car_1.transfer_to_edge(road_bc)
print(car_1)

# Agent(agent_id='Car1', current_edge=(B -> C), position=0.00)
```
