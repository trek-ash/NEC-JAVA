# Example Programs

## Example Program 1 :
``` Java
package DayThree;
import java.util.Stack;
public class ExampOne {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Stack<String> stackOfCards=new Stack<>();
		stackOfCards.push("Jack");
		stackOfCards.push("Queen");
		stackOfCards.push("King");
		stackOfCards.push("Ace");
		System.out.println("Stack=> "+stackOfCards);
		System.out.println();
		String cardAtTop= stackOfCards.pop();
		System.out.println("Stack pop()=> "+cardAtTop);
		System.out.println("Current Stack=> "+stackOfCards);
		System.out.println();
		cardAtTop=stackOfCards.peek();
		System.out.println("Stack.peek()=> "+ cardAtTop);
		System.out.println("Current stack=> "+ stackOfCards);
	}
}
```

## Example Program 2: Hash Set 
```Java
package DayThree;
import java.util.*;
public class HashSet## Example {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int count[]= {34,22,10,60,30,22};
		Set<Integer> set=new HashSet<Integer>();
		try {
			for (int i=0; i<5; i++) {
				set.add(count[i]);
			}
			System.out.println(set);
			TreeSet sortedSet=new TreeSet<Integer>(set);
			System.out.println("The sorted list is: ");
			System.out.println(sortedSet);
			System.out.println("The first element of the set is: "+(Integer)sortedSet.first());
			System.out.println("The last element of the set is: "+(Integer)sortedSet.last());
		}
		catch(Exception e) {}
	}
}
```

## Example 3: Hash Map
``` Java
package DayThree;
import java.util.*;
public class HashMapExamp {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Map<String,String> fruit=new HashMap<String,String>();
		fruit.put("Apple","red");
		fruit.put("Pear","yellow");
		fruit.put("plum","purple");
		fruit.put("cherry","red");
		for(String key: fruit.keySet()) {
			System.out.println(key+": "+fruit.get(key));
		}
	}

}
```

## Example 4: Exception Handling
``` Java
package DayThree;

public class ExceptionExamp {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			int data=100/0;
		}
		catch(ArithmeticException e) {
			System.out.println(e);
		}
		System.out.println("rest of the code...");

	}

}
```

## Example 5: Multiple catch and finally
``` Java
package DayThree;

public class MultiCatchBlockExamp {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			int a[]=new int[5];
			a[5]=50/0;
		}
		//compile time error because exception is a larger block than the others(if exception is written above array wale classes)
		catch(ArithmeticException e) {
			System.out.println("Task 1 completed");
		}
		catch(ArrayIndexOutOfBoundsException e) {
			System.out.println("Task 2 completed");
		}
		catch(Exception e) {
			System.out.println("Task completed");
		}
		finally
		{
			System.out.println("Finally block is always executed");
		}
		
		System.out.println("rest of the code..");
	}

}
```

## Example 6: Exception not handled
``` Java
package DayThree;

public class TestFinally {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			int data=25/0;
			System.out.println(data);
		}
		catch(NullPointerException e) {
			System.out.println(e);
		}
		finally {
			System.out.println("Always executed");
		}
			System.out.println("rest");

	}

}
```

## Example 7: Test throw and throws
``` Java
package DayThree;
import java.io.IOException;
public class TestThrows {
void m() throws IOException{
	throw new IOException("device error");
}
void n() throws IOException{
	m();
}
void p() {
	try {
		n();
	} catch(Exception e) {
		System.out.println("Exception handled");
	}
}


	public static void main(String[] args) {
		// TODO Auto-generated method stub
		TestThrows obj=new TestThrows();
		obj.p();
		System.out.println("Normal flow");
	}
}
```

## Example 8: User Defined Exception
``` Java
package DayThree;

class WrongInputException extends Exception {
	WrongInputException(String s){
		super (s);
	}

}
package DayThree;

class Input {
	void method() throws WrongInputException {
		throw new WrongInputException("Wrong input");
	}

}
package DayThree;

public class UserDefinedExcept {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			Input n=new Input();
			n.method();
		}
		catch(WrongInputException wie) {
			System.out.println(wie.getMessage());
		}
	}
}
```

## Example 9: Try with resources
``` Java
package DayThree;
import java.io.*;
public class TryWithReources {

	public static void main(String[] args) {
		try(BufferedReader br=new BufferedReader(new FileReader("aaa.txt")))
				{
					String str;
					while((str=br.readLine())!=null) {
						System.out.println(str);
					}
				}
					catch (IOException ie) {
						System.out.println("Exception");
					}
	}
// NOTE : BufferedReader is auto closable.
}
```



## Example 10: Multithreading 
``` Java
package DayThree;

public class MyThread extends Thread{
String ss;
public MyThread(String s)
{
	ss=s;
	
}
public void run()
{
	for(int i=0;i<100;i++) {
		System.out.println(ss+ "thread is running with ... stage "+i);
}
}
}
package DayThree;

public class ThreadEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		MyThread t1=new MyThread("t1");
		MyThread t2=new MyThread("t2");
		t1.start();
		t2.start();
	}

}
```

## Example 11: Threading using Runnable
``` Java
package DayThree;

public class MyThread implements Runnable{
public void run()
{
	for(int i=0;i<100;i++) {
		System.out.println("thread is running "+i);
}
}
}
package DayThree;

public class ThreadEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Thread t=new Thread(new MyThread());
		t.start();
	}

}
```

## Example 12: Thread Priority
``` Java
package DayThree;

public class A extends Thread{
	public void run() {
		System.out.println("Thread A started");
		for (int i=1; i<=4; i++) {
			System.out.println("\t From thread A: i= "+i);
		}
		System.out.println("Exit from A");
	}

}
package DayThree;

public class B extends Thread {
	public void run() {
		System.out.println("Thread B started");
		for(int j=1; j<=4; j++)
		{
			System.out.println("\t From thread B: i= "+j);
		}
		System.out.println("Exit from B");
	}

}
package DayThree;

public class C extends Thread{
	public void run() {
		System.out.println("Thread C started");
		for(int k=1; k<=4; k++)
		{
			System.out.println("\t From thread C: i= "+k);
		}
		System.out.println("Exit from C");
	}

}
package DayThree;

public class ThreadPrior {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		A threadA=new A();
		B threadB=new B();
		C threadC=new C();
		threadC.setPriority(Thread.MAX_PRIORITY);
		threadB.setPriority(threadA.getPriority()+1);	
		threadA.setPriority(Thread.MIN_PRIORITY);
	System.out.println("Started Thread A");
	threadA.start();
	System.out.println("Started Thread B");
	threadB.start();
	System.out.println("Started Thread C");
	threadC.start();
	System.out.println("End thread");
	}

}
```

## Example 13: Chat
``` Java
package DayThree;

public class Chat {
	boolean flag=false;
	public synchronized void Question(String msg) {
		if (flag) {
			try {
				wait();
			} catch(InterruptedException e) {
				e.printStackTrace();
			}
		}
		System.out.println(msg);
		flag=true;
		notify();
	}
	public synchronized void Answer(String msg) {
		if(!flag) {
			try {
				wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		System.out.println(msg);
		flag=false;
		notify();
		
	}
}
package DayThree;

public class T1 implements Runnable {
	Chat m;
	String[] s1= {"hi","how are you ?","Iam also doing fine!"};
	public T1(Chat m1)
	{
		this.m=m1;
		new Thread(this,"Question").start();
	}public void run()
	{
		for(int i=0;i<s1.length;i++)
		{
			m.Question(s1[i]);
		}
	}
}
package DayThree;

public class T2 implements Runnable{
	Chat m;
	String[] s2= {"hi","I am good. What about you?","Great!"};
	public T2(Chat m2)
	{
		this.m=m2;
		new Thread(this,"Answer").start();
	}public void run()
	{
		for(int i=0;i<s2.length;i++)
		{
			m.Answer(s2[i]);
		}
	}

}
package DayThree;

public class TestThread {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Chat m=new Chat();
		new T1(m);
		new T2(m);
	}
}
```

## Example 14: Schedule Task
``` Java
package DayThree;
import java.util.TimerTask;
import java.util.Date;
public class ScheduledTask extends TimerTask {
	Date now;
	public void run() {
		now=new Date();
		System.out.println("Time is: "+now);
	}
}
package DayThree;
import java.util.Timer;
public class SchedulerMain {

	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		Timer time=new Timer();
		ScheduledTask st=new ScheduledTask();
		time.schedule(st, 0, 1000);
		for(int i=0; i<=5; i++) {
			System.out.println("Execution in main thread "+i);
			Thread.sleep(2000);
			if(i==5) {
				System.out.println("Application terminates");
				System.exit(0);
			}
		}

	}

}
```

# Exercise Programs

## Exercise 1:  Make a user defined exception if input is not between 1 and 9
``` Java
package DayThree;

public class WrongInput extends Exception {
	WrongInput(String s){
		super(s);
	}

}
package DayThree;

public class Input1 {
	void method1 (int i)throws WrongInput {
		if (i<0 || i>9)
			throw new WrongInput("Wrong Input");
	}

}
package DayThree;
public class UserDefinedExcep {

        public static void main(String[] args) {
            // TODO Auto-generated method stub
            try {
                Input1 n=new Input1();
                n.method1(34);
            }
            catch(WrongInput wi) {
                System.out.println(wi.getMessage());

        }

    }
}
```

## Exercise 2:
``` Java
public ISOMsg isoMsgChequeStop(StopChequePaymentParams stopChequePaymentParams) {
 ISOMsg m = new ISOMsg();

 String accountNumber = stopChequePaymentParams.getAccountNumber();
 String reasonCode = stopChequePaymentParams.getReasonCode();
 Integer chequeStartNo = stopChequePaymentParams.getChequeStartNo();
 Integer noOfLeaves = stopChequePaymentParams.getLeavesCount();

 try {

  m.setMTI(MSGComposerConstants.MTI_TX); //MTI

  m.set(2, stopChequePaymentParams.getInitiator()); 
  m.set(3, MSGComposerConstants.PROCESSING_CODE_CHQ_STOP); 
  m.set(4, "0000000000000000");
  String stan = Util.padRight(stanGenerator.generateSTAN(), " ", 12);
  m.set(11, stan); //System Trace Audit Number
  m.set(12, Util.getCurrentDateTime()); 
  m.set(17, Util.getCurrentDate()); //Capture Date
  m.set(32, MSGComposerConstants.ACQUIRING_II_CODE); 
  m.set(37, "412812134941"); //constant
  m.set(41, "00390039"); //atm id
  m.set(42, Util.padRight("1000008", " ", 15)); //atm id
  m.set(43, "LAXMI ATM");

  if (stopChequePaymentParams.hasPartners()) {
   m.set(46, stopChequePaymentParams.getPartnerPattern());  }

  m.set(49, stopChequePaymentParams.getTransactionCurrencyCode());

  String field62 = Util.padLeft(chequeStartNo.toString(), " ", 16) +
   Util.padLeft(noOfLeaves.toString(), "0", 4) +
   Util.padRight(reasonCode, " ", 5);

  m.set(62, field62);
  m.set(102, accountNumber);
  m.set(123, MSGComposerConstants.DELIVERY_CH_CTRL_ID); 
 } catch (ISOException e) {
  e.printStackTrace();
 }
 return m;
}
```

# Assignment:
## 1. Generic User Defined Classes
The idea is to allow type (Integer, String, etc and user defined types) to be a parameter to methods, classes and interfaces. The syntax for objects of generic classes is as follows:
BaseType <Type> obj = new BaseType <Type>();

## 2. Try With Multiple Resources
``` Java
import java.io.DataInputStream;  
import java.io.FileInputStream;  
import java.io.FileOutputStream;  
import java.io.InputStream;    
public class TryWithResources {    
public static void main(String args[]){      
try(    
        FileOutputStream fileOutputStream =new FileOutputStream(“abc.txt");  
        InputStream input = new FileInputStream("abc.txt")){  
        String msg = "Hello!";      
        byte byteArray[] = msg.getBytes();        
        fileOutputStream.write(byteArray);  
        System.out.println("Data written");  
        System.out.println(msg);  
        DataInputStream inst = new DataInputStream(input);    
        int data = input.available();    
        byte[] byteArray2 = new byte[data]; 
        inst.read(byteArray2);    
        String str = new String(byteArray2);   
        System.out.println(“Data read");  
        System.out.println(str);  
}catch(Exception exception){  
       System.out.println(exception);  
}     }    }  
```

## 3. Auto Closable Objects
An object that may hold resources (such as file or socket handles) until it is closed. The close() method of an Auto Closeable object is called automatically when exiting a try-with-resources block for which the object has been declared in the resource specification header. This construction ensures prompt release, avoiding resource exhaustion exceptions and errors that may otherwise occur.

