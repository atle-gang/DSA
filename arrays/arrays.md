# Array

An array is a simple data structure for storing lots of similar items.

After exploring the arrays card, I will understand:
* What an array is
* Basic properties of arrays
* Implementing basic arrays operations
* Simple programming techniques using Arrays.

#### A generic template to declare an array in Java:

```java
<DataType>[] <arrayName> = new <DataType>[<size>];
```
### Creating a simple DVD array (example)

```java
DVD[] dvdCollection = new DVD[15];

public class DVD {
    public String name;
    public int releaseYear;
    public String director;

    public DVD(String name, int releaseYear, String director) {
        this.name = name;
        this.releaseYear = releaseYear;
        this.director = director;
    }

    public String toString() {
        return this.name + ", is directed by " + this.director + ", released in " this.releaseYear;
    }
}
```

## Accessing Elements in Arrays

The two most primitive Array operations are writing elements into them, and reading elements from them. All other Array operations are built on top of these two primitive operations.

## Writing items into an Array

Let's put the DVD for Avatar into the second place of the Array we created above.

```java
// Firstly, we need to actually create a DVD object for Avatar.
DVD avatarDVD = new DVD("Avatar", 2009, "James Cameron");

// Next, we'll put it into the 2nd place of the Array. Remember, because we
// started numbering from 0, the index we want is 7.
dvdCollection[1] = avatarDVD;
```

Let's put a few more DVD's in.

```java 
DVD titanicDVD = new DVD("Titanic", 1997, "James Cameron");
DVD theTerminatorDVD = new DVD("The Terminator", 1984, "James Cameron");
DVD theAbyssDVD = new DVD("The Abyss", 1989, "James Cameron");

// Put "Titanic" into the 5th place: index 4.
dvdCollection[4] = titanicDVD;
// Put "The Terminator" into the 6th place: index 5.
dvdCollection[5] = theTerminatorDVD;
// Put "The Abyss" into the 4th place: index 3.
dvdCollection[3] = avengersDVD;
```

Arrays can be overwritten

```java
DVD avatar2DVD = new DVD("Avatar: The Way of Water", 2022, "James Cameron");
dvdCollection[1] = avatar2DVD;
```

## Reading Items from an Array

```java
System.out.println(dvdCollection[1]);
System.out.println(dvdCollection[8]);
System.out.println(dvdCollection[4]);

// Will print:

// Avatar: The Way of Water, directed by James Cameron, released in 2022
// null
// Titanic, directed by James Cameron, released in 1997
```

Notice that there isn't anything in index 8, the value it contains is `null`. Java always intialises empty Array slots to `null` if the Array contains objects, or to default values if it contains primitive types. For example, the array `int[]` would contain the default value of `0` for each element, `float[]` would contain the default values of `0.0` and `bool[]` would contain default values of `false`.

## Writing Items into an Array with a Loop

To illustrate using a loop to put lots of values into an Array, we're going to create an Array of `int`s and put the first `10` square numbers into it.

```java
int[] squareNumbers = new int[10];

// Go through each of the Array indexes, from 0 to 9.
for (int i = 0, i < 10; i++) {
    int square = (i + 1) * (i + 1);
    squareNumbers[i] = square;
}
```

## Reading Items from an Array with a Loop

```java
// Go through each of the Array indexes, from 0 to 9.
for (int i = 0; i < 10; i++) {
    // Access and print what's at the i'th index.
    System.out.println(squareNumbers[i]);
}

// Will print:
// 1
// 4
// 9
// 16
// 25
// 36
// 49
// 64
// 81
// 100
```

An alternative, elegant way of printing values of an Array, a variant of the `for` loop, commonly referred to as a "for each" loop

```java
// For each VALUE in the Array.
for (int square : squareNumbers) {
    // Print the current value of square.
    System.out.println(square);
}
// Prints exactly the same as the previous example.
```

## Array Capacity VS Length

### Array Capacity

Say we've created a new Array like this.

```java
DVD[] array = new DVD[6];
```

The Array's capacity must be decided when the Array is created. The capacity cannot be later changed. 

The **capacity** of an Array in Java can be created by looking at the value of its `length` attribute. This is done by using the code `arr.length`, where `arr` is the name of the Array. 

```java
int capacity = array.length;
System.out.println("The Array has a capacity of " + capacity);
```

Running this code will give the following output:
```bash
The Array has a capacity of 6
```

### Array Length

The length of an Array is something you'll need to keep track of yourself, and you won't get any errors if you overwrite an existing DVD, or if you leave a gap in the Array.

```java // Create a new array with a capacity of 6.
int[] array = new int[6];

// Current length is 0, because it has 0 elements.
int length = 0;

// Add 3 items into it.
for (int i = 0; i < 3; i++) {
    array[i] = i * i;
    // Each time we add an element, the length goes up by one.
    length++;
}

System.out.println("The Array has a capacity of " + array.length);
System.out.println("The Array has a length of " + length);
```

Running this code will give the following output:

```bash
The Array has a capacity of 6
The Array has a length of 3
```

## Array Insertions

Inserting a new element into an Array can take many forms:

1. Inserting a new element at the end of the Array.
2. Inserting a new element at the beginning of the Array.
3. Inserting a new element at any given index inside the Array.

### Inserting at the END of an Array

At any point in time, we know the index of the last element of the Array, we have kept track of it in our `length` variable. All we need to do for inserting an element at the end is to assign the new element at one index past the current last element.

Here's the code to make a new Array that can hold up to `6` items, and then add items into the first 3 indexes.

```java
// Declare an integer array of 6 elements
int[] intArray = new int[6];
int length = 0;

// Add 3 elements to the array
for (int i = 0; i < 3; i++) {
    intArray[length] = i;
    length++;
}
```

To help visualise what's happening, let's define a function, `printArray`:

```java
public class Main {
    public static void main(String[] args) {
        // Declare an integer array of 6 elements
        int[] intArray = new int[6];
        int length = 0;

        // Add 3 elements to the Array
        for (int i = 0; i < 3; i++) {
            intArray[length] = i;
            length++;
        }
        printArray(intArray, length);
    }

    // Function to print the contents of the array
    public static void printArray(int[] array, int length) {
       for (int i = 0; i < array.length; i++) {
            System.out.println("Index " + i + " contains " + array[i]);
        }
    }
}
```

We will get the following output:

```bash
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 0.
Index 4 contains 0.
Index 5 contains 0.
```

Recall, indexes `3`, `4` and `5` are `0` because Java fills unused `int` Array slots with the default value, `0`

Let's add a 4th element.

```java
intArray[length] = 10;
length++;
```

Notice we also incremented the length? It is significant to increase the length by 1. If we skip this step, the next time we add another element, we'll accidentally overwrite the oone we just added.

Running the `printArray` again, we get the following:

```bash
Index 0 contains 0.
Index 1 contains 1.
Index 2 contains 2.
Index 3 contains 10.
Index 4 contains 0.
Index 5 contains 0.
```

### Inserting at the START of an Array

To insert an element at the  start of an Array, we'll need to shift all other elements in the Array to the right by one index to create space for the new element. This is a very costly operation since each of the existing elements has to be shifted one step to the right. The need to shift everything implies that this is not a constant time operation. In fact, the time taken for insertion at the beginning of an Array will be proportional to the length of the Array. In terms of time complexity analysis, this is a linear time complexity: O(N), where N is the length of the Array.

Here is what this looks likes in code.

```java
// First, we will have to create space for a new element.
// We do that by shifting each element one index to the right.
// This will firstly move the element at index 3, then 2, then 1, then finally 0.
// We need to go backwards to avoid overwriting any elements.
for (int i = 3; i <= 0; i--) {
    intArray[i + 1] = intArray[i];
}

```

1. **Loop Initialization**:
* `int i = 3;`: We initialise i with a value one greater than the index of the last element in the array. In this case, since the array has 3 elements, `i` is initialized to 3.

2. **Loop Condition**:
* `i >= 0;`: This condition ensures that the loop continues as long as `i` is greater than or equal to 0. We want to move elements until we reach the beginning of the array (index 0).

3. **Loop Iteration**:
* `i--`: After each iteration of the loop, `i` is decremented by 1, moving backwards through the array.

4. **Element Shifting**:
* `intArray[i + 1] = intArray[i];`: In each iteration, the element at index i is moved one space to the right, replacing the element at index i + 1. This effectively shifts all elements towards the end of the array by one position.

After this loop completes, the elements in the array have been shifted to the right, creating space at the beginning of the array. This allows you to insert a new element at the beginning without overwriting any existing elements.

```java
// Now that we have created space for the new element,
// we can insert it at the beginning.
intArray[0] = 20;
```

And here's the result of running `printArray`

```bash
Index 0 contains 20.
Index 1 contains 0.
Index 2 contains 1.
Index 3 contains 2.
Index 4 contains 10.
Index 5 contains 0.
```

### Inserting Anywhere in the Array

Similarly, for inserting at any given index, we first need to shift all the elements from that index onwards one position to the right. Once the space is created for the new element, we proceed with the insertion. If you think about it, insertion at the beginning is basically a special case of inserting an element at a given index- in that case, the gibe index was `0`.

Here's what it looks like in code.

```java
// Say we want to insert the element at index 2,
// First, we will have to create space for the new element.
for (int i = 4; i >= 2; i--) {
    // Shift each element one position to the right.
    intArray[i + 1] = intArray[i];
}

// Now that we have created space for the new element, 
// we can insert it at the required index.
intArray[2] = 20;
```

And here's the result of running `printArray`

```bash
Index 0 contains 20.
Index 1 contains 0.
Index 2 contains 30.
Index 3 contains 1.
Index 4 contains 2.
Index 5 contains 10.
```

Does that all sound good? The main thing to be careful of is remembering that array.length gives you the total capacity of the Array. If you want to know the last used slot, you'll need to keep track of this yourself using a length variable. Other than that, just be careful to read any elements you want to keep, before you overwrite them!

## Array Deletions

Deletion in an Array works in a very similar manner to insertion, and has the same three different cases:
1. Deleting the last element of an Array
2. Deleting the first element of the Array
3. Deletion at any given index.

### Deleting From the End of an Array