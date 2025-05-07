
# 🛣️ CityConnect – BFS Traversal Solution

This exercise simulates a road network between cities and uses **Breadth-First Search (BFS)** to check if two cities are connected.

---

## 🧩 Problem Overview

- Each **city** is a node.
- Each **road** is an undirected edge.
- Implement functionality to:
  - Add cities
  - Connect cities with roads
  - Check if two cities are reachable
  - List directly connected cities

---

## ✅ Solution Walkthrough

### 📦 Data Structure

Use a map to represent city connections:

```java
Map<String, List<String>> roadMap = new HashMap<>();
```

---

### 🧱 Step 1: Add a City

```java
public void addCity(String name) {
    roadMap.putIfAbsent(name, new ArrayList<>());
}
```

Adds a city if it doesn't already exist.

---

### 🔗 Step 2: Connect Two Cities

```java
public void connectCities(String city1, String city2) {
    addCity(city1);
    addCity(city2);
    roadMap.get(city1).add(city2);
    roadMap.get(city2).add(city1);
}
```

Creates an undirected road between two cities.

---

### 🚀 Step 3: Check Reachability (BFS)

```java
public boolean isReachable(String source, String destination) {
    Set<String> visited = new HashSet<>();
    Queue<String> queue = new LinkedList<>();
    queue.add(source);

    while (!queue.isEmpty()) {
        String current = queue.poll();
        if (current.equals(destination)) return true;
        visited.add(current);

        for (String neighbor : roadMap.getOrDefault(current, Collections.emptyList())) {
            if (!visited.contains(neighbor)) {
                queue.add(neighbor);
            }
        }
    }
    return false;
}
```

Performs a layer-by-layer search to find a connection.

---

### 🧠 Example: Is Paris connected to Nice?

Cities:
- Paris
- Lyon
- Marseille
- Nice
- Dijon
- Lille

Connections:
- Paris - Lyon
- Paris - Lille
- Lyon - Marseille
- Lyon - Dijon
- Marseille - Nice

---

### 🔄 BFS Order (From Paris to Nice)

1. Paris
2. Lyon
3. Lille
4. Marseille
5. Dijon
6. **Nice** ✅

---

### 📊 BFS Traversal Diagram

![BFS Traversal](bfs_city_traversal.png)

---

## 🧪 Bonus Ideas

- Prevent duplicate connections
- Count hops between cities
- Show shortest path
- Add or remove cities dynamically

---

Happy coding! 🚀
