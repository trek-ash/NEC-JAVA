# Example Programs

## Example Program 1
``` Java
abstract class Bank {
    abstract int getRateOfInterest();
}

class SBI extends Bank {
    int getRateOfInterest() {
        return 4;
    }
}

class PNB extends Bank {
    int getRateOfInterest() {
        return 5;
    }
}

class TestBank {
    public static void main(String args[]) {
        Bank B = new SBI();
        int interest = B.getRateOfInterest();
        System.out.println("Interest is : " + interest);
    }
}
```

## Example Program 2
``` Java
class StaticExample {
    static {
        System.out.println("Static block is invoked");
    }

    public static void main(String[] args) {
        System.out.println("Hello from main");
    }
}
```

## Example Program 3
``` Java
interface Printable {
    void show();

    void print();
}

interface Showable {
    void show();
}

class TestInterface implements Showable, Printable {
    public void show() {
        System.out.println("Hello Diego");
    }

    public void print() {
        System.out.println("Hello Sam");
    }

    public static void main(String[] args) {
        Printable P = new TestInterface();
        P.print();
        P.show();
        Showable S = new TestInterface();
        S.show();
        // S.print() won't work.
    }
}
```

## Example Program 4
```Java
class Outer_Class {
	int num;
	class InnerClass {
		public void print() {
		       System.out.println("This is an inner class");
		}
	}
	void display_Inner() {
		InnerClass inner =  new InnerClass();
		inner.print();
	}
}
public class MyClass {
	public static void main(String args[]) {
		Outer_Class outer = new Outer_Class();
		outer.display_Inner();
		Outer_Class.InnerClass inner = outer.new InnerClass();
		inner.print();
	}
}
```
## Example 5
``` Java
import java.io.*;

public class fileExample {
    public static void main(String[] args) {
        if (args.length != 2)
            System.err.println("Usage.java.fileCopy");
        else {
            try {
                copy(args[0], args[1]);
            } catch (Exception e) {
                System.err.println(e.getMessage());
            }
        }
    }

    public static void copy(String from_name, String to_name) throws IOException {
        File from_file = new File(from_name);
        File to_file = new File(to_name);
        try {
            FileInputStream from = new FileInputStream(from_file);
            FileOutputStream to = new FileOutputStream(to_file);
            byte[] buffer = new byte[4096];
            int readCount = 0;
            while ((readCount = from.read(buffer)) > 0) {
                to.write(buffer, 0, readCount);
            }
        } catch (Exception e) {
            System.err.println(e.getMessage());
        } finally {
            if (from != null || to != null)
                try {
                    from.close();
                    to.close();
                } catch (IOException e) {
                    System.err.println(e.getMessage());
                }
        }

    }
}
```

## Example Program 6
``` Java
import java.util.*;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<Integer> a = new ArrayList<Integer>(10);
        for (int i = 1; i <= 10; i++)
            a.add(i);
        System.out.println(a);
        a.remove(3);
        System.out.println(a);
        System.out.println("Is empty? " + a.isEmpty());
        System.out.println("Index of 7 : " + a.indexOf(7));
    }
}
```

## Example Program 7
``` Java
package com.core;
import java.util.*;
public class basicArrayList {
	public static void main(String[] args)
	{
		ArrayList<String> al=new ArrayList<String>();
		al.add("Java");
		al.add("C++");
		al.add("Python");
		al.add("Perl");
		System.out.println(al);
		System.out.println("Element at index 1: "+al.get(1));
		System.out.println("Does list contain Java? "+al.contains("Java"));
		al.add(2,"Play");
		System.out.println(al);
		System.out.println("IS array List empty?"+al.isEmpty());
		System.out.println("Index of perl is "+al.indexOf("Perl"));
		
		System.out.println("Size of the array list is "+al.size());
		System.out.println(al);
		al.remove("Perl");
		for(String str:al)
		System.out.println(str);
		
	}

}
```

## Example Program 8
``` Java
package com.core;
import java.util.*;
public class BasicVectorOperations {

	public static void main(String[] args) {
		Vector<String> v=new Vector<String>();
		v.add("First");
		v.add("Second");
		v.add("Third");
		System.out.println(v);
		v.add(2,"Random");
		System.out.println(v);
		System.out.println("Element at index 3 is "+v.get(3));
		System.out.println("First element of this vector is "+v.firstElement());
		System.out.println("Last element of this vector is "+v.lastElement());
		System.out.println("IS element empty? "+v.isEmpty());
		System.out.println("Size of vector"+v.size());
		System.out.println("Max size of vector"+v.capacity());
		// TODO Auto-generated method stub

	}

}
```

## Example Program 9
``` Java
package com.core;
import java.util.*;
public class BasicVectorOperations {

	public static void main(String[] args) {
		Vector<String> v=new Vector<String>();
		v.add("First");
		v.add("Second");
		v.add("Third");
		System.out.println(v);
		v.add(2,"Random");
		System.out.println(v);
		System.out.println("Element at index 3 is "+v.get(3));
		System.out.println("First element of this vector is "+v.firstElement());
		System.out.println("Last element of this vector is "+v.lastElement());
		System.out.println("IS element empty? "+v.isEmpty());
		System.out.println("Size of vector"+v.size());
		System.out.println("Max size of vector"+v.capacity());
	}

}
```

## Example Program 10
``` Java
package com.core;
import java.util.*;

public class IteratorDemo {
	public static void main(String[] args)
	{
		ArrayList<String> al=new ArrayList<String>();
		al.add("C");
		al.add("E");
		al.add("B");
		al.add("A");
		al.add("D");
		System.out.print(" Original contents of al : ");
		Iterator itr=al.iterator();
		while(itr.hasNext())
		{
			Object element=itr.next();
			System.out.print(element+" ");
			
		}
		System.out.println();
		ListIterator litr=al.listIterator();
		while(litr.hasNext())
		{
			Object element=litr.next();
			litr.set(element+"+");
		}
		System.out.print("Modified contents of al : ");
		itr=al.iterator();
		while(itr.hasNext())
		{
			Object element=itr.next();
			System.out.print(element+" ");
		}
		System.out.println();
		System.out.print("Modified list backwards : ");
		while(litr.hasPrevious())
		{
			Object element=litr.previous();
			System.out.print(element+" ");
		}
		System.out.println();
	}

}
```

## Example Program 11
``` Java
package com.core;
import java.util.*;
public class LinkList {
	public static void main(String[] args)
	{
		LinkedList<String> al=new LinkedList<String>();
		al.add("Java");
		al.add("C++");
		al.add("Python");
		al.add("Perl");
		System.out.println(al);
		System.out.println("Element at index 1: "+al.get(1));
		System.out.println("Does list contain Java? "+al.contains("Java"));
		al.add(2,"Play");
		System.out.println(al);
		System.out.println("IS array List empty?"+al.isEmpty());
		System.out.println("Index of perl is "+al.indexOf("Perl"));
		
		System.out.println("Size of the array list is "+al.size());
		System.out.println(al);
		al.remove("Perl");
		for(String str:al)
		System.out.println(str);
		
	}

}
```

## Example Program 12
``` Java
package com.core;
import java.util.*;

public class QueueExample {

	public static void main(String[] args) {
		Queue<String> qe=new LinkedList<String>();
		qe.add("b");
		qe.add("a");
		qe.add("c");
		qe.add("e");
		qe.add("d");
		Iterator it=qe.iterator();
		System.out.println("Initial size  of queue"+qe.size());
		while(it.hasNext())
		{
			String iteratorValue=(String)it.next();
			System.out.println("Queue next value "+iteratorValue);
		}
		System.out.println("queue peek "+qe.peek());
		System.out.println("queue poll "+qe.poll());
		System.out.println("Final size  of queue "+qe.size());
	}

}
```

# Exercise Programs

## Exercise Program 1
``` Java
import java.io.*;

public class spaircount {
    public static void main(String[] args) {
        if (args.length != 1)
            System.err.println("Usage.java.fileCopy");
        else {
            try {
                copy(args[0]);
            } catch (Exception e) {
                System.err.println(e.getMessage());
            }
        }
    }

    public static void copy(String from_name) throws IOException {
        File from_file = new File(from_name);

        try {
            FileInputStream from = new FileInputStream(from_file);

            byte[] buffer = new byte[4096];
            int readCount = 0;
            int count = 0;
            while ((readCount = from.read()) > 0) {
                char c = (char) readCount;

                if (c == '{' || c == '}')
                    count++;
            }
            System.out.println("count is : " + count);
        } catch (Exception e) {
            System.err.println(e.getMessage());
        } 
    }
}
```

## Exercise Program 2
```Java
import java.util.*;
import java.io.*;

public class SayHello {
    public static void main(String[] args) {
        Scanner S = new Scanner(System.in);
        System.out.print("Enter your name :");
        String s = S.next();
        System.out.println("Hello, " + s);
        Date d = new Date(System.currentTimeMillis());
        System.out.println(d);

        File f = new File("Name_collection.txt");
        String content = "\n" + s + "\nLogin time : " + d;

        try {
            FileOutputStream file = new FileOutputStream(f, true);
            file.write(content.getBytes());
        } catch (IOException e) {
            System.err.println("Error :" + e.getMessage());
        }
    }
}
```

## Exercise Program 3
``` Java
import java.io.*;

public class fileIO {
    public static void main(String[] args) {
        if (args.length != 2)
            System.err.println("Usage.java.fileCopy");
        else {
            try {
                copy(args[0], args[1]);
            } catch (Exception e) {
                System.err.println(e.getMessage());
            }
        }
    }

    public static void copy(String from_name, String author) throws IOException {
        File from_file = new File(from_name);
        String to_name = from_name + ".class";
        to_name = to_name.replace(".java", "");
        File to_file = new File(to_name);
        var flag = to_file.createNewFile();
        if (flag) {
            try {
                FileInputStream from = new FileInputStream(from_file);
                FileOutputStream to = new FileOutputStream(to_file, true);
                byte[] buffer = new byte[4096];
                int readCount = 0;
                String content = "//Written by " + author + "\n";
                to.write(content.getBytes());
                while ((readCount = from.read(buffer)) > 0) {
                    to.write(buffer, 0, readCount);
                }
            } catch (Exception e) {
                System.err.println(e.getMessage());
            }
        }
    }
}
```