# 🛣️ Delhi–Dehradun Expressway Simulation using Advanced DSA

<div align="center">

![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![STL](https://img.shields.io/badge/STL-Graph%20Algorithms-brightgreen?style=for-the-badge)
![DSA](https://img.shields.io/badge/DSA-Advanced-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

A smart highway simulation system using real-world DSA concepts — graph algorithms, toll management, route optimization, and more — modeled on the **Delhi–Dehradun Expressway**.

[Features](#-features) • [Algorithms Used](#-algorithms--data-structures) • [Getting Started](#-getting-started) • [Sample I/O](#-sample-inputoutput) • [Architecture](#-system-architecture) • [Future Scope](#-future-enhancements)

</div>

---

## 📌 Overview

This project simulates a **smart highway navigation system** inspired by the real Delhi–Dehradun Expressway. It models cities as **graph nodes** and roads as **weighted edges**, then applies advanced DSA techniques to solve problems like:

- Shortest path computation (by time, distance, or toll)
- Minimum spanning tree for road network optimization
- Fuel arbitrage detection via negative cycle identification
- Efficient toll management and range queries

> **Goal:** Bridge the gap between theoretical DSA and real-world system design.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🗺️ **Shortest Path Finder** | Computes optimal routes by time, distance, or toll cost |
| 🌲 **Minimum Spanning Tree** | Finds the most efficient road network using Kruskal's algorithm |
| ⛽ **Fuel Arbitrage Detection** | Detects negative cycles using Bellman-Ford |
| 🚧 **Toll Management System** | Tracks vehicle toll history using Bloom Filter |
| 🏆 **Top-K Toll Plazas** | Retrieves highest-revenue toll plazas using a Max-Heap |
| 📊 **Range Query System** | Efficient prefix/range sum queries with Fenwick Tree |

---

## 🧠 Algorithms & Data Structures

```
Graph (Adjacency List)
 ├── Dijkstra's Algorithm      → Shortest path (time / distance / toll)
 ├── Bellman-Ford Algorithm    → Negative cycle detection (fuel arbitrage)
 ├── Kruskal's Algorithm + DSU → Minimum Spanning Tree
 ├── Fenwick Tree (BIT)        → Range sum queries on toll data
 ├── Bloom Filter              → O(1) vehicle toll-pass verification
 ├── Max-Heap / Priority Queue → Top-K toll plaza queries & Dijkstra
 └── Hash Map (unordered_map) → Fast city/node lookups
```

### ⏱️ Time Complexity

| Algorithm | Time Complexity |
|---|---|
| Dijkstra's Algorithm | `O(E log V)` |
| Bellman-Ford | `O(V × E)` |
| Kruskal's Algorithm | `O(E log E)` |
| Fenwick Tree Query/Update | `O(log N)` |
| Bloom Filter Lookup | `O(1)` |

---

## 🚀 Getting Started

### Prerequisites

- C++17 or later
- g++ compiler
- Standard C++ STL (no external libraries needed)

### Installation & Run

```bash
# Clone the repository
git clone https://github.com/your-username/delhi-dehradun-expressway-dsa.git
cd delhi-dehradun-expressway-dsa

# Compile
g++ -std=c++17 -O2 -o expressway main.cpp

# Run
./expressway
```

> Make sure `expressway.txt` is present in the same directory as the binary.

---

## 📂 Project Structure

```
delhi-dehradun-expressway-dsa/
│
├── main.cpp               # Entry point & menu-driven CLI
├── graph.cpp              # Graph construction and traversal
├── dijkstra.cpp           # Shortest path (Dijkstra)
├── bellman_ford.cpp       # Negative cycle detection
├── kruskal.cpp            # MST using DSU
├── fenwick_tree.cpp       # Range query support
├── bloom_filter.cpp       # Vehicle pass verification
├── expressway.txt         # Input data file
└── README.md
```

---

## 📄 Sample Input/Output

### Input Format (`expressway.txt`)

```
5 5
Delhi 0
Baghpat 47
Shamli 77
Saharanpur 122
Dehradun 192
Delhi Baghpat 47 40 60
Baghpat Shamli 30 25 40
Shamli Saharanpur 45 35 60
Saharanpur Dehradun 70 60 100
Delhi Saharanpur 170 130 180
```

**Format:**
```
<num_cities> <num_roads>
<CityName> <km_from_Delhi>
...
<CityA> <CityB> <distance_km> <time_min> <toll_INR>
```

### Sample Output

```
=== Shortest Path: Delhi → Dehradun ===
Route   : Delhi → Baghpat → Shamli → Saharanpur → Dehradun
Distance: 192 km
Time    : 160 min
Toll    : ₹260

=== Minimum Spanning Tree ===
Edges selected: 4
Total weight  : 192 km

=== Fuel Arbitrage Detection ===
No negative cycle detected. ✅

=== Top-3 Toll Plazas ===
1. Saharanpur  — ₹100
2. Delhi       — ₹60
3. Shamli      — ₹60
```

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────┐
│          expressway.txt             │
│   (Cities, Roads, Weights)          │
└────────────────┬────────────────────┘
                 │ Input Parsing
                 ▼
┌─────────────────────────────────────┐
│         Graph Construction          │
│   Adjacency List (weighted, undirected) │
└────┬──────┬──────┬──────┬──────┬───┘
     │      │      │      │      │
     ▼      ▼      ▼      ▼      ▼
 Dijkstra Bellman Kruskal Fenwick Bloom
 Shortest  -Ford    MST    Tree   Filter
  Path    NegCycle         RQ    Vehicle
                                  Check
     │      │      │      │      │
     └──────┴──────┴──────┴──────┘
                 │
                 ▼
┌─────────────────────────────────────┐
│         CLI Output Results          │
└─────────────────────────────────────┘
```

---

## 🌍 Real-World Applications

- 🗺️ Navigation & GPS route planning systems
- 🏙️ Smart city traffic management
- 💳 Electronic toll collection (ETC) systems
- 🚛 Logistics and freight route optimization
- 🛣️ Highway infrastructure planning

---

## ⚠️ Limitations

- CLI-based only (no graphical interface)
- Uses static input data (no real-time traffic updates)
- No live map rendering or geolocation

---

## 🔮 Future Enhancements

- [ ] 🖥️ Add GUI using React.js or Electron
- [ ] 🌐 Integrate real-time traffic APIs (Google Maps / HERE)
- [ ] 🗺️ Add interactive map visualization (Leaflet.js / Mapbox)
- [ ] 📱 Convert into a full-stack web application
- [ ] 🔄 Support dynamic edge weight updates (road closures, accidents)
- [ ] 📡 Add live vehicle tracking simulation

---

## 📚 Learning Outcomes

- Practical implementation of advanced DSA in a real-world context
- Graph-based problem solving and algorithm selection
- Route optimization and performance trade-offs
- System design thinking beyond academic exercises

---

## 🤝 Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

Made with ❤️ using C++ & DSA | Inspired by the Delhi–Dehradun Expressway

⭐ Star this repo if you found it helpful!

</div>
