# Depth First Search

## Description

DFS is an algorithm used for traversing a tree to find a node that satisfies a given criteria. It starts at the root node, then traverses the left subtree, then the right subtree.  

NOTE: DFS can be applied to a graph when:

- the starting point / node is given
- measures are taken to avoid traversing the same vertices twice. This may take the form of a "visited" array of Booleans.

### Visual Demonstration (Tree)
In this example, the nodes are labelled in the order that they would be visited. Note how the order is always current node, left subtree, right subtree. 

![Alt Text](https://upload.wikimedia.org/wikipedia/commons/1/1f/Depth-first-tree.svg)

## Java Code Representation (Tree)
```
public Node DFS(Node root, Node target) {
    Stack<Node> stack = new Stack<>();;
    stack.push(root);
    while (!stack.isEmpty()) {
        Node curr = stack.pop();
        if (curr.val == target ) return curr;
        if (curr.left != null) {
            stack.push(curr.left);
        }
        if (curr.right != null) {
            stack.push(curr.right);
        }
    }
    // value was not found, return null
    return null;
}
```

### Visual Representation
https://youtu.be/Y40bRyPQQr0  


## Java Code Representation (Graph)
NOTE: It is assumed that the Graph is implemented with an adjacency matrix - an array of lists of integers, with each index of the array representing a vertex, and the list containing all of the other vertices it connects to - see the Graphs section for more detail
```
public void BFS(int s) {
    Queue<Integer> queue = new Queue<>();
    boolean[] visited = new boolean[numNodes];
    visited[s] = true;
    queue.enqueue(s);
    while (!queue.isEmpty()) {
        int curr = queue.dequeue();
        // if you're searching for a specific vertex, perform check here on curr
        // or, print node like in the example above
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