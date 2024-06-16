## 🏛️ Blockchain Fundamentals with Python

Welcome to the **Blockchain Fundamentals** repository! This project provides a comprehensive introduction to blockchain technology using Python, covering key concepts and practical implementations. Perfect for those who want to dive into the world of decentralized technologies.

### 📁 Repository Structure

```
blockchain-fundamentals/
├── README.md
├── blockchain.ipynb
├── requirements.txt
└── .gitignore
```

### 📜 Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Classes and Functions](#classes-and-functions)
6. [Visualization](#visualization)
7. [Contributing](#contributing)

### 📝 Introduction

This project demonstrates the fundamental principles of blockchain technology through a Python implementation. It includes creating a blockchain, adding blocks, mining with proof-of-work, and visualizing a peer-to-peer network.

### ✨ Features

- **Blockchain Implementation**: Core blockchain and block functionalities.
- **Mining**: Simple proof-of-work algorithm.
- **Networking**: Simulated peer-to-peer network.
- **Visualization**: Graphical representation of the blockchain network.

### 🚀 Installation

To get started, clone the repository and install the necessary dependencies:

```bash
git clone https://github.com/yourusername/blockchain-fundamentals.git
cd blockchain-fundamentals
pip install -r requirements.txt
```

### 🛠️ Usage

Open the Jupyter Notebook `blockchain.ipynb` to explore and execute the code. This notebook guides you through the entire process, from blockchain creation to network visualization.

```bash
jupyter notebook blockchain.ipynb
```

### 🧩 Classes and Functions

#### `Block`

```python
class Block:
    def __init__(self, index, previous_hash, timestamp, data, nonce=0):
        self.index = index
        self.previous_hash = previous_hash
        self.timestamp = timestamp
        self.data = data
        self.nonce = nonce
        self.hash = self.calculate_hash()

    def calculate_hash(self):
        sha = hashlib.sha256()
        sha.update(f"{self.index}{self.previous_hash}{self.timestamp}{self.data}{self.nonce}".encode('utf-8'))
        return sha.hexdigest()

    def mine_block(self, difficulty):
        target = '0' * difficulty
        while self.hash[:difficulty] != target:
            self.nonce += 1
            self.hash = self.calculate_hash()
```

#### `Node`

```python
class Node:
    def __init__(self, node_id):
        self.node_id = node_id
        self.blockchain = Blockchain()

    def receive_block(self, block):
        self.blockchain.add_block(block)
```

#### `Blockchain`

```python
class Blockchain:
    def __init__(self):
        self.chain = [self.create_genesis_block()]
        self.difficulty = 2

    def create_genesis_block(self):
        return Block(0, "0", time.time(), "Genesis Block")

    def add_block(self, new_block):
        new_block.previous_hash = self.chain[-1].hash
        new_block.mine_block(self.difficulty)
        self.chain.append(new_block)
```

### 📊 Visualization

The notebook includes code for visualizing the blockchain network using `networkx` and `matplotlib`:

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
nodes = [node1, node2, node3]
G.add_nodes_from(nodes)
edges = [(node1, node2), (node1, node3), (node2, node3)]
G.add_edges_from(edges)

pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True, node_color='skyblue', node_size=600, font_size=10)
plt.axis('off')
plt.show()
```

This visual representation helps in understanding the decentralized nature of blockchain technology.

### 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

---

Feel free to reach out if you have any questions or suggestions. Enjoy exploring blockchain technology! 🚀🔗
