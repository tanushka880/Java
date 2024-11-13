class Node {
    int data;
    Node next;

    // Constructor to create a new node
    public Node(int data) {
        this.data = data;
        this.next = null; // By default, next is null
    }
}

class Insertion {
    Node head; // Head of the list

    // Method to insert a new node at the beginning
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data); // Create a new node
        newNode.next = head;           // Point the new node to the current head
        head = newNode;                // Update head to the new node
    }

    // Method to display the linked list
    public void display() {
        Node current = head;
        if (current == null) {
            System.out.println("List is empty.");
            return;
        }
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }

    // Method to insert a node at the middle of the linked list
    public void insertAtMiddle(int data) {
        // If the list is empty, insert at the beginning
        if (head == null) {
            insertAtBeginning(data);
            return;
        }

        Node slow = head;
        Node fast = head;
        Node newNode = new Node(data);

        // Move fast pointer two steps and slow pointer one step at a time
        while (fast != null && fast.next != null) {
            fast = fast.next.next; // Move fast pointer two steps
            slow = slow.next;       // Move slow pointer one step
        }

        // Now slow pointer is at the middle, insert the new node after it
        newNode.next = slow.next;
        slow.next = newNode;

        System.out.println(data + " inserted at the middle of the list.");
    }

    public static void main(String[] args) {
        Insertion list = new Insertion();

        // Insert elements at the beginning
        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.insertAtBeginning(40);
        list.insertAtBeginning(50);

        // Display the linked list before insertion at middle
        System.out.println("Linked List before insertion at the middle:");
        list.display();

        // Insert an element at the middle
        list.insertAtMiddle(25);

        // Display the linked list after insertion at middle
        System.out.println("Linked List after inserting 25 at the middle:");
        list.display();
    }
}
