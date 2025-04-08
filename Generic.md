```cs
#Generic_method.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Polymorphism
{
   public class Generic_Meth
    {
        public void Swap<T1>(ref T1 x , ref T1 y)
        {
            T1 t;
            t = x;
            x = y;
            y = t;
        }

    }
}
# program.cs
// See https://aka.ms/new-console-template for more information
using Polymorphism;

class FunctionOverloading
{

    public static void Main()
    {
        Generic_Meth gm = new Generic_Meth();
        //Calling the method Swap and pass integer type of data
        {
            int A = 10, B = 20;
            string A1 = "Hello", B1 = "World";
            gm.Swap<int>(ref A, ref B);

            //Calling the method Swap and pass string type of data
            gm.Swap<string>(ref A1, ref B1);

            Console.WriteLine("After Swap A= {0} \t B= {1}", A, B);
            Console.WriteLine("After Swap A1= {0} \t B1= {1}", A1, B1);
            //
            A1 = "hi";
            B1 = "Hello";
            gm.Swap(ref A1, ref B1);
            Console.WriteLine("After Swap A= {0} \t B= {1}", A1, B1);
            Console.ReadKey();
        }
    }
}
```
```cs
#Generic Method with different #Data-type:
class Generic_Method_With_Diff_DataType
    {
        public static void Gmethod<myType1, myType2>(myType1 x, myType2 y)
        {
            Console.WriteLine(" Mytype1 = " + x);
            Console.WriteLine(" Mytype2 = " + y);
        }
        static void Main()
        {
            Gmethod<int, float>(56, 9.4546f);
            Gmethod<string, int>("Hello", 465);
            Console.ReadKey();
        }
    }

##Generic Class:
 class GenericClass<T,T1>
    {   T a;
        T1 b;
        public GenericClass(T a, T1 b)
        {
            this.a = a;
            this.b = b;
        }
        public void Display()
        {
            Console.WriteLine("The First value: {0}", a);
            Console.WriteLine("The Second value: {0}", b);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            GenericClass<int,string> iobj = new GenericClass<int,string >(10,"Hi");
            GenericClass<string,char> sobj = new GenericClass<string,char>("Geetha",'S');
            iobj.Display();
            sobj.Display();
            Console.ReadKey();
        }
    }
#############################################endregion
####Array
####hashtable
// See https://aka.ms/new-console-template for more information
using Polymorphism;
using System.Collections;

class FunctionOverloading
{

    public static void Main()
    {
        Hashtable hs = new Hashtable();
        hs.Add("f1 ", "apple");
        hs.Add("f2", "orange");
        hs.Add("f3", "grape");
        foreach (var key in hs)
        {
            Console.WriteLine(key);
        }
        hs.Remove("f3");
        foreach (var key in hs)
        {
            Console.WriteLine(key);
        }
        Console.WriteLine(hs["f3"]);
        hs.Add("f3", "grape");
        hs.Add("f4", "watermelon");
        hs.Add("f5", "pine");
        Console.WriteLine("count of hashtable" + hs.Count);
        Console.WriteLine(hs.Contains("f4"));
        //copying hashtable
        Hashtable hs1 = new Hashtable(hs);
        foreach (var key in hs1)
        {
            Console.WriteLine("after copying "+key);

        }
        object[] h2 = new object[10];

        Console.WriteLine("copying in array");
        hs.Keys.CopyTo(h2, 1);
        string[] h3 = new string[10];
        Console.WriteLine("After copying in string as array");
        hs.Keys.CopyTo(h3, 1);
        //to remove all values from the hashtable :
        //Clear () 
        Console.WriteLine(" Total no.of items in hs  Before clear " + hs.Count);
        hs.Clear();
        Console.WriteLine(" Total no.of items in hs  after clear " + hs.Count);

    }
}

####Stack

using System;
using System.Collections;
class FunctionOverloading
{
    public static void Main()
    {

        Stack<string> mystack = new Stack<string>();
        mystack.Push("poornima");
        mystack.Push("surya");
        mystack.Push("Akshaya");
        Console.WriteLine("Stack after pushing");
        foreach(var item in mystack)
        {
            Console.WriteLine(item);
        }
        Console.WriteLine("Top elemnet" + mystack.Peek());
        Console.WriteLine("pop lelement from stack" + mystack.Pop());

    }
}
####Queue
using System;
using System.Collections;
class FunctionOverloading
{
    public static void Main()
    {
        Queue<string> myqueue = new Queue<string>();
        myqueue.Enqueue("poornima");
        myqueue.Enqueue("surya");
        myqueue.Enqueue("Akshaya");
        Console.WriteLine("Queue after enqueuing");
        foreach (var item in myqueue)
        {
            Console.WriteLine(item);

        }
          Console.WriteLine("Frontelement " + myqueue.Peek());
        Console.WriteLine("pop the element from queue" + myqueue.Dequeue());
        Queue<string> myque2 = new Queue<string>(myqueue);
        foreach (var item in myque2)
        {
            Console.WriteLine(item);

        }
        string[] obj = new string[myqueue.Count+1];
        myqueue.CopyTo(obj, 0);
        
    }
}
#SortedList
using System.Collections;
// SortedList<int,string> sl = new SortedList<int,string>();
SortedList sl = new SortedList();
sl.Add(001, "ziavudeen");
sl.Add(002, "Abinaya");
sl.Add(003, "John");
sl.Add(004, "Arjun");
sl.Add(007, "Nithin");
sl.Add(006, "Fransy");
sl.Add(005, "Ritesh");
foreach (DictionaryEntry item in sl)
{
    Console.WriteLine(item.Key + "\t\t" + item.Value);
}
Console.WriteLine(" Check whether ziavudeen  is in the List or not? \n\n");
if (sl.ContainsValue("Uma"))
{
    Console.WriteLine("This student name is already in the list");
}
else
{
    sl.Add(008, "Uma");
    Console.WriteLine(" Uma name Added in the List");
}
Console.WriteLine(sl.Count);

if (sl.ContainsKey(008))
{
    Console.WriteLine(" Yes. Key 008 is Available in the List");
}
else
{
    Console.WriteLine(" Yes. Key 008 is  Not Available in the List");
}

object KeyAtIndex3 = sl.GetKey(3);
Console.WriteLine(" Key at the Index(3) = " + KeyAtIndex3);

int myindex = sl.IndexOfKey(007)
Console.WriteLine(" The Index of 007 =" + myindex);
Console.WriteLine(" Index of value of  ziavudeen" + sl.IndexOfValue("ziavudeen"));
Console.WriteLine(" replace the value of key 003");
sl.SetByIndex(003, "Geetha");

Console.WriteLine(" ---SetByIndex() ---");
IList mylist = sl.GetKeyList();

foreach (DictionaryEntry item in sl)
{
    Console.WriteLine(item.Key + "        " + item.Value);
}



Console.ReadLine();
    ```



