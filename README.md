### ✅ Step-by-Step Solution to CityConnect – With Visual and Explanation

Let's build a simplified example where cities are nodes and roads are undirected edges. Here’s a step-by-step breakdown:

---

![image](https://github.com/user-attachments/assets/a3119116-c660-4005-a41a-eefe9d131c2b)


### 🌍 Graph Overview (Above Image)

This graph shows a road network:

```
Paris ─── Lyon ─── Marseille ─── Nice
  │        │
  │        └── Dijon
  └── Lille
```

---

### 🧱 Step 1: Data Structure Design

Use:

* `Map<String, List<String>>` for the graph (adjacency list)
* Each city is a key; each value is a list of directly connected cities

**Java Concept**:

```java
Map<String, List<String>> roadMap = new HashMap<>();
```

---

### 🧩 Step 2: Adding Cities

Method:

```java
public void addCity(String name) {
    roadMap.putIfAbsent(name, new ArrayList<>());
}
```

📘 **Explanation**:

* Only adds if city doesn't already exist.
* Ensures each city has a "friends list" (connected cities).

---

### 🔗 Step 3: Connecting Two Cities

Method:

```java
public void connectCities(String city1, String city2) {
    addCity(city1);
    addCity(city2);
    roadMap.get(city1).add(city2);
    roadMap.get(city2).add(city1);
}
```

📘 **Explanation**:

* Ensures both cities are present.
* Adds bidirectional (undirected) roads.

---

### 🔍 Step 4: Is City Reachable (BFS)

Method:

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

📘 **Explanation**:

* Breadth-First Search: checks city-by-city layer until destination is found or all options are exhausted.
* Prevents revisiting cities using a `Set`.

---

### 📄 Example Trace: `isReachable("Paris", "Nice")`

**Queue Evolution**:

```
[Paris]
→ Poll Paris, add Lyon, Lille
[**Lyon**, Lille]
→ Poll Lyon, add Marseille, Dijon
[**Lille**, Marseille, Dijon]
→ Poll Marseille, add Nice
[**Dijon**, **Nice**] → FOUND!
```

---

### 🧠 How to Read the Diagram:

![image](https://github.com/user-attachments/assets/300ef353-df14-43fb-aea5-239cefcc2fde)


* **Blue arrows** show the order in which cities were visited during BFS.
* **Numbers** next to each city indicate the **visit sequence**.
* **Dashed lines** represent other connections in the network that BFS *did not* follow directly at that step.

### 🔄 BFS Order:

1. **Paris** (start)
2. **Lyon** and **Lille**
3. From Lyon → **Marseille** and **Dijon**
4. From Marseille → **Nice** (target found ✅)

This is a classic BFS wave-like expansion from the source outward.


