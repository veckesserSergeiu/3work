public class Node {
int data;
Node left;
Node right;

public Node(int data) {
this.data = data;
left = null;
right = null;
}
}

 

 

 

 

 

 

 

 

public class BeenaryTree {
Node root;
private Node addRecursive(Node current, int data){
if (current==null){
return new Node(data);
}
if (data< current.data){
current.left = addRecursive(current.left, data);
} else if (data> current.data) {
current.right = addRecursive(current.right, data);
}
else {
return current;
}
return current;
}
public void add(int data) {
root = addRecursive(root, data);
}

public void delete(int data) {
root = deleteRecursive(root, data);
}

private Node deleteRecursive(Node current, int data) {
if (current == null) {
return null;
}

if (data == current.data) {


// Node has no children
if (current.left == null && current.right == null) {
return null;
}

// Node has only one child
if (current.right == null) {
return current.left;
}

if (current.left == null) {
return current.right;
}

// Node has two children
int smallestValue = findSmallestValue(current.right);
current.data = smallestValue;
current.right = deleteRecursive(current.right, smallestValue);
return current;
}

if (data < current.data) {
current.left = deleteRecursive(current.left, data);
return current;
}

current.right = deleteRecursive(current.right, data);
return current;
}

private int findSmallestValue(Node root) {
return root.left == null ? root.data : findSmallestValue(root.left);
}
