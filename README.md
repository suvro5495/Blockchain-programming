### Blockchain Fundamentals in Python

---
![Blockchain Technology](https://editor.analyticsvidhya.com/uploads/49174Blockchain-Technology.png)

# 🌐 Blockchain Fundamentals in Python

Welcome to the **Blockchain Fundamentals** GitHub repository! This project demonstrates the basic principles of blockchain technology using Python. It includes the creation of blocks, mining, and a decentralized peer-to-peer network simulation. The code is well-documented and visualizes the blockchain network using `hashlib`, `networkx` and `matplotlib`.

## 📂 Repository Structure

```plaintext
.
├── README.md               # Overview and guide to the repository
├── blockchain.ipynb        # Jupyter Notebook with the blockchain implementation
└── requirements.txt        # List of dependencies required to run the project
```

## 🚀 Getting Started

To get started with this project, follow the instructions below.

### Prerequisites

Ensure you have the following installed:
- Python 3.7+
- Jupyter Notebook

Install the required Python libraries using `pip`:

```bash
pip install -r requirements.txt
```

### Running the Jupyter Notebook

Launch the Jupyter Notebook to explore and run the code interactively:

```bash
jupyter notebook blockchain.ipynb
```

## 📖 Code Overview

### Imports

We start by importing necessary libraries:

```python
import hashlib
import time
import random
import threading
import networkx as nx
import matplotlib.pyplot as plt
```

### Classes

#### Block

```python
class Block:
    def __init__(self, index, previous_hash, timestamp, data, nonce=0):
        self.index = index
        self.previous_hash = previous_hash
        self.timestamp = timestamp
        self.data = data
        self.nonce = nonce
        self.hash = self.calculate_hash()
```

#### Blockchain

```python
class Blockchain:
    def __init__(self):
        self.chain = [self.create_genesis_block()]
        self.difficulty = 2

    def create_genesis_block(self):
        return Block(0, "0", time.time(), "Genesis Block")

    def get_latest_block(self):
        return self.chain[-1]

    def add_block(self, new_block):
        new_block.previous_hash = self.get_latest_block().hash
        new_block.hash = new_block.calculate_hash()
        self.chain.append(new_block)
```

#### Node

```python
class Node:
    def __init__(self, node_id, blockchain):
        self.node_id = node_id
        self.blockchain = blockchain

    def mine_block(self, data):
        # Mining logic
```

### Visualization

We visualize the blockchain network using `networkx` and `matplotlib`:

```python
G = nx.Graph()
G.add_nodes_from([node1, node2, node3])
G.add_edges_from([(node1, node2), (node1, node3), (node2, node3)])

pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True, node_color='skyblue', node_size=600, font_size=10)
plt.axis('off')
plt.show()
```

### Running the Network

The network simulation and block discovery protocol are executed as follows:

```python
if __name__ == '__main__':
    # Create nodes
    node1 = Node("Node1", Blockchain())
    node2 = Node("Node2", Blockchain())
    node3 = Node("Node3", Blockchain())

    # Connect nodes
    connect_nodes(node1, node2)
    connect_nodes(node1, node3)
    connect_nodes(node2, node3)

    # Start mining and broadcasting blocks
    node1.mine_block("First block data")
    node2.mine_block("Second block data")
    node3.mine_block("Third block data")

    # Wait for block propagation
    time.sleep(5)

    # Visualize the network
    visualize_network([node1, node2, node3])
```

## 🛠️ Features

- **Block Creation:** Creating new blocks with unique hashes.
- **Mining:** Mining blocks with a proof-of-work algorithm.
- **Decentralized Network:** Simulating a P2P network with multiple nodes.
- **Visualization:** Visualizing the network graphically.

## 📊 Graphical Representation

Each node in the network is represented by a labeled node in the graph. The edges represent connections between the nodes.

![Blockchain Network](https://unova.io/wp-content/uploads/2021/11/blockchainnetworkunova-1536x1305.png)

## 🌟 Contributions

Contributions are welcome! Please fork this repository and submit pull requests for any improvements or additional features.

---

Feel free to explore the code, run the simulations, and visualize the blockchain network. Happy coding! 😃

---

### Contact

For any queries or discussions, please reach out to the repository maintainer at [suvro5495@gmail.com](suvro5495@gmail.com).

---

**Stay connected and keep exploring the world of blockchain!**

---

Enjoy building and learning with Blockchain Fundamentals in Python! 🚀
