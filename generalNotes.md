<h1>Java</h1>
<h2>JVM (Java Virtual Machine)</h2>
There are 3 types of high-level programming languages: <br>
- <strong>Compiled:</strong> The code is compiled (translated) into a machine code that runs on a specific platform (Microsoft/Mac/...) <br>
- <strong>Interpreted:</strong> Translate the code into machine code whenever you run the program, the translation to machine code won't be saved in any form. If you want to rerun the code you have to retranslate the whole code again. That is what makes interpreted programming languages slower than compiled ones. <br>
- <strong>JVM:</strong> The code is first compiled into what is called Bytecode saved in (.class) file the n The Bytecode is interpreted by JVM into the machine code of the platform that the program running on. <br>

<h2>Generics</h2>
Generics are used to generalize the code where it can be used with different data types. Example:
    
    /* 
    You can restrict the type of generic to be the classes that extend a specific class or interface:
    <T extends Class1 & Interface1 & Interface2>
    Remember that you can't extend more than one class but you can extend as much as you want of interfaces.
    */
    public class Test <T>{
      public void print(T v) {
          System.out.println(v);
      }
    }

    //main:
    public class Main {
        public static void main(String[] args) {
            Test<String> T = new Test<>();
            Integer[] init = {1,2,3,4,5,6,7,8,9,10,11,12,13,14};
            List<Integer> l = new ArrayList<>(Arrays.asList(init));
            T.print("ABBAS\nHUSSAIN\nHUSSAIN\nHUSSAIN\n");
            repeatedPrint("HUSSAIN");
            printList(l);
        }
        public static <T> void repeatedPrint(T s){
            System.out.println("\n"+s+"\n"+s);
        }
        //Notice that wildcard "?" can extend a specific class similar to the generic type
        public static void printList(List<?> l){
            for (Object e:l) {
                System.out.println(e);
            }
        }
    }

<h2>Java Collection Framework</h2>
Before we start with the Java collection let's take a look at the idea of wrapper classes; wrapper classes are objects that represent the primitive data types. They are used in places primitive types in object form. Java Collection does not accept primitive types therefore we have to use wrapper classes. One of the greatest things about wrapper classes is the autoboxing and unboxing where the type of the values will be changed automatically into primitive wherever you need them as primitives. <br>
There are 3 interfaces that implement the Java Collection Interface: <br>
1. List Interface. <br>
2. Set Interface. <br>
3. Queue Interface. <br>
<h3>- ArrayList: </h3>is a dynamic list that grows automatically, it is so fast in accessing data while it uses random access algorithm to access data. It is not a perfect choice for adding and removing elements from a list which requires a lot of work. It implements List Interface <br> 
<h3>- LinkedList: </h3>is a dynamic list that grows automatically, it is so fast in adding and removing elements from the list and it is composed of nodes that are connected to each other using addresses while they are distributed randomly in memory. It is so slow in retrieving data as they are distributed randomly in the memory. It implements List Interface and DeQueue Interface. The functions inherited from DeQueue Interface include "getFirst()", "getLast()", "addFirst()", "addLast", etc. <br>
<h3>- HashSet: </h3>is a dynamic list that grows automatically, it does not accept duplicates. Its initial size by default is 16 with a 75% load factor, to change those default values: <br>

        HashSet<String> hs = new HashSet<>(100, 0.8)

<h3>- LinkedHashSet: </h3>is a dynamic list that grows automatically, it does not accept duplicates. It does not accept duplicates but it preserves the insertion order of the elements, its internal implementation is based on a hash table and linked list. <br>
        
<h3>- Stack: </h3>is a dynamic list that grows automatically, it builds on the concept of "First In Last Out (FILO)" <br>
<h3>- PriorityQueue: </h3>is a dynamic list that grows automatically, it builds on the concept of "First In First Out (FIFO)", it is similar to LinkedList where it implements Queue Interface but it does not support heterogeneous data in the list. It has two main methods "offer()" and "add()", the first one return "Null" if the insertion fails and the second returns an exception. <br>
<br>
In the 'java.util' package there is a class called Collections. It has a lot of useful methods that can be applied to lists as:

        Collections.sort(List);
        Collection.shuffle(List);


<h2>Iterator</h2>
It is a class provided by the 'java.util' package that can be used to iterate over iterable data structures. Iterator is more efficient than loops where it does not keep track of the indices of the elements and it is more thread-safe than loops. Example:

        Integer[] init = {1,2,3,4,5,6,7,8,9,10,11,12,13,14};
        List li = new List(Arrays.asList(inti));
        Iterator itrList = li.iterator();
        while(itrList.hasNext()){
            System.out.println(itrList.next());
        }



<h2>Map Interface </h2>
Map Interface is  used to store key-value pairs, both key and value should be objects while keys can't be duplicated. The most common classes that implement map interface are the following:
<h3>- HashMap</h3>It uses the hashtable as the underlying data structure, it doesn't preserve the insertion order of the elements. HashMap is a great choice for searching operations. <br>

<h3>- HashTable</h3>It uses the hashtable as the underlying data structure, it doesn't preserve the insertion order of the elements. HashTable is an old version of the map. It is not thread-safe and does not accept null keys or values at all. <br>

<h2>Records</h2>
In Java, the record keyword was introduced in Java 14 as a preview feature and became a standard feature in Java 16. Records provide a concise way to create immutable data classes. They are designed to be a quick and clean way to create classes that are primarily used to store data and have minimal behavior.

        public record Point(int x, int y) {}

<h2>Functional Programming</h2>
Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data. In Java, functional programming has become more prominent with the introduction of features like lambda expressions, functional interfaces, and the Stream API in Java 8.

        public class StreamExample {
            public static void main(String[] args) {
                // Create a list of integers
                List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
                // Use streams to filter and print the odd numbers
                numbers.stream()           // Convert the list to a stream
                       .filter(n -> n % 2 != 0) // Filter out even numbers (Lambda Expresion)
                       .forEach(System.out::println); // Print each remaining number (Method Reference)
            }
        }

__map__ returns a new stream of transformed elements. Has similar functionality to forEach but for each is void:

    public class MapExample {
        public static void main(String[] args) {
            List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");
    
            // Use map to convert each name to uppercase
            List<String> upperCaseNames = names.stream()
                                               .map(String::toUpperCase)
                                               .collect(Collectors.toList());
    
            // Print the new list
            upperCaseNames.forEach(System.out::println);
        }
    }

__Predicate__ is a functional interface that represents a condition (or predicate) that takes one argument and returns a boolean value.

        public class PredicateExample {
            public static void main(String[] args) {
                List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David", "Eve");
        
                // Define a predicate that checks if a string has a length greater than 3
                Predicate<String> lengthGreaterThanThree = name -> name.length() > 3;
        
                // Use the predicate to filter the list
                List<String> filteredNames = names.stream()
                                                  .filter(lengthGreaterThanThree)
                                                  .collect(Collectors.toList());
        
                // Print the filtered list
                System.out.println(filteredNames); // Output: [Alice, Charlie, David]
            }
    }

__Optional class__ is a container object which may or may not contain a non-null value. It was introduced in Java 8 to reduce the number of null references and avoid potential NullPointerException errors. By using Optional, developers can explicitly specify the possibility of an absent value and handle it more gracefully. 
You can create an Optional object using the following methods:
empty(): Returns an empty Optional instance.
of(value): Returns an Optional with the specified non-null value.
ofNullable(value): Returns an Optional with the specified value, or an empty Optional if the value is null.

        Optional<String> optionalEmpty = Optional.empty();          // An empty Optional
        Optional<String> optionalValue = Optional.of("Hello");      // Optional containing "Hello"
        Optional<String> optionalNullable = Optional.ofNullable(null);  // An empty Optional
        Optional<String> optionalNullableValue = Optional.ofNullable("World"); // Optional containing "World"

To access the value contained in an Optional, you can use the following methods:
get(): Returns the value if present, otherwise throws NoSuchElementException. Use this method with caution.
isPresent(): Returns true if the value is present, otherwise false.
ifPresent(Consumer<? super T> consumer): Executes the given consumer if a value is present.
orElse(T other): Returns the value if present, otherwise returns the specified default value.
orElseGet(Supplier<? extends T> other): Returns the value if present, otherwise invokes the specified supplier and returns the result.
orElseThrow(Supplier<? extends X> exceptionSupplier): Returns the value if present, otherwise throws an exception produced by the exception supplier.

        public Optional<String> getOptionalValue() {
            return Optional.empty(); // or Optional.of("some value")
        }
        
        public void processOptionalValue() {
            Optional<String> optionalValue = getOptionalValue();
            optionalValue.ifPresentOrElse(
                value -> System.out.println(value.toUpperCase()),
                () -> System.out.println("No value present")
            );
        }

