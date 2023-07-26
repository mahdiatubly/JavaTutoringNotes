<h1>Java</h1>
<h2>JVM(Java Virtual Machine)</h2>
There are 3 types of high-level programming languages: <br>
- <strong>Compiled:</strong> The code is compiled (translated) into a machine code that runs on a specific platform (Microsoft/Mac/...) <br>
- <strong>Interpreted:</strong> Translate the code into machine code whenever you run the program, the translation to machine code won't be saved in any form. If you want to rerun the code you have to retranslate the whole code again. That is what makes interpreted programming languages slower than compiled ones. <br>
- <strong>JVM:</strong> The code is first compiled into what is called Bytecode saved in (.class) file the n The Bytecode is interpreted by JVM into the machine code of the platform that the program running on. <br>

<h2>Generics</h2>
Generics are used to generalize the code where it can be used with different data types. Example:

    public class Test <T>{
      public void print(T v) {
          System.out.println(v);
      }
    }

    //main:
    public class Main {
      public static void main(String[] args) {
          Test<String> T = new Test<>();
          T.print("ABBAS\nHUSSAIN\nHUSSAIN\nHUSSAIN\n");
      }
    }
