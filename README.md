# JAVA COLLECTION PROGRAMS

## Complete Set of 10 Programs with Questions, Solutions & Outputs

---

## Question 1

**Write a java program to read 'N' names of your friends, store it into HashSet and display them in ascending order.**

### Answer:

```java
import java.util.*;

public class FriendsHashSet {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        HashSet<String> friends = new HashSet<>();

        System.out.print("Enter number of friends: ");
        int n = sc.nextInt();
        sc.nextLine();

        System.out.println("Enter names of friends:");
        for(int i = 0; i < n; i++) {
            System.out.print("Friend " + (i+1) + ": ");
            friends.add(sc.nextLine());
        }

        ArrayList<String> sortedList = new ArrayList<>(friends);
        Collections.sort(sortedList);

        System.out.println("\nFriends names in ascending order:");
        for(String name : sortedList) {
            System.out.println(name);
        }
        sc.close();
    }
}
```

### Output:

```
Enter number of friends: 5
Enter names of friends:
Friend 1: Alice
Friend 2: David
Friend 3: Bob
Friend 4: Charlie
Friend 5: Bob

Friends names in ascending order:
Alice
Bob
Charlie
David
```

---

## Question 2

**Write a Java program to create LinkedList of String objects and perform the following:**

- **(i) Add element at the end of the list**
- **(ii) Delete first element of the list**
- **(iii) Display the contents of list in reverse order**

### Answer:

```java
import java.util.*;

public class LinkedListString {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of initial elements: ");
        int n = sc.nextInt();
        sc.nextLine();

        System.out.println("Enter elements:");
        for(int i = 0; i < n; i++) {
            System.out.print("Element " + (i+1) + ": ");
            list.add(sc.nextLine());
        }

        System.out.println("\nOriginal List: " + list);

        System.out.print("\nEnter element to add at end: ");
        String newElement = sc.nextLine();
        list.addLast(newElement);
        System.out.println("After adding at end: " + list);

        if(!list.isEmpty()) {
            String removed = list.removeFirst();
            System.out.println("\nRemoved first element: " + removed);
            System.out.println("After removing first: " + list);
        }

        System.out.println("\nList in reverse order:");
        for(int i = list.size() - 1; i >= 0; i--) {
            System.out.println(list.get(i));
        }
        sc.close();
    }
}
```

### Output:

```
Enter number of initial elements: 4
Enter elements:
Element 1: Apple
Element 2: Banana
Element 3: Cherry
Element 4: Date

Original List: [Apple, Banana, Cherry, Date]

Enter element to add at end: Elderberry
After adding at end: [Apple, Banana, Cherry, Date, Elderberry]

Removed first element: Apple
After removing first: [Banana, Cherry, Date, Elderberry]

List in reverse order:
Elderberry
Date
Cherry
Banana
```

---

## Question 3

**Write a Java program to store city names and their STD codes using an appropriate collection and perform following operations:**

- **(i) Add a new city and its code (No duplicates)**
- **(ii) Remove a city from the collection**
- **(iii) Search for a city name and display the code**

### Answer:

```java
import java.util.*;

public class CitySTDCode {
    public static void main(String[] args) {
        HashMap<String, String> cityMap = new HashMap<>();
        Scanner sc = new Scanner(System.in);

        cityMap.put("Mumbai", "022");
        cityMap.put("Delhi", "011");
        cityMap.put("Pune", "020");

        while(true) {
            System.out.println("\n=== City STD Code Manager ===");
            System.out.println("1. Add new city");
            System.out.println("2. Remove city");
            System.out.println("3. Search city");
            System.out.println("4. Display all cities");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();
            sc.nextLine();

            switch(choice) {
                case 1:
                    System.out.print("Enter city name: ");
                    String city = sc.nextLine();
                    if(cityMap.containsKey(city)) {
                        System.out.println("City already exists!");
                    } else {
                        System.out.print("Enter STD code: ");
                        String code = sc.nextLine();
                        cityMap.put(city, code);
                        System.out.println("City added successfully!");
                    }
                    break;

                case 2:
                    System.out.print("Enter city name to remove: ");
                    String removeCity = sc.nextLine();
                    if(cityMap.remove(removeCity) != null) {
                        System.out.println("City removed successfully!");
                    } else {
                        System.out.println("City not found!");
                    }
                    break;

                case 3:
                    System.out.print("Enter city name to search: ");
                    String searchCity = sc.nextLine();
                    String code = cityMap.get(searchCity);
                    if(code != null) {
                        System.out.println("STD Code for " + searchCity + ": " + code);
                    } else {
                        System.out.println("City not found!");
                    }
                    break;

                case 4:
                    System.out.println("\nAll Cities and STD Codes:");
                    for(Map.Entry<String, String> entry : cityMap.entrySet()) {
                        System.out.println(entry.getKey() + " : " + entry.getValue());
                    }
                    break;

                case 5:
                    System.out.println("Exiting...");
                    sc.close();
                    return;

                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}
```

### Output:

```
=== City STD Code Manager ===
1. Add new city
2. Remove city
3. Search city
4. Display all cities
5. Exit
Enter choice: 1
Enter city name: Kolkata
Enter STD code: 033
City added successfully!

=== City STD Code Manager ===
1. Add new city
2. Remove city
3. Search city
4. Display all cities
5. Exit
Enter choice: 3
Enter city name to search: Pune
STD Code for Pune: 020

=== City STD Code Manager ===
1. Add new city
2. Remove city
3. Search city
4. Display all cities
5. Exit
Enter choice: 4

All Cities and STD Codes:
Mumbai : 022
Pune : 020
Kolkata : 033
Delhi : 011
```

---

## Question 4

**Write a Java program to accept 'n' integers from the user and store them in a collection. Display them in the sorted order. The collection should not accept duplicate elements. Search for a particular element using predefined search method in the Collection framework.**

### Answer:

```java
import java.util.*;

public class SortedSetWithSearch {
    public static void main(String[] args) {
        TreeSet<Integer> numbers = new TreeSet<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of integers: ");
        int n = sc.nextInt();

        System.out.println("Enter integers:");
        for(int i = 0; i < n; i++) {
            System.out.print("Number " + (i+1) + ": ");
            numbers.add(sc.nextInt());
        }

        System.out.println("\nIntegers in sorted order (duplicates removed):");
        System.out.println(numbers);

        System.out.print("\nEnter number to search: ");
        int search = sc.nextInt();

        if(numbers.contains(search)) {
            System.out.println(search + " is present in the collection");
        } else {
            System.out.println(search + " is not present in the collection");
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of integers: 7
Enter integers:
Number 1: 45
Number 2: 12
Number 3: 78
Number 4: 23
Number 5: 12
Number 6: 90
Number 7: 34

Integers in sorted order (duplicates removed):
[12, 23, 34, 45, 78, 90]

Enter number to search: 23
23 is present in the collection
```

---

## Question 5

**Write a java program to create a TreeSet, add some colors (String) and print out the content of TreeSet in ascending order.**

### Answer:

```java
import java.util.*;

public class ColorTreeSet {
    public static void main(String[] args) {
        TreeSet<String> colors = new TreeSet<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of colors: ");
        int n = sc.nextInt();
        sc.nextLine();

        System.out.println("Enter colors:");
        for(int i = 0; i < n; i++) {
            System.out.print("Color " + (i+1) + ": ");
            colors.add(sc.nextLine());
        }

        System.out.println("\nColors in ascending order:");
        for(String color : colors) {
            System.out.println(color);
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of colors: 6
Enter colors:
Color 1: Red
Color 2: Blue
Color 3: Green
Color 4: Yellow
Color 5: Blue
Color 6: Orange

Colors in ascending order:
Blue
Green
Orange
Red
Yellow
```

---

## Question 6

**Write a java program to accept 'N' integers from a user. Store and display integers in sorted order having proper collection class. The collection should not accept duplicate elements.**

### Answer:

```java
import java.util.*;

public class SortedIntegersNoDuplicates {
    public static void main(String[] args) {
        TreeSet<Integer> numbers = new TreeSet<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of integers: ");
        int n = sc.nextInt();

        System.out.println("Enter integers:");
        for(int i = 0; i < n; i++) {
            System.out.print("Integer " + (i+1) + ": ");
            int num = sc.nextInt();
            if(!numbers.add(num)) {
                System.out.println("  (Duplicate! Not added)");
            }
        }

        System.out.println("\nIntegers in sorted order:");
        System.out.println(numbers);

        System.out.println("\nDetailed display:");
        for(Integer num : numbers) {
            System.out.println(num);
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of integers: 8
Enter integers:
Integer 1: 50
Integer 2: 20
Integer 3: 80
Integer 4: 20
  (Duplicate! Not added)
Integer 5: 65
Integer 6: 30
Integer 7: 50
  (Duplicate! Not added)
Integer 8: 10

Integers in sorted order:
[10, 20, 30, 50, 65, 80]

Detailed display:
10
20
30
50
65
80
```

---

## Question 7

**Write a java program to accept 'N' Integers from a user store them into LinkedList Collection and display only negative integers.**

### Answer:

```java
import java.util.*;

public class LinkedListNegative {
    public static void main(String[] args) {
        LinkedList<Integer> numbers = new LinkedList<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of integers: ");
        int n = sc.nextInt();

        System.out.println("Enter integers:");
        for(int i = 0; i < n; i++) {
            System.out.print("Integer " + (i+1) + ": ");
            numbers.add(sc.nextInt());
        }

        System.out.println("\nAll integers: " + numbers);

        System.out.println("\nNegative integers:");
        boolean found = false;
        for(Integer num : numbers) {
            if(num < 0) {
                System.out.println(num);
                found = true;
            }
        }

        if(!found) {
            System.out.println("No negative integers found!");
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of integers: 8
Enter integers:
Integer 1: 25
Integer 2: -15
Integer 3: 30
Integer 4: -7
Integer 5: 42
Integer 6: -23
Integer 7: 10
Integer 8: -5

All integers: [25, -15, 30, -7, 42, -23, 10, -5]

Negative integers:
-15
-7
-23
-5
```

---

## Question 8

**Write a java program to accept 'N' Subject Names from a user store them into LinkedList Collection and Display them by using Iterator interface.**

### Answer:

```java
import java.util.*;

public class SubjectLinkedList {
    public static void main(String[] args) {
        LinkedList<String> subjects = new LinkedList<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of subjects: ");
        int n = sc.nextInt();
        sc.nextLine();

        System.out.println("Enter subject names:");
        for(int i = 0; i < n; i++) {
            System.out.print("Subject " + (i+1) + ": ");
            subjects.add(sc.nextLine());
        }

        System.out.println("\nSubjects using Iterator:");
        Iterator<String> iterator = subjects.iterator();
        int count = 1;
        while(iterator.hasNext()) {
            System.out.println(count + ". " + iterator.next());
            count++;
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of subjects: 5
Enter subject names:
Subject 1: Mathematics
Subject 2: Physics
Subject 3: Chemistry
Subject 4: Computer Science
Subject 5: English

Subjects using Iterator:
1. Mathematics
2. Physics
3. Chemistry
4. Computer Science
5. English
```

---

## Question 9

**Write a Java program to create LinkedList of integer objects and perform the following:**

- **(i) Add element at first position**
- **(ii) Delete last element**
- **(iii) Display the size of link list**

### Answer:

```java
import java.util.*;

public class LinkedListIntegerOps {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of initial elements: ");
        int n = sc.nextInt();

        System.out.println("Enter integers:");
        for(int i = 0; i < n; i++) {
            System.out.print("Integer " + (i+1) + ": ");
            list.add(sc.nextInt());
        }

        System.out.println("\nOriginal List: " + list);
        System.out.println("Size: " + list.size());

        System.out.print("\nEnter integer to add at first position: ");
        int newElement = sc.nextInt();
        list.addFirst(newElement);
        System.out.println("After adding at first: " + list);
        System.out.println("Size: " + list.size());

        if(!list.isEmpty()) {
            int removed = list.removeLast();
            System.out.println("\nRemoved last element: " + removed);
            System.out.println("After removing last: " + list);
            System.out.println("Final Size: " + list.size());
        }

        sc.close();
    }
}
```

### Output:

```
Enter number of initial elements: 5
Enter integers:
Integer 1: 10
Integer 2: 20
Integer 3: 30
Integer 4: 40
Integer 5: 50

Original List: [10, 20, 30, 40, 50]
Size: 5

Enter integer to add at first position: 5
After adding at first: [5, 10, 20, 30, 40, 50]
Size: 6

Removed last element: 50
After removing last: [5, 10, 20, 30, 40]
Final Size: 5
```

---

## Question 10

**Write a java program to accept 'N' student names through command line, store them into the appropriate Collection and display them by using Iterator and ListIterator interface.**

### Answer:

```java
import java.util.*;

public class StudentNamesIterator {
    public static void main(String[] args) {

        if(args.length == 0) {
            System.out.println("No student names provided!");
            System.out.println("Usage: java StudentNamesIterator name1 name2 name3 ...");
            return;
        }

        ArrayList<String> students = new ArrayList<>();

        System.out.println("Adding " + args.length + " student names...\n");
        for(String name : args) {
            students.add(name);
        }

        System.out.println("=== Using Iterator (Forward) ===");
        Iterator<String> iterator = students.iterator();
        int count = 1;
        while(iterator.hasNext()) {
            System.out.println(count + ". " + iterator.next());
            count++;
        }

        System.out.println("\n=== Using ListIterator (Forward) ===");
        ListIterator<String> listIterator = students.listIterator();
        while(listIterator.hasNext()) {
            int index = listIterator.nextIndex();
            String name = listIterator.next();
            System.out.println("Index " + index + ": " + name);
        }

        System.out.println("\n=== Using ListIterator (Backward) ===");
        while(listIterator.hasPrevious()) {
            int index = listIterator.previousIndex();
            String name = listIterator.previous();
            System.out.println("Index " + index + ": " + name);
        }

        System.out.println("\nTotal students: " + students.size());
    }
}
```

### Output:

```
Command: java StudentNamesIterator Alice Bob Charlie Diana Edward

Adding 5 student names...

=== Using Iterator (Forward) ===
1. Alice
2. Bob
3. Charlie
4. Diana
5. Edward

=== Using ListIterator (Forward) ===
Index 0: Alice
Index 1: Bob
Index 2: Charlie
Index 3: Diana
Index 4: Edward

=== Using ListIterator (Backward) ===
Index 4: Edward
Index 3: Diana
Index 2: Charlie
Index 1: Bob
Index 0: Alice

Total students: 5
```

---

## SUMMARY

### Collections Used:

1. **HashSet** - Unordered collection, no duplicates allowed
2. **LinkedList** - Ordered collection, allows duplicates, efficient insertion/deletion
3. **HashMap** - Key-value pairs, no duplicate keys allowed
4. **TreeSet** - Sorted collection, no duplicates, maintains natural ordering
5. **ArrayList** - Ordered collection, allows duplicates, fast random access

### Key Concepts Covered:

✓ Adding, removing, and searching elements
✓ Iterating using Iterator and ListIterator
✓ Sorting collections (ascending order)
✓ Handling duplicates
✓ Command line arguments
✓ Menu-driven programs
✓ Forward and backward iteration
✓ Size and capacity management

---

**Collection Programs Summary:**

- Total Programs: 10
- Format: Markdown
- Page Size: A4
- Font Recommendations: Courier New (code), Times New Roman (text)
- Font Size: 12pt

---

# JAVA THREADING PROGRAMS

## Complete Set of 10 Programs (Questions 11-20) with Solutions & Outputs

---

## Question 11

**Write a Java program to display all the alphabets between 'A' to 'Z' after every 2 seconds.**

### Answer:

```java
public class AlphabetDisplay extends Thread {
    public void run() {
        try {
            for (char ch = 'A'; ch <= 'Z'; ch++) {
                System.out.println(ch);
                Thread.sleep(2000);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        AlphabetDisplay thread = new AlphabetDisplay();
        thread.start();
        System.out.println("Displaying alphabets A to Z with 2 seconds delay...");
    }
}
```

### Output:

```
Displaying alphabets A to Z with 2 seconds delay...
A
(2 seconds delay)
B
(2 seconds delay)
C
...
Z
```

---

## Question 12

**Write a Java program using Runnable interface to blink Text on the frame.**

### Answer:

```java
import javax.swing.*;
import java.awt.*;

public class BlinkingText extends JFrame implements Runnable {
    private JLabel label;
    private boolean isVisible = true;
    private Thread thread;

    public BlinkingText() {
        setTitle("Blinking Text");
        setSize(400, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());

        label = new JLabel("BLINKING TEXT");
        label.setFont(new Font("Arial", Font.BOLD, 24));
        label.setForeground(Color.RED);
        add(label);

        thread = new Thread(this);
        thread.start();

        setVisible(true);
    }

    public void run() {
        try {
            while (true) {
                Thread.sleep(500);
                isVisible = !isVisible;
                label.setVisible(isVisible);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        new BlinkingText();
    }
}
```

### Output:

```
A window appears with "BLINKING TEXT" that blinks on and off every 500 milliseconds.
The text appears in red and alternates between visible and invisible states.
```

---

## Question 13

**Write a java program to simulate traffic signal using threads.**

### Answer:

```java
import javax.swing.*;
import java.awt.*;

public class TrafficSignal extends JFrame implements Runnable {
    private JPanel redPanel, yellowPanel, greenPanel;
    private Thread thread;

    public TrafficSignal() {
        setTitle("Traffic Signal Simulation");
        setSize(200, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(3, 1));

        redPanel = new JPanel();
        redPanel.setBackground(Color.GRAY);
        add(redPanel);

        yellowPanel = new JPanel();
        yellowPanel.setBackground(Color.GRAY);
        add(yellowPanel);

        greenPanel = new JPanel();
        greenPanel.setBackground(Color.GRAY);
        add(greenPanel);

        thread = new Thread(this);
        thread.start();

        setVisible(true);
    }

    public void run() {
        try {
            while (true) {
                redPanel.setBackground(Color.RED);
                yellowPanel.setBackground(Color.GRAY);
                greenPanel.setBackground(Color.GRAY);
                System.out.println("RED - STOP");
                Thread.sleep(3000);

                redPanel.setBackground(Color.GRAY);
                yellowPanel.setBackground(Color.YELLOW);
                greenPanel.setBackground(Color.GRAY);
                System.out.println("YELLOW - READY");
                Thread.sleep(1000);

                redPanel.setBackground(Color.GRAY);
                yellowPanel.setBackground(Color.GRAY);
                greenPanel.setBackground(Color.GREEN);
                System.out.println("GREEN - GO");
                Thread.sleep(3000);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        new TrafficSignal();
    }
}
```

### Output:

```
RED - STOP
(3 seconds - Red light glows)
YELLOW - READY
(1 second - Yellow light glows)
GREEN - GO
(3 seconds - Green light glows)
RED - STOP
(cycle continues...)
```

---

## Question 14

**Write a Java program to create a thread for moving a ball inside a panel vertically. The ball should be created when the user clicks on the start button.**

### Answer:

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class MovingBall extends JFrame implements ActionListener {
    private BallPanel ballPanel;
    private JButton startButton;

    public MovingBall() {
        setTitle("Moving Ball");
        setSize(400, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        ballPanel = new BallPanel();
        add(ballPanel, BorderLayout.CENTER);

        startButton = new JButton("START");
        startButton.addActionListener(this);
        add(startButton, BorderLayout.SOUTH);

        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        ballPanel.startBall();
        startButton.setEnabled(false);
    }

    public static void main(String[] args) {
        new MovingBall();
    }
}

class BallPanel extends JPanel implements Runnable {
    private int yPosition = 50;
    private int ballSize = 30;
    private Thread thread;
    private boolean running = false;

    public void startBall() {
        if (!running) {
            running = true;
            thread = new Thread(this);
            thread.start();
        }
    }

    public void paintComponent(Graphics g) {
        super.paintComponent(g);
        g.setColor(Color.RED);
        g.fillOval(getWidth() / 2 - ballSize / 2, yPosition, ballSize, ballSize);
    }

    public void run() {
        int direction = 1;
        try {
            while (running) {
                yPosition += direction * 5;

                if (yPosition >= getHeight() - ballSize || yPosition <= 0) {
                    direction *= -1;
                }

                repaint();
                Thread.sleep(50);
            }
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted: " + e.getMessage());
        }
    }
}
```

### Output:

```
A window appears with a START button.
When clicked, a red ball appears and moves vertically up and down within the panel.
The ball bounces when it reaches the top or bottom of the panel.
```

---

## Question 15

**Write a java program to display name and priority of a Thread.**

### Answer:

```java
public class ThreadInfo extends Thread {
    public ThreadInfo(String name, int priority) {
        setName(name);
        setPriority(priority);
    }

    public void run() {
        System.out.println("Thread Name: " + getName());
        System.out.println("Thread Priority: " + getPriority());
        System.out.println("Thread ID: " + getId());
        System.out.println("Is Alive: " + isAlive());
        System.out.println("----------------------------");
    }

    public static void main(String[] args) {
        System.out.println("Main Thread Information:");
        System.out.println("Name: " + Thread.currentThread().getName());
        System.out.println("Priority: " + Thread.currentThread().getPriority());
        System.out.println("\nCreating custom threads...\n");

        ThreadInfo t1 = new ThreadInfo("High Priority Thread", Thread.MAX_PRIORITY);
        ThreadInfo t2 = new ThreadInfo("Normal Priority Thread", Thread.NORM_PRIORITY);
        ThreadInfo t3 = new ThreadInfo("Low Priority Thread", Thread.MIN_PRIORITY);

        t1.start();
        t2.start();
        t3.start();
    }
}
```

### Output:

```
Main Thread Information:
Name: main
Priority: 5

Creating custom threads...

Thread Name: High Priority Thread
Thread Priority: 10
Thread ID: 14
Is Alive: true
----------------------------
Thread Name: Normal Priority Thread
Thread Priority: 5
Thread ID: 15
Is Alive: true
----------------------------
Thread Name: Low Priority Thread
Thread Priority: 1
Thread ID: 16
Is Alive: true
----------------------------
```

---

## Question 16

**Write a Multithreading program in java to display the numbers between 1 to 100 continuously in a TextField by clicking on button. (Use Runnable Interface).**

### Answer:

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class NumberDisplay extends JFrame implements ActionListener {
    private JTextField textField;
    private JButton startButton;
    private NumberThread numberThread;

    public NumberDisplay() {
        setTitle("Number Display");
        setSize(400, 150);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());

        textField = new JTextField(20);
        textField.setFont(new Font("Arial", Font.BOLD, 20));
        textField.setEditable(false);
        add(textField);

        startButton = new JButton("START");
        startButton.addActionListener(this);
        add(startButton);

        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        if (numberThread == null || !numberThread.isRunning()) {
            numberThread = new NumberThread(textField);
            Thread t = new Thread(numberThread);
            t.start();
            startButton.setEnabled(false);
        }
    }

    public static void main(String[] args) {
        new NumberDisplay();
    }
}

class NumberThread implements Runnable {
    private JTextField textField;
    private boolean running = false;

    public NumberThread(JTextField textField) {
        this.textField = textField;
    }

    public boolean isRunning() {
        return running;
    }

    public void run() {
        running = true;
        try {
            for (int i = 1; i <= 100; i++) {
                textField.setText(String.valueOf(i));
                Thread.sleep(100);
            }
            textField.setText("Completed!");
        } catch (InterruptedException e) {
            System.out.println("Thread interrupted: " + e.getMessage());
        }
        running = false;
    }
}
```

### Output:

```
A window appears with a text field and START button.
When clicked, numbers from 1 to 100 display continuously:
1
2
3
...
99
100
Completed!
```

---

## Question 17

**Write a java program to solve producer consumer problem in which a producer produces a value and consumer consume the value before producer generate the next value. (Hint: use thread synchronization)**

### Answer:

```java
class SharedResource {
    private int data;
    private boolean hasData = false;

    public synchronized void produce(int value) {
        while (hasData) {
            try {
                wait();
            } catch (InterruptedException e) {
                System.out.println("Producer interrupted");
            }
        }
        this.data = value;
        System.out.println("Produced: " + value);
        hasData = true;
        notify();
    }

    public synchronized int consume() {
        while (!hasData) {
            try {
                wait();
            } catch (InterruptedException e) {
                System.out.println("Consumer interrupted");
            }
        }
        int value = data;
        System.out.println("Consumed: " + value);
        hasData = false;
        notify();
        return value;
    }
}

class Producer implements Runnable {
    private SharedResource resource;

    public Producer(SharedResource resource) {
        this.resource = resource;
    }

    public void run() {
        for (int i = 1; i <= 10; i++) {
            resource.produce(i);
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                System.out.println("Producer sleep interrupted");
            }
        }
    }
}

class Consumer implements Runnable {
    private SharedResource resource;

    public Consumer(SharedResource resource) {
        this.resource = resource;
    }

    public void run() {
        for (int i = 1; i <= 10; i++) {
            resource.consume();
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                System.out.println("Consumer sleep interrupted");
            }
        }
    }
}

public class ProducerConsumer {
    public static void main(String[] args) {
        SharedResource resource = new SharedResource();

        Thread producerThread = new Thread(new Producer(resource));
        Thread consumerThread = new Thread(new Consumer(resource));

        producerThread.start();
        consumerThread.start();
    }
}
```

### Output:

```
Produced: 1
Consumed: 1
Produced: 2
Consumed: 2
Produced: 3
Consumed: 3
...
Produced: 10
Consumed: 10
```

---

## Question 18

**Write a java program for the implementation of synchronization.**

### Answer:

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
        System.out.println(Thread.currentThread().getName() + " - Count: " + count);
    }

    public int getCount() {
        return count;
    }
}

class CounterThread extends Thread {
    private Counter counter;

    public CounterThread(Counter counter, String name) {
        super(name);
        this.counter = counter;
    }

    public void run() {
        for (int i = 0; i < 5; i++) {
            counter.increment();
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                System.out.println(getName() + " interrupted");
            }
        }
    }
}

public class SynchronizationDemo {
    public static void main(String[] args) {
        Counter counter = new Counter();

        CounterThread t1 = new CounterThread(counter, "Thread-1");
        CounterThread t2 = new CounterThread(counter, "Thread-2");
        CounterThread t3 = new CounterThread(counter, "Thread-3");

        System.out.println("Starting threads with synchronization...\n");

        t1.start();
        t2.start();
        t3.start();

        try {
            t1.join();
            t2.join();
            t3.join();
        } catch (InterruptedException e) {
            System.out.println("Main thread interrupted");
        }

        System.out.println("\nFinal Count: " + counter.getCount());
    }
}
```

### Output:

```
Starting threads with synchronization...

Thread-1 - Count: 1
Thread-2 - Count: 2
Thread-3 - Count: 3
Thread-1 - Count: 4
Thread-2 - Count: 5
...
Thread-3 - Count: 15

Final Count: 15
```

---

## Question 19

**Write a java program that implements a multi-thread application that has three threads. First thread generates random integer number after every one second, if the number is even; second thread computes the square of that number and print it. If the number is odd, the third thread computes the cube of that number and print it.**

### Answer:

```java
import java.util.Random;

class NumberGenerator extends Thread {
    public void run() {
        Random random = new Random();
        try {
            for (int i = 0; i < 10; i++) {
                int number = random.nextInt(100);
                System.out.println("\nGenerated Number: " + number);

                if (number % 2 == 0) {
                    EvenThread evenThread = new EvenThread(number);
                    evenThread.start();
                } else {
                    OddThread oddThread = new OddThread(number);
                    oddThread.start();
                }

                Thread.sleep(1000);
            }
        } catch (InterruptedException e) {
            System.out.println("Generator thread interrupted");
        }
    }
}

class EvenThread extends Thread {
    private int number;

    public EvenThread(int number) {
        this.number = number;
    }

    public void run() {
        int square = number * number;
        System.out.println("Even Number - Square of " + number + " = " + square);
    }
}

class OddThread extends Thread {
    private int number;

    public OddThread(int number) {
        this.number = number;
    }

    public void run() {
        int cube = number * number * number;
        System.out.println("Odd Number - Cube of " + number + " = " + cube);
    }
}

public class MultiThreadApp {
    public static void main(String[] args) {
        System.out.println("Starting Multi-Thread Application...");
        NumberGenerator generator = new NumberGenerator();
        generator.start();
    }
}
```

### Output:

```
Starting Multi-Thread Application...

Generated Number: 42
Even Number - Square of 42 = 1764

Generated Number: 17
Odd Number - Cube of 17 = 4913

Generated Number: 88
Even Number - Square of 88 = 7744
```

---

## Question 20

# Java Program 10: Thread for Printing Text N Times

---

## Question

Write a java program to define a thread for printing text on output screen for 'n' number of times. Create 3 threads and run them. Pass the text 'n' parameters to the thread constructor.

**Example:**
- First thread prints "COVID19" 10 times
- Second thread prints "LOCKDOWN2020" 20 times
- Third thread prints "VACCINATED2021" 30 times

---

## Solution

### Code

```java
class TextPrinter extends Thread {
    private String text;
    private int count;
    
    // Constructor to initialize text and count
    public TextPrinter(String text, int count) {
        this.text = text;
        this.count = count;
    }
    
    // Override run method - executed when thread starts
    public void run() {
        System.out.println("\n" + Thread.currentThread().getName() + 
                          " started printing \"" + text + "\"");
        System.out.println("=".repeat(50));
        
        for (int i = 1; i <= count; i++) {
            System.out.println(Thread.currentThread().getName() + 
                              ": " + text + " - " + i);
            
            try {
                // Small delay to make output visible
                Thread.sleep(50);
            } catch (InterruptedException e) {
                System.out.println("Thread interrupted: " + e.getMessage());
            }
        }
        
        System.out.println("=".repeat(50));
        System.out.println(Thread.currentThread().getName() + 
                          " completed printing \"" + text + "\"");
        System.out.println();
    }
}

public class Program10_TextPrinter {
    public static void main(String[] args) {
        System.out.println("******************************************************");
        System.out.println("    MULTITHREADING PROGRAM - TEXT PRINTER");
        System.out.println("******************************************************");
        
        // Create three threads with different text and count parameters
        TextPrinter thread1 = new TextPrinter("COVID19", 10);
        TextPrinter thread2 = new TextPrinter("LOCKDOWN2020", 20);
        TextPrinter thread3 = new TextPrinter("VACCINATED2021", 30);
        
        // Set thread names for better identification
        thread1.setName("Thread-1");
        thread2.setName("Thread-2");
        thread3.setName("Thread-3");
        
        // Display thread information
        System.out.println("\nThread Information:");
        System.out.println("-".repeat(50));
        System.out.println(thread1.getName() + " will print \"COVID19\" 10 times");
        System.out.println(thread2.getName() + " will print \"LOCKDOWN2020\" 20 times");
        System.out.println(thread3.getName() + " will print \"VACCINATED2021\" 30 times");
        
        // Start all three threads
        System.out.println("\n" + "=".repeat(50));
        System.out.println("Starting all threads...");
        System.out.println("=".repeat(50));
        
        thread1.start();
        thread2.start();
        thread3.start();
        
        // Wait for all threads to complete
        try {
            thread1.join();
            thread2.join();
            thread3.join();
        } catch (InterruptedException e) {
            System.out.println("Main thread interrupted: " + e.getMessage());
        }
        
        System.out.println("\n" + "=".repeat(50));
        System.out.println("All threads have completed execution!");
        System.out.println("=".repeat(50));
    }
}
```

## Output

```
******************************************************
    MULTITHREADING PROGRAM - TEXT PRINTER
******************************************************

Thread Information:
--------------------------------------------------
Thread-1 will print "COVID19" 10 times
Thread-2 will print "LOCKDOWN2020" 20 times
Thread-3 will print "VACCINATED2021" 30 times

==================================================
Starting all threads...
==================================================

Thread-1 started printing "COVID19"
==================================================

Thread-2 started printing "LOCKDOWN2020"
==================================================

Thread-3 started printing "VACCINATED2021"
==================================================
Thread-1: COVID19 - 1
Thread-2: LOCKDOWN2020 - 1
Thread-3: VACCINATED2021 - 1
Thread-1: COVID19 - 2
Thread-2: LOCKDOWN2020 - 2
Thread-3: VACCINATED2021 - 2
Thread-1: COVID19 - 3
Thread-2: LOCKDOWN2020 - 3
Thread-3: VACCINATED2021 - 3
Thread-1: COVID19 - 4
Thread-2: LOCKDOWN2020 - 4
Thread-3: VACCINATED2021 - 4
Thread-1: COVID19 - 5
Thread-2: LOCKDOWN2020 - 5
Thread-3: VACCINATED2021 - 5
Thread-1: COVID19 - 6
Thread-2: LOCKDOWN2020 - 6
Thread-3: VACCINATED2021 - 6
Thread-1: COVID19 - 7
Thread-2: LOCKDOWN2020 - 7
Thread-3: VACCINATED2021 - 7
Thread-1: COVID19 - 8
Thread-2: LOCKDOWN2020 - 8
Thread-3: VACCINATED2021 - 8
Thread-1: COVID19 - 9
Thread-2: LOCKDOWN2020 - 9
Thread-3: VACCINATED2021 - 9
Thread-1: COVID19 - 10
==================================================
Thread-1 completed printing "COVID19"

Thread-2: LOCKDOWN2020 - 10
Thread-3: VACCINATED2021 - 10
Thread-2: LOCKDOWN2020 - 11
Thread-3: VACCINATED2021 - 11
Thread-2: LOCKDOWN2020 - 12
Thread-3: VACCINATED2021 - 12
Thread-2: LOCKDOWN2020 - 13
Thread-3: VACCINATED2021 - 13
Thread-2: LOCKDOWN2020 - 14
Thread-3: VACCINATED2021 - 14
Thread-2: LOCKDOWN2020 - 15
Thread-3: VACCINATED2021 - 15
Thread-2: LOCKDOWN2020 - 16
Thread-3: VACCINATED2021 - 16
Thread-2: LOCKDOWN2020 - 17
Thread-3: VACCINATED2021 - 17
Thread-2: LOCKDOWN2020 - 18
Thread-3: VACCINATED2021 - 18
Thread-2: LOCKDOWN2020 - 19
Thread-3: VACCINATED2021 - 19
Thread-2: LOCKDOWN2020 - 20
==================================================
Thread-2 completed printing "LOCKDOWN2020"

Thread-3: VACCINATED2021 - 20
Thread-3: VACCINATED2021 - 21
Thread-3: VACCINATED2021 - 22
Thread-3: VACCINATED2021 - 23
Thread-3: VACCINATED2021 - 24
Thread-3: VACCINATED2021 - 25
Thread-3: VACCINATED2021 - 26
Thread-3: VACCINATED2021 - 27
Thread-3: VACCINATED2021 - 28
Thread-3: VACCINATED2021 - 29
Thread-3: VACCINATED2021 - 30
==================================================
Thread-3 completed printing "VACCINATED2021"


==================================================
All threads have completed execution!
==================================================
```

---

## Alternative Implementation (Using Runnable Interface)

```java
class TextPrinterRunnable implements Runnable {
    private String text;
    private int count;
    
    public TextPrinterRunnable(String text, int count) {
        this.text = text;
        this.count = count;
    }
    
    public void run() {
        for (int i = 1; i <= count; i++) {
            System.out.println(Thread.currentThread().getName() + 
                              ": " + text + " - " + i);
            try {
                Thread.sleep(50);
            } catch (InterruptedException e) {
                System.out.println(e);
            }
        }
        System.out.println(Thread.currentThread().getName() + " completed!\n");
    }
}

public class Program10_Alternative {
    public static void main(String[] args) {
        // Create Runnable objects
        TextPrinterRunnable r1 = new TextPrinterRunnable("COVID19", 10);
        TextPrinterRunnable r2 = new TextPrinterRunnable("LOCKDOWN2020", 20);
        TextPrinterRunnable r3 = new TextPrinterRunnable("VACCINATED2021", 30);
        
        // Create Thread objects with Runnable
        Thread t1 = new Thread(r1, "Thread-1");
        Thread t2 = new Thread(r2, "Thread-2");
        Thread t3 = new Thread(r3, "Thread-3");
        
        // Start threads
        t1.start();
        t2.start();
        t3.start();
    }
}
```
# JDBC Program List — Java Database Connectivity 

> **Setup Required for All Programs**
> - Install MySQL and create database: `CREATE DATABASE company;`
> - Download `mysql-connector-j.jar` and place it in your project folder
> - Compile: `javac -cp .;mysql-connector-j.jar FileName.java`
> - Run: `java -cp .;mysql-connector-j.jar FileName`
> - Change `DB_USER` / `DB_PASS` to match your MySQL credentials

---

## Program 1

**Question:** Write a Java program to accept the details of Employee (Eno, EName, Designation, Salary) from a user and store it into the database. *(Use Swing)*

```sql
-- Run this in MySQL first
CREATE DATABASE IF NOT EXISTS company;
USE company;
CREATE TABLE IF NOT EXISTS Employee (
    Eno         INT PRIMARY KEY,
    EName       VARCHAR(50),
    Designation VARCHAR(50),
    Salary      DOUBLE
);
```

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.sql.*;

public class Program1_EmployeeSwing extends JFrame implements ActionListener {

    private static final String DB_URL  = "jdbc:mysql://localhost:3306/company";
    private static final String DB_USER = "root";
    private static final String DB_PASS = "password";

    private final JTextField txtEno, txtEname, txtDesig, txtSalary;
    private final JButton    btnInsert, btnClear, btnViewAll;
    private final JTextArea  taOutput;

    public Program1_EmployeeSwing() {
        setTitle("Employee Registration");
        setSize(520, 480);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(new BorderLayout(10, 10));

        JPanel formPanel = new JPanel(new GridBagLayout());
        formPanel.setBorder(BorderFactory.createTitledBorder("Enter Employee Details"));
        GridBagConstraints g = new GridBagConstraints();
        g.insets = new Insets(6, 10, 6, 10);
        g.fill   = GridBagConstraints.HORIZONTAL;

        String[]     labels = {"Employee No:", "Employee Name:", "Designation:", "Salary:"};
        txtEno    = new JTextField(18);
        txtEname  = new JTextField(18);
        txtDesig  = new JTextField(18);
        txtSalary = new JTextField(18);
        JTextField[] fields = {txtEno, txtEname, txtDesig, txtSalary};

        for (int i = 0; i < labels.length; i++) {
            g.gridx = 0; g.gridy = i; g.weightx = 0.3;
            formPanel.add(new JLabel(labels[i]), g);
            g.gridx = 1; g.weightx = 0.7;
            formPanel.add(fields[i], g);
        }

        JPanel btnPanel = new JPanel(new FlowLayout(FlowLayout.CENTER, 15, 5));
        btnInsert  = new JButton("Insert");
        btnClear   = new JButton("Clear");
        btnViewAll = new JButton("View All");
        btnInsert.addActionListener(this);
        btnClear.addActionListener(this);
        btnViewAll.addActionListener(this);
        btnPanel.add(btnInsert);
        btnPanel.add(btnClear);
        btnPanel.add(btnViewAll);

        taOutput = new JTextArea(8, 40);
        taOutput.setEditable(false);
        taOutput.setFont(new Font(Font.MONOSPACED, Font.PLAIN, 12));
        JScrollPane sp = new JScrollPane(taOutput);
        sp.setBorder(BorderFactory.createTitledBorder("Output"));

        add(formPanel, BorderLayout.NORTH);
        add(btnPanel,  BorderLayout.CENTER);
        add(sp,        BorderLayout.SOUTH);
        setLocationRelativeTo(null);
        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == btnClear) {
            txtEno.setText(""); txtEname.setText("");
            txtDesig.setText(""); txtSalary.setText("");
            taOutput.setText(""); return;
        }
        if (e.getSource() == btnViewAll) { displayAll(); return; }

        try {
            int    eno   = Integer.parseInt(txtEno.getText().trim());
            String name  = txtEname.getText().trim();
            String desig = txtDesig.getText().trim();
            double sal   = Double.parseDouble(txtSalary.getText().trim());

            if (name.isEmpty() || desig.isEmpty())
                throw new IllegalArgumentException("Name/Designation cannot be empty.");

            try (Connection con = DriverManager.getConnection(DB_URL, DB_USER, DB_PASS);
                 PreparedStatement ps = con.prepareStatement(
                     "INSERT INTO Employee (Eno, EName, Designation, Salary) VALUES (?,?,?,?)")) {
                ps.setInt(1, eno); ps.setString(2, name);
                ps.setString(3, desig); ps.setDouble(4, sal);
                int rows = ps.executeUpdate();
                taOutput.setText(rows > 0
                    ? "Record inserted: Eno=" + eno + ", " + name + ", " + desig + ", " + sal
                    : "Insert failed.");
                JOptionPane.showMessageDialog(this, "Employee inserted successfully!",
                    "Success", JOptionPane.INFORMATION_MESSAGE);
            }
        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, "Eno and Salary must be valid numbers.",
                "Input Error", JOptionPane.ERROR_MESSAGE);
        } catch (IllegalArgumentException ex) {
            JOptionPane.showMessageDialog(this, ex.getMessage(), "Validation", JOptionPane.WARNING_MESSAGE);
        } catch (SQLException ex) {
            JOptionPane.showMessageDialog(this, "DB Error: " + ex.getMessage(),
                "SQL Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    private void displayAll() {
        StringBuilder sb = new StringBuilder();
        sb.append(String.format("%-6s %-20s %-15s %-10s%n", "Eno", "EName", "Designation", "Salary"));
        sb.append("-".repeat(55)).append("\n");
        try (Connection con = DriverManager.getConnection(DB_URL, DB_USER, DB_PASS);
             ResultSet rs = con.createStatement().executeQuery("SELECT * FROM Employee")) {
            while (rs.next())
                sb.append(String.format("%-6d %-20s %-15s %-10.2f%n",
                    rs.getInt("Eno"), rs.getString("EName"),
                    rs.getString("Designation"), rs.getDouble("Salary")));
        } catch (SQLException ex) { sb.append("Error: ").append(ex.getMessage()); }
        taOutput.setText(sb.toString());
    }

    public static void main(String[] args) {
        try { Class.forName("com.mysql.cj.jdbc.Driver"); }
        catch (ClassNotFoundException ex) { System.err.println("Driver not found."); }
        SwingUtilities.invokeLater(Program1_EmployeeSwing::new);
    }
}
```

**Sample Output:**
```
A Swing window opens with fields: Employee No, Employee Name, Designation, Salary.
After filling and clicking Insert:
  Popup: "Employee inserted successfully!"
  Output area: Record inserted: Eno=101, Alice, Manager, 75000.0

Clicking View All:
Eno    EName                Designation     Salary
-------------------------------------------------------
101    Alice                Manager         75000.00
102    Bob                  Developer       60000.00
```

---

## Program 2

**Question:** Write a Java program for the following:
- i. To create a `Product(Pid, Pname, Price)` table.
- ii. Insert at least five records into the table.
- iii. Display all the records from the table.

```java
import java.sql.*;

public class Program2_ProductTable {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(URL, USER, PASS);
            Statement  st  = con.createStatement();

            // i. Create table
            String createSQL =
                "CREATE TABLE IF NOT EXISTS Product (" +
                "  Pid   INT PRIMARY KEY AUTO_INCREMENT," +
                "  Pname VARCHAR(60)  NOT NULL," +
                "  Price DECIMAL(10,2) NOT NULL" +
                ")";
            st.execute(createSQL);
            System.out.println("Step i  : Product table created successfully.");

            // ii. Insert five records
            st.execute("DELETE FROM Product");
            String insertSQL = "INSERT INTO Product (Pname, Price) VALUES (?,?)";
            PreparedStatement ps = con.prepareStatement(insertSQL);

            Object[][] products = {
                {"Laptop",             55000.00},
                {"Smartphone",         18999.00},
                {"Wireless Mouse",       999.50},
                {"Mechanical Keyboard", 3499.00},
                {"USB-C Hub",           1299.75}
            };

            for (Object[] row : products) {
                ps.setString(1, (String) row[0]);
                ps.setDouble(2, (Double) row[1]);
                ps.addBatch();
            }
            int[] counts = ps.executeBatch();
            System.out.println("Step ii : " + counts.length + " records inserted.");
            ps.close();

            // iii. Display all records
            System.out.println("\nStep iii: All Product Records");
            System.out.println("-".repeat(50));
            System.out.printf("%-5s  %-25s  %s%n", "Pid", "Pname", "Price");
            System.out.println("-".repeat(50));

            ResultSet rs = st.executeQuery("SELECT * FROM Product ORDER BY Pid");
            while (rs.next()) {
                System.out.printf("%-5d  %-25s  %.2f%n",
                    rs.getInt("Pid"),
                    rs.getString("Pname"),
                    rs.getDouble("Price"));
            }
            System.out.println("-".repeat(50));

            rs.close(); st.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("MySQL Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }
}
```

**Sample Output:**
```
Step i  : Product table created successfully.
Step ii : 5 records inserted.

Step iii: All Product Records
--------------------------------------------------
Pid    Pname                      Price
--------------------------------------------------
1      Laptop                     55000.00
2      Smartphone                 18999.00
3      Wireless Mouse             999.50
4      Mechanical Keyboard        3499.00
5      USB-C Hub                  1299.75
--------------------------------------------------
```

---

## Program 3

**Question:** Write a Java program to display information about all columns in the `DONAR` table using `ResultSetMetaData`.

```sql
-- Run in MySQL first
USE company;
CREATE TABLE IF NOT EXISTS DONAR (
    DonorID   INT PRIMARY KEY AUTO_INCREMENT,
    DonorName VARCHAR(60),
    BloodGroup VARCHAR(5),
    DonorAge  INT,
    City      VARCHAR(40)
);
INSERT INTO DONAR (DonorName, BloodGroup, DonorAge, City) VALUES
('Amit Sharma',  'A+', 28, 'Mumbai'),
('Sneha Patil',  'B-', 34, 'Pune'),
('Ravi Kumar',   'O+', 22, 'Delhi');
```

```java
import java.sql.*;

public class Program3_ResultSetMetaData {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(URL, USER, PASS);
            Statement  st  = con.createStatement();

            ResultSet rs = st.executeQuery("SELECT * FROM DONAR");

            // Retrieve metadata
            ResultSetMetaData rsmd = rs.getMetaData();
            int colCount = rsmd.getColumnCount();

            System.out.println("=".repeat(60));
            System.out.println("  Column Information for Table: DONAR");
            System.out.println("=".repeat(60));
            System.out.printf("%-5s %-20s %-15s %-8s %-8s%n",
                "No.", "Column Name", "Data Type", "Size", "Nullable");
            System.out.println("-".repeat(60));

            for (int i = 1; i <= colCount; i++) {
                System.out.printf("%-5d %-20s %-15s %-8d %-8s%n",
                    i,
                    rsmd.getColumnName(i),
                    rsmd.getColumnTypeName(i),
                    rsmd.getColumnDisplaySize(i),
                    rsmd.isNullable(i) == ResultSetMetaData.columnNullable ? "YES" : "NO"
                );
            }

            System.out.println("=".repeat(60));
            System.out.println("Total Columns: " + colCount);
            System.out.println("\nAdditional Info:");
            System.out.println("-".repeat(40));
            for (int i = 1; i <= colCount; i++) {
                System.out.println("Column " + i + " : " + rsmd.getColumnName(i));
                System.out.println("  Table Name   : " + rsmd.getTableName(i));
                System.out.println("  Class Name   : " + rsmd.getColumnClassName(i));
                System.out.println("  Is AutoIncr  : " + rsmd.isAutoIncrement(i));
                System.out.println("  Is ReadOnly  : " + rsmd.isReadOnly(i));
                System.out.println();
            }

            rs.close(); st.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }
}
```

**Sample Output:**
```
============================================================
  Column Information for Table: DONAR
============================================================
No.   Column Name          Data Type       Size     Nullable
------------------------------------------------------------
1     DonorID              INT             11       NO
2     DonorName            VARCHAR         60       YES
3     BloodGroup           VARCHAR         5        YES
4     DonorAge             INT             11       YES
5     City                 VARCHAR         40       YES
============================================================
Total Columns: 5

Additional Info:
----------------------------------------
Column 1 : DonorID
  Table Name   : DONAR
  Class Name   : java.lang.Integer
  Is AutoIncr  : true
  Is ReadOnly  : false
...
```

---

## Program 4

**Question:** Write a Java program to display information about the database and list all the tables in the database. *(Use `DatabaseMetaData`)*

```java
import java.sql.*;

public class Program4_DatabaseMetaData {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(URL, USER, PASS);

            DatabaseMetaData dbmd = con.getMetaData();

            // ── Database Information ──────────────────────
            System.out.println("=".repeat(55));
            System.out.println("        DATABASE INFORMATION");
            System.out.println("=".repeat(55));
            System.out.println("Database Product Name    : " + dbmd.getDatabaseProductName());
            System.out.println("Database Product Version : " + dbmd.getDatabaseProductVersion());
            System.out.println("JDBC Driver Name         : " + dbmd.getDriverName());
            System.out.println("JDBC Driver Version      : " + dbmd.getDriverVersion());
            System.out.println("JDBC URL                 : " + dbmd.getURL());
            System.out.println("Username                 : " + dbmd.getUserName());
            System.out.println("Max Connections          : " + dbmd.getMaxConnections());
            System.out.println("Supports Transactions    : " + dbmd.supportsTransactions());
            System.out.println("Supports Stored Procs    : " + dbmd.supportsStoredProcedures());
            System.out.println("Read Only                : " + dbmd.isReadOnly());
            System.out.println("=".repeat(55));

            // ── List All Tables ───────────────────────────
            System.out.println("\nTables in database 'company':");
            System.out.println("-".repeat(40));
            System.out.printf("%-5s  %-25s  %-10s%n", "No.", "Table Name", "Table Type");
            System.out.println("-".repeat(40));

            String[] types = {"TABLE"};
            ResultSet rs = dbmd.getTables(null, null, "%", types);
            int count = 1;
            while (rs.next()) {
                System.out.printf("%-5d  %-25s  %-10s%n",
                    count++,
                    rs.getString("TABLE_NAME"),
                    rs.getString("TABLE_TYPE"));
            }
            System.out.println("-".repeat(40));
            System.out.println("Total Tables: " + (count - 1));

            rs.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }
}
```

**Sample Output:**
```
=======================================================
        DATABASE INFORMATION
=======================================================
Database Product Name    : MySQL
Database Product Version : 8.0.33
JDBC Driver Name         : MySQL Connector/J
JDBC Driver Version      : mysql-connector-j-8.0.33
JDBC URL                 : jdbc:mysql://localhost:3306/company
Username                 : root@localhost
Max Connections          : 151
Supports Transactions    : true
Supports Stored Procs    : true
Read Only                : false
=======================================================

Tables in database 'company':
----------------------------------------
No.    Table Name                Table Type
----------------------------------------
1      DONAR                     TABLE
2      Employee                  TABLE
3      Product                   TABLE
4      Teacher                   TABLE
----------------------------------------
Total Tables: 4
```

---

## Program 5

**Question:** Write a Java program to accept the details of Teacher (TNo, TName, Subject). Insert at least 5 records into Teacher table and display the details of Teacher who is teaching "JAVA" Subject. *(Use `PreparedStatement` Interface)*

```sql
-- Run in MySQL first
USE company;
CREATE TABLE IF NOT EXISTS Teacher (
    TNo     INT PRIMARY KEY,
    TName   VARCHAR(60),
    Subject VARCHAR(50)
);
```

```java
import java.sql.*;

public class Program5_TeacherPreparedStatement {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(URL, USER, PASS);

            // ── Insert 5 Teacher records ──────────────────
            con.createStatement().execute("DELETE FROM Teacher");

            PreparedStatement psInsert = con.prepareStatement(
                "INSERT INTO Teacher (TNo, TName, Subject) VALUES (?,?,?)");

            Object[][] teachers = {
                {1, "Prof. Anita Desai",   "JAVA"},
                {2, "Prof. Rahul Mehta",   "Python"},
                {3, "Prof. Sneha Joshi",   "JAVA"},
                {4, "Prof. Kiran Patil",   "Database"},
                {5, "Prof. Vijay Sharma",  "C++"}
            };

            for (Object[] t : teachers) {
                psInsert.setInt(1, (Integer) t[0]);
                psInsert.setString(2, (String)  t[1]);
                psInsert.setString(3, (String)  t[2]);
                psInsert.addBatch();
            }
            int[] result = psInsert.executeBatch();
            System.out.println(result.length + " teacher records inserted.\n");
            psInsert.close();

            // ── Display teachers teaching JAVA ────────────
            PreparedStatement psSelect = con.prepareStatement(
                "SELECT * FROM Teacher WHERE Subject = ?");
            psSelect.setString(1, "JAVA");
            ResultSet rs = psSelect.executeQuery();

            System.out.println("Teachers teaching JAVA:");
            System.out.println("-".repeat(45));
            System.out.printf("%-5s  %-25s  %-10s%n", "TNo", "TName", "Subject");
            System.out.println("-".repeat(45));

            boolean found = false;
            while (rs.next()) {
                found = true;
                System.out.printf("%-5d  %-25s  %-10s%n",
                    rs.getInt("TNo"),
                    rs.getString("TName"),
                    rs.getString("Subject"));
            }
            if (!found) System.out.println("No teachers found for JAVA.");
            System.out.println("-".repeat(45));

            rs.close(); psSelect.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }
}
```

**Sample Output:**
```
5 teacher records inserted.

Teachers teaching JAVA:
---------------------------------------------
TNo    TName                      Subject
---------------------------------------------
1      Prof. Anita Desai          JAVA
3      Prof. Sneha Joshi          JAVA
---------------------------------------------
```

---

## Program 6

**Question:** Write a Menu Driven program in Java for the following. Assume Employee table with attributes (ENo, EName, Salary) is already created.
1. Insert  2. Update  3. Display  4. Exit

```java
import java.sql.*;
import java.util.Scanner;

public class Program6_MenuDrivenEmployee {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";
    static Connection con;

    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            con = DriverManager.getConnection(URL, USER, PASS);

            // Ensure table exists
            con.createStatement().execute(
                "CREATE TABLE IF NOT EXISTS Employee (" +
                "  Eno    INT PRIMARY KEY," +
                "  EName  VARCHAR(50)," +
                "  Salary DOUBLE)");

            Scanner sc = new Scanner(System.in);
            int choice;

            do {
                System.out.println("\n===== Employee Menu =====");
                System.out.println("1. Insert");
                System.out.println("2. Update");
                System.out.println("3. Display");
                System.out.println("4. Exit");
                System.out.print("Enter choice: ");
                choice = Integer.parseInt(sc.nextLine().trim());

                switch (choice) {
                    case 1 -> insertEmployee(sc);
                    case 2 -> updateEmployee(sc);
                    case 3 -> displayAll();
                    case 4 -> System.out.println("Exiting... Goodbye!");
                    default -> System.out.println("Invalid choice. Try again.");
                }
            } while (choice != 4);

            sc.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }

    static void insertEmployee(Scanner sc) throws SQLException {
        System.out.print("Enter Employee No   : "); int eno    = Integer.parseInt(sc.nextLine().trim());
        System.out.print("Enter Employee Name : "); String name = sc.nextLine().trim();
        System.out.print("Enter Salary        : "); double sal  = Double.parseDouble(sc.nextLine().trim());

        PreparedStatement ps = con.prepareStatement(
            "INSERT INTO Employee (Eno, EName, Salary) VALUES (?,?,?)");
        ps.setInt(1, eno); ps.setString(2, name); ps.setDouble(3, sal);
        int rows = ps.executeUpdate();
        System.out.println(rows > 0 ? "Employee inserted successfully." : "Insert failed.");
        ps.close();
    }

    static void updateEmployee(Scanner sc) throws SQLException {
        System.out.print("Enter Employee No to update : "); int eno = Integer.parseInt(sc.nextLine().trim());
        System.out.print("Enter new Salary            : "); double sal = Double.parseDouble(sc.nextLine().trim());

        PreparedStatement ps = con.prepareStatement(
            "UPDATE Employee SET Salary = ? WHERE Eno = ?");
        ps.setDouble(1, sal); ps.setInt(2, eno);
        int rows = ps.executeUpdate();
        System.out.println(rows > 0
            ? "Salary updated for Eno=" + eno
            : "No employee found with Eno=" + eno);
        ps.close();
    }

    static void displayAll() throws SQLException {
        ResultSet rs = con.createStatement().executeQuery("SELECT * FROM Employee ORDER BY Eno");
        System.out.println("\n" + "-".repeat(45));
        System.out.printf("%-6s  %-20s  %-10s%n", "Eno", "EName", "Salary");
        System.out.println("-".repeat(45));
        boolean found = false;
        while (rs.next()) {
            found = true;
            System.out.printf("%-6d  %-20s  %-10.2f%n",
                rs.getInt("Eno"), rs.getString("EName"), rs.getDouble("Salary"));
        }
        if (!found) System.out.println("No records found.");
        System.out.println("-".repeat(45));
        rs.close();
    }
}
```

**Sample Output:**
```
===== Employee Menu =====
1. Insert
2. Update
3. Display
4. Exit
Enter choice: 1
Enter Employee No   : 101
Enter Employee Name : Alice
Enter Salary        : 75000
Employee inserted successfully.

Enter choice: 3
---------------------------------------------
Eno     EName                 Salary
---------------------------------------------
101     Alice                 75000.00
---------------------------------------------

Enter choice: 2
Enter Employee No to update : 101
Enter new Salary            : 80000
Salary updated for Eno=101

Enter choice: 4
Exiting... Goodbye!
```

---

## Program 7

**Question:** Write a Java program to delete the details of a given employee (ENo, EName, Salary). Accept employee ID through command line. *(Use `PreparedStatement` Interface)*

```java
import java.sql.*;

public class Program7_DeleteEmployee {

    static final String URL  = "jdbc:mysql://localhost:3306/company";
    static final String USER = "root";
    static final String PASS = "password";

    public static void main(String[] args) {

        // Accept ENo from command line argument
        if (args.length == 0) {
            System.out.println("Usage: java Program7_DeleteEmployee <EmployeeNo>");
            System.out.println("Example: java -cp .;mysql-connector-j.jar Program7_DeleteEmployee 101");
            return;
        }

        int eno;
        try {
            eno = Integer.parseInt(args[0]);
        } catch (NumberFormatException ex) {
            System.err.println("Invalid Employee No. Please enter a valid integer.");
            return;
        }

        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(URL, USER, PASS);

            // First display the record to be deleted
            PreparedStatement psSelect = con.prepareStatement(
                "SELECT * FROM Employee WHERE Eno = ?");
            psSelect.setInt(1, eno);
            ResultSet rs = psSelect.executeQuery();

            if (!rs.next()) {
                System.out.println("No employee found with Eno = " + eno);
                rs.close(); psSelect.close(); con.close(); return;
            }

            System.out.println("Record to be deleted:");
            System.out.println("-".repeat(45));
            System.out.printf("%-6s  %-20s  %-10s%n", "Eno", "EName", "Salary");
            System.out.println("-".repeat(45));
            System.out.printf("%-6d  %-20s  %-10.2f%n",
                rs.getInt("Eno"), rs.getString("EName"), rs.getDouble("Salary"));
            System.out.println("-".repeat(45));
            rs.close(); psSelect.close();

            // Delete using PreparedStatement
            PreparedStatement psDelete = con.prepareStatement(
                "DELETE FROM Employee WHERE Eno = ?");
            psDelete.setInt(1, eno);
            int rows = psDelete.executeUpdate();

            if (rows > 0)
                System.out.println("Employee with Eno=" + eno + " deleted successfully.");
            else
                System.out.println("Deletion failed.");

            psDelete.close(); con.close();

        } catch (ClassNotFoundException ex) {
            System.err.println("Driver not found: " + ex.getMessage());
        } catch (SQLException ex) {
            System.err.println("SQL Error: " + ex.getMessage());
        }
    }
}
```

**Sample Output:**
```
$ java -cp .;mysql-connector-j.jar Program7_DeleteEmployee 101

Record to be deleted:
---------------------------------------------
Eno     EName                 Salary
---------------------------------------------
101     Alice                 80000.00
---------------------------------------------
Employee with Eno=101 deleted successfully.

$ java -cp .;mysql-connector-j.jar Program7_DeleteEmployee 999
No employee found with Eno = 999
```

---

## Program 8

**Question:** Write a Java program to create a PROJECT table with fields `project_id`, `Project_name`, `Project_description`, `Project_Status`. Insert values in the table. Display all the details of the PROJECT table in a tabular format on the screen. *(Using Swing)*

```java
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.sql.*;

public class Program8_ProjectSwing extends JFrame {

    private static final String URL  = "jdbc:mysql://localhost:3306/company";
    private static final String USER = "root";
    private static final String PASS = "password";

    private final JTable     table;
    private final DefaultTableModel model;
    private final JLabel     lblStatus;

    public Program8_ProjectSwing() {
        setTitle("PROJECT Table Viewer");
        setSize(750, 480);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(new BorderLayout(10, 10));

        // ── Header ────────────────────────────────────────
        JLabel header = new JLabel("PROJECT Details", SwingConstants.CENTER);
        header.setFont(new Font("Arial", Font.BOLD, 18));
        header.setBorder(BorderFactory.createEmptyBorder(10, 0, 5, 0));
        add(header, BorderLayout.NORTH);

        // ── Table ─────────────────────────────────────────
        String[] cols = {"Project ID", "Project Name", "Description", "Status"};
        model = new DefaultTableModel(cols, 0) {
            @Override public boolean isCellEditable(int r, int c) { return false; }
        };
        table = new JTable(model);
        table.setRowHeight(24);
        table.getTableHeader().setFont(new Font("Arial", Font.BOLD, 13));
        table.setFont(new Font("Arial", Font.PLAIN, 12));
        table.setSelectionBackground(new Color(173, 216, 230));

        // Column widths
        int[] widths = {80, 160, 280, 100};
        for (int i = 0; i < widths.length; i++)
            table.getColumnModel().getColumn(i).setPreferredWidth(widths[i]);

        JScrollPane sp = new JScrollPane(table);
        sp.setBorder(BorderFactory.createTitledBorder("All Projects"));
        add(sp, BorderLayout.CENTER);

        // ── Button + Status bar ───────────────────────────
        JPanel south = new JPanel(new BorderLayout());
        JButton btnRefresh = new JButton("Refresh Data");
        btnRefresh.addActionListener(e -> loadData());
        JPanel btnPanel = new JPanel();
        btnPanel.add(btnRefresh);
        lblStatus = new JLabel("Ready", SwingConstants.CENTER);
        lblStatus.setFont(new Font("Arial", Font.ITALIC, 11));
        south.add(btnPanel,  BorderLayout.NORTH);
        south.add(lblStatus, BorderLayout.SOUTH);
        add(south, BorderLayout.SOUTH);

        // ── Init DB then load ──────────────────────────────
        initDatabase();
        loadData();

        setLocationRelativeTo(null);
        setVisible(true);
    }

    private void initDatabase() {
        try (Connection con = DriverManager.getConnection(URL, USER, PASS);
             Statement  st  = con.createStatement()) {

            st.execute(
                "CREATE TABLE IF NOT EXISTS PROJECT (" +
                "  project_id          INT PRIMARY KEY AUTO_INCREMENT," +
                "  Project_name        VARCHAR(80)  NOT NULL," +
                "  Project_description VARCHAR(200)," +
                "  Project_Status      VARCHAR(30)" +
                ")");

            // Insert only if empty
            ResultSet rs = st.executeQuery("SELECT COUNT(*) FROM PROJECT");
            rs.next();
            if (rs.getInt(1) == 0) {
                PreparedStatement ps = con.prepareStatement(
                    "INSERT INTO PROJECT (Project_name, Project_description, Project_Status) VALUES (?,?,?)");

                Object[][] data = {
                    {"Hospital Mgmt System",  "Manage patient records and billing",         "Completed"},
                    {"E-Commerce Platform",   "Online shopping with payment gateway",        "In Progress"},
                    {"Library System",        "Book issue, return and fine management",      "Completed"},
                    {"College ERP",           "Automate academic and admin operations",      "In Progress"},
                    {"Chat Application",      "Real-time messaging using WebSocket",         "Pending"},
                };
                for (Object[] row : data) {
                    ps.setString(1, (String) row[0]);
                    ps.setString(2, (String) row[1]);
                    ps.setString(3, (String) row[2]);
                    ps.addBatch();
                }
                ps.executeBatch();
                ps.close();
            }
            rs.close();
            lblStatus.setText("Database initialized.");

        } catch (SQLException ex) {
            lblStatus.setText("DB Init Error: " + ex.getMessage());
        }
    }

    private void loadData() {
        model.setRowCount(0);
        try (Connection con = DriverManager.getConnection(URL, USER, PASS);
             ResultSet  rs  = con.createStatement()
                 .executeQuery("SELECT * FROM PROJECT ORDER BY project_id")) {
            int count = 0;
            while (rs.next()) {
                model.addRow(new Object[]{
                    rs.getInt("project_id"),
                    rs.getString("Project_name"),
                    rs.getString("Project_description"),
                    rs.getString("Project_Status")
                });
                count++;
            }
            lblStatus.setText("Total records loaded: " + count);
        } catch (SQLException ex) {
            lblStatus.setText("Load Error: " + ex.getMessage());
        }
    }

    public static void main(String[] args) {
        try { Class.forName("com.mysql.cj.jdbc.Driver"); }
        catch (ClassNotFoundException ex) { System.err.println("Driver not found."); }
        SwingUtilities.invokeLater(Program8_ProjectSwing::new);
    }
}
```

**Sample Output:**
```
A Swing window titled "PROJECT Table Viewer" opens with a JTable:

+------------+----------------------+--------------------------------+-----------+
| Project ID |   Project Name       |         Description            |  Status   |
+------------+----------------------+--------------------------------+-----------+
|     1      | Hospital Mgmt System | Manage patient records...      | Completed |
|     2      | E-Commerce Platform  | Online shopping with payment.. | In Progr. |
|     3      | Library System       | Book issue, return and fine... | Completed |
|     4      | College ERP          | Automate academic and admin... | In Progr. |
|     5      | Chat Application     | Real-time messaging using...   | Pending   |
+------------+----------------------+--------------------------------+-----------+
Status bar: "Total records loaded: 5"
```

---

## Quick Reference

| Program | Topic | Key Concept |
|---------|-------|-------------|
| 1 | Employee (Swing + Insert) | `JFrame`, `PreparedStatement` |
| 2 | Product (Create/Insert/Display) | `Statement`, `executeBatch()` |
| 3 | DONAR column info | `ResultSetMetaData` |
| 4 | Database & table list | `DatabaseMetaData` |
| 5 | Teacher – filter by subject | `PreparedStatement` SELECT |
| 6 | Menu-driven Employee CRUD | `Scanner`, switch-case, JDBC |
| 7 | Delete by command-line arg | `args[]`, `PreparedStatement` DELETE |
| 8 | Project table (Swing table) | `JTable`, `DefaultTableModel` |

---

## Common Errors & Fixes

| Error | Cause | Fix |
|-------|-------|-----|
| `ClassNotFoundException` | JAR not in classpath | Add `-cp .;mysql-connector-j.jar` |
| `Access denied for user` | Wrong credentials | Check `DB_USER` / `DB_PASS` |
| `Communications link failure` | MySQL not running | Start MySQL service |
| `Table doesn't exist` | DDL not run | Run the SQL setup block first |
| `Duplicate entry for key PRIMARY` | Inserting same PK twice | Use `DELETE` before re-inserting in demo |




## COMPREHENSIVE SUMMARY

### Java Programs Complete Collection:

**Part 1: Collection Programs (Questions 1-10)**

- HashSet, LinkedList, HashMap, TreeSet, ArrayList
- Adding, removing, and searching elements
- Iteration using Iterator and ListIterator
- Sorting and handling duplicates

**Part 2: Threading Programs (Questions 11-20)**

- Thread creation and lifecycle management
- Runnable interface and Thread class
- Thread synchronization and deadlock prevention
- Producer-Consumer pattern
- Thread priorities and scheduling
- GUI-based threading with Swing
- Thread pools and ExecutorService

**Part 3: JBDC Connection and Implementation
- JBDC Connection
- JBDC Statement
- JBDC PreparedStatement
- JBDC DatabaseMetadata
- JBDC DriverMAnagement

### Key Concepts Mastered:

✓ Collection Framework fundamentals
✓ Thread creation and lifecycle
✓ Thread synchronization primitives
✓ Concurrent programming patterns
✓ GUI event handling with threads
✓ Resource management and pooling
✓ Time-based operations
✓ Inter-thread communication
✓ JBDC Connection
✓ Full Core JBDC API
✓ Swing GUI Based Data Entry And Display

---

**Complete Documentation:**

- **Total Programs:** 28 (10 Collection + 10 Threading + 8 JBDC)
- **Format:** Markdown with complete executable code
- **Difficulty Level:** Beginner to Intermediate
- **Topics Covered:** Collections, Threading, Synchronization
- **Page Format:** A4
- **Font Recommendations:** Courier New (code), Times New Roman (text)
- **Font Size:** 12pt

**END OF COMPLETE JAVA PROGRAMS DOCUMENTATION**
