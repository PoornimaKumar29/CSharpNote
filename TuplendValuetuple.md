```cs
##In C#, both Tuple and ValueTuple are used to store multiple values in a single object

using System;

class Program
{
    static (string Name, int Age) GetStudentInfo()
    {
        string name = "Poornima";
        int age = 22;
        return (name, age);
    }

    static void Main()
    {
        var student = GetStudentInfo();
        Console.WriteLine($"Name: {student.Name}, Age: {student.Age}");
    }
}

```