```cs
using System.Collections;
class Program
{
    public static void Main()
    {
        PartialCustomer partialCustomer = new PartialCustomer();
        partialCustomer.GetCustomerInfo();
    }

    internal class Customer1
        {
        }

    public partial class PartialCustomer
    {
        public int CustomerId { get; set; }
        public string Name { get; set; }
        public string City { get; set; }

        public PartialCustomer()
        {
            CustomerId = 101;
            Name = "Test Customer";
            City = "Chennai";
        }
    }
    internal class Customer2
    {
    }
    public partial class PartialCustomer
    {
        public void GetCustomerInfo()
        {
            Console.WriteLine($"Id ={CustomerId} \nName ={Name}\nCity={City}");
        }
    }
   


}
```