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