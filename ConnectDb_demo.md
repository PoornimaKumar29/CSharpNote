```cs
####employee.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Numerics;
using System.Text;
using System.Threading.Tasks;
using Microsoft.Data.SqlClient;
namespace connectd_demo
{
    public class employee
    {
        string ConnectionString = "Server= POORNIMA\\SQLSERVER2022; Database=SQL-D3;Trusted_Connection=True;";
       //another way to connect sql
       //string connectionString1 = "Data Source=LAPTOP-0TBPBTEL\\SQLEXPRESS;Initial Catalog=Hexa_Mar_25;Integrated Security=True";
        public void AddNewEmployee(int employee_id , string emp_name , string emp_email, long emp_phoone)
        {
            using (SqlConnection connection = new SqlConnection(ConnectionString))
            {
                string query = $"insert into employee(employee_id , emp_name , emp_email, emp_phoone)values(@employee_id , @emp_name, @emp_email, @emp_phoone)";
                SqlCommand cmd = new SqlCommand(query, connection);
                cmd.Parameters.AddWithValue("@employee_id", employee_id);
                cmd.Parameters.AddWithValue("@emp_name", emp_name);
                cmd.Parameters.AddWithValue("@emp_email", emp_email);
                cmd.Parameters.AddWithValue("@emp_phoone", emp_phoone);
                connection.Open();
                int rowsadded = cmd.ExecuteNonQuery();
                if (rowsadded > 0)
                {
                    Console.WriteLine("Record inserted successfully");
                }
                else
                {
                    Console.WriteLine("Something went wrong");
                }
            }
        }   
    }
}
####program.cs
using connectd_demo;

Console.WriteLine("Hello, World!");
employee emp = new employee();
emp.AddNewEmployee(105, "suryah", "surya@gmail.com", 9442143491);
Console.ReadLine();
```