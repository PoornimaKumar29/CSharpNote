```cs
############# Function overloading  example
##calculator.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Polymorphism
{
    class Calculator
    {
        public void Add(int x,int y)
        {
            Console.WriteLine("Addition of numbers " + (x + y));
        }
        public void Add(int x , int y ,int z)
        {
            Console.WriteLine("Addition of three numbers " + (x +z+ y));
        }
        public void Add(float x, float y, int z)
        {
            Console.WriteLine("Addition of three numbers " + (x + z + y));
        }
    }
   
}
```
```cs
 #program.cs
 // See https://aka.ms/new-console-template for more information
using Polymorphism;

class FunctionOverloading
{
    static void Main()
    {
        //----polymorphism
        Calculator c = new Calculator();
        c.Add(12, 32, 12);
        c.Add(23, 23);
        c.Add(12.3f, 34.34f, 23);
        Console.ReadLine();
    }
}
```


```cs
################function overriding
#program.cs
// See https://aka.ms/new-console-template for more information
using Polymorphism;

class FunctionOverloading
{
    static void Main()
    {
        //Derived d = new Derived();
        //d.fun1();
        Calculator c1 = new Derived();
        c1.fun1();
        //Calculator c = new Calculator();
        //c.fun1();

    }
}

#calculator.cs / class program
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Polymorphism
{
    class Calculator
    {
        public virtual void fun1()
        {
            Console.WriteLine("Overriding method virtual");
        }
    }
        class Derived : Calculator
        {
            public override void fun1()
            {
            //base.fun1();
            Console.WriteLine("Iam overided function");
            }
        }
}
```
