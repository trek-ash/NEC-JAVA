# Example Programs


## Example Program 1
``` Java
class A
{
    public static void main(String[] args)
    {
        StringBuilder sb=new StringBuilder("Hello");
        sb.append("Java");
        System.out.println(sb);
        sb.insert(1,"java");
        System.out.println(sb);
        sb.replace(1,3,"Java");
        System.out.println(sb);
        sb.delete(1,3);
        System.out.println(sb);
        sb.reverse();
        System.out.println(sb);
    }
}
```
## Example Program 2
``` Java
class hello
{
    public static void main(String args[])
    {
        System.out.println("Hello world");
        System.out.println(args[0]);
    }
}
```

## Example Program 3
``` Java
class B
{
    public static void main(String[] args)
    {
        StringBuffer sb=new StringBuffer("Hello");
        sb.append("Java");
        System.out.println(sb);
        sb.insert(1,"java");
        System.out.println(sb);
        sb.replace(1,3,"Java");
        System.out.println(sb);
        sb.delete(1,3);
        System.out.println(sb);
        sb.reverse();
        System.out.println(sb);
    }
}
```
## Example Program 4
``` Java
class Lamp {
    boolean isOn;
    void turnOn
    {
        isOn = true;
    }
    void turnOff
    {
        isOn = false;
    }

    void display() {
        System.out.println("Light on? " + isOn);
    }
}

class example {
    public class static main(String args[])
    {
    Lamp l1=new Lamp();
    Lamp l2=new Lamp();
    l1.turnOn();
    l2.turnOff();
    l1.display();
    l2.display();
    }
}
```
## Example Program 5
``` Java 
public class JavaClassExample {
    private String name;

    public void setName(String n) {
        name = n;
    }

    public String getName() {
        return name;
    }

    public static void main(String[] args) {
        JavaClassExample j = new JavaClassExample();
        j.setName("VISITOR");
        System.out.println("Hello " + j.getName());
    }

}
```

## Example Program 6
``` Java
public class StringDemo {
    public static void main(String[] args) {
        char[] a = { 'H', 'e', 'l', 'l', 'o' };
        String s = new String(a);
        System.out.println(s);
        System.out.println(s.toUpperCase());
        System.out.println(s.toLowerCase());
        System.out.println(s);

        s = " Sachin ";
        System.out.println(s);
        System.out.println(s.trim());
        s = "Sachin";
        System.out.println(s.startsWith("Sa"));
        System.out.println(s.endsWith("n"));
        System.out.println(s.charAt(0));
        System.out.println(s.length());
        int ab = 10;

        s = String.valueOf(ab);
        System.out.println(s + 10);

    }
}
```

# Exercise Program

```Java
class Exercise {

    private Boolean isPrime(int k) {
        for(int i=2;i<Math.sqrt(k); i++)
            if(k%i==0)
                return false;
            return true;
    }

    public void printPascal() {
        int num = 1;
        for(int i=0;i<5;i++) {
            for(int k=5; k>i; k--) {
                System.out.print(" ");
            }
            num = 1;
            for(int j=0;j<=i;j++) {
                System.out.print(num+ " ");
                num = num * (i - j) / (j + 1);
            }
            System.out.println();
        }
    }

    public void printPattern() {
        System.out.println("\nPattern 1 : ");
        for(int i=0;i<4;i++) {
            for(int j=0;j<4; j++)
                if(i>=j)
                    System.out.print(i+1);
            System.out.print("\n");
        }
        System.out.println("\nPattern 2 : ");
        for(int i=0;i<4;i++) {
            for(int j=0;j<4; j++)
                if(i>=j)
                    System.out.print(j+1);
            System.out.print("\n");
        }
    }

    public void printSeries() {
        int i = 0, k = 1;
        System.out.println("\nFirst 100 prime nums are :");
        while(i<=100) {
            if(isPrime(k)) {
                System.out.println(k+"\t");
                i++;
            }
            k++;
        }
    }
}

public class Main {

    public static void main(String[] args) {
	    Exercise E = new Exercise();

	    // PROGRAM 1: Pascal's triangle
	    E.printPascal();

	    // PROGRAM 2: Print pattern
	    E.printPattern();

	    // PROGRAM 3: Print 100 prime numbers
	    E.printSeries();
     }
}
```