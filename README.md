## 🎓 **Exercise: "CityConnect" – A Road Network CLI App (Guided Assignment)**

### 🧩 Problem Overview

Build a CLI program to manage a network of cities and roads.
Each city is a **node**, and roads are **undirected connections**.
Users can:

* Add cities
* Connect cities with roads
* Check if two cities are reachable
* List all cities directly connected to a given city

---

## 🛠️ Step-by-Step Guidance

### 🧱 Step 1: `CityGraph` Class

Create a class called `CityGraph` to manage your road network.

#### Fields:

```java
// A map that links each city to a list of cities directly connected to it.
Map<String, List<String>> roadMap = new HashMap<>();
```

---

### 🔧 Step 2: Add a City

Method: `addCity(String name)`

```java
// If the city isn't already in the map, add it with an empty list of connected cities.
```

---

### 🔗 Step 3: Connect Two Cities

Method: `connectCities(String city1, String city2)`

```java
// Ensure both cities exist in the map by calling addCity for each.
// Then, add city2 to city1's connection list and vice versa.
// This models an undirected road between them.
```

---

### 📜 Step 4: Get Connected Cities

Method: `getConnectedCities(String city)`

```java
// Return the list of cities connected to the given city.
// If the city doesn't exist, return an empty list.
```

---

### 🚀 Step 5: Check If Reachable (BFS)

Method: `isReachable(String source, String destination)`

```java
// Use a Set to keep track of visited cities.
// Use a Queue to implement Breadth-First Search (BFS).
// Start by adding the source city to the queue.
// While the queue isn't empty:
//   - Poll the current city.
//   - If it's the destination, return true.
//   - Mark it as visited.
//   - Enqueue all unvisited neighbors of the current city.
// If the loop finishes without finding the destination, return false.
```

---

## 🧪 CLI Layer: `Main` Class

Use `Scanner` to read user input. Parse commands using `split("\\s+")`.
Add a loop to handle these commands:

---

### 🔤 Supported Commands:

* `addcity <name>`
  → Add a new city

* `connect <city1> <city2>`
  → Connect two cities with a road

* `reachable <city1> <city2>`
  → Check if there's a path between the two cities

* `list <city>`
  → List all cities directly connected to this city

* `exit`
  → Exit the program

---

### 📘 Extra Challenges (Optional):

* Prevent duplicate connections
* Make it case-insensitive
* Count the number of hops in a connection
* Add a `removeCity` command (harder)
