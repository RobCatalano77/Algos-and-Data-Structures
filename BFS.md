# Breadth First Search

## Description

BFS is an algorithm used for traversing a tree to find a node that satisfies a given criteria. It starts at the root node and searches all nodes at the present depth prior to exploring nodes at the next depth level. Extra memory, usually in the form of a queue, is used to keep track of the child nodes that have not yet been visited. 

NOTE: BFS can be applied to a graph when:

- the starting point / node is given
- measures are taken to avoid traversing the same vertices twice. This may take the form of a "visited" array of Booleans.

### Visual Demonstration (Tree)
In this example, grey means the node is queued, ready to be explored. Black means the node is explored (removed from the queue);

![Alt Text](https://upload.wikimedia.org/wikipedia/commons/4/46/Animated_BFS.gif)

## Java Code Representation (Tree)
```
public Node BFS(Tree tree, Node root, Node target) {
    Queue<Node> queue = new Queue<>();
    queue.enqueue(root);
    while (!queue.isEmpty()) {
        Node curr = queue.dequeue();
        if (curr == target ) return curr;
        if (curr.left != null) {
            queue.enqueue(curr.left);
        }
        if (curr.right != null) {
            queue.enqueue(curr.right);
        }
    }
}
```

### Visual Demonstration (Graph)
NOTE: a '1' in the visited array signifies 'true', meaning it has been visited. A '0' signfies 'false', meaning it hasn't been visited yet.

![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs1.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs2.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs3.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs4.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs5.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs6.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs7.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs8.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs9.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs10.png)
![Alt Text](https://media.geeksforgeeks.org/wp-content/cdn-uploads/bfs11.png)

For a video explanation, check out https://youtu.be/0u78hx-66Xk


## Java Code Representation (Graph)
NOTE: It is assumed that the Graph is implemented with an adjacency matrix - an array of linked lists, with each index of the array representing a vertex, and the linked list containing all of the other vertices it connects to - see the Graphs section for more detail
```
public void BFS(int s) {
    Queue<Integer> queue = new Queue<>();
    boolean[] visited = new boolean[numNodes];
    visited[s] = true;
    queue.enqueue(s);
    while (!queue.isEmpty()) {
        int curr = queue.dequeue();
        // if you're searching for a specific vertex, perform check here on curr
        List<Integer> vertices = adj[curr];
        for (int v : vertices) {
            if (!visited[v]) {
                visited[v] = true;
                queue.enqueue(v);
            }
        }
    }

}
```