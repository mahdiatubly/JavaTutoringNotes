<h1>Java</h1>
<h2>JVM(Java Virtual Machine)</h2>
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
        //Notice that wildcard "?" can extend a specific class similar to generic type
        public static void printList(List<?> l){
            for (Object e:l) {
                System.out.println(e);
            }
        }
    }

<h2>Java Collection</h2>
Before we start with the Java collection let's take a look at the idea of wrapper classes; wrapper classes are objects that represent the primitive data types. They are used in places primitive types in object form. Java Collection does not accept primitive types therefore we have to use wrapper classes. One of the greatest things about wrapper classes is the autoboxing and unboxing where the type of the values will be changed automatically into primitive wherever you need them as primitives.

