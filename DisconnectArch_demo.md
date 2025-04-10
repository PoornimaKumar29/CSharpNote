```cs
###program.cs
// See https://aka.ms/new-console-template for more information
using disconnect_Arch;


Disconnected disconnect = new Disconnected();
bool keeprun = true;
while (keeprun)
{
    Console.WriteLine("Enter the choice 1-4 \n 1.GetallEmployees \n " +
        "2. Add New employee \n 3.Update Employee \n 4.Delete Employee " +
        "\n 5.Exit");
    int choice = Convert.ToInt32(Console.ReadLine());

    switch (choice)
    {
        case 1:
            disconnect.Getallemployee();
            break;
        case 2:
            {
                employee emp = GetEmployeeInfo();
                disconnect.addnewemployee(emp);
                break;
            }

        case 3:
            {
                Console.WriteLine("Enter the employee id to Update ");

                employee updateEmp = GetEmployeeInfo();
                disconnect.updateemployee(updateEmp);
                break;
            }

        case 4:
            {
                Console.WriteLine("Enter the employee id to Delete ");
                int id = Convert.ToInt32(Console.ReadLine());
                disconnect.DeleteEmployee(id);
                break;
            }
        case 5:
            {
                keeprun = false;
                Console.WriteLine("Exiting program...");
                break;
            }

    }
}
disconnect.Getallemployee();

static employee GetEmployeeInfo()
{
    employee employee = new employee();
    Console.WriteLine("Entet the employeeId,Name,Department");
    employee.id = Convert.ToInt32(Console.ReadLine());
    employee.name = Console.ReadLine();
    employee.Department = Console.ReadLine();
   
    return employee;
}
//employeeCRUD.AddNewEmployee(employee);
Console.ReadLine();

###employee.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace disconnect_Arch
{
    public class employee
    {
        public int id { get; set; }
        public string name { get; set; }
        public string Department { get; set; }
    }
}


###Disconnected.cs
using System;
using System.Collections.Generic;
using System.Data;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.Data.SqlClient;

namespace disconnect_Arch
{
    public class Disconnected
    {
        string connectionstring = @"Server=POORNIMA\SQLSERVER2022;Database=SQL-D3;Trusted_connection=True;TrustServerCertificate=True";
        public void Getallemployee()
        {
            try
            {
                using (SqlConnection connect = new SqlConnection(connectionstring))
                {
                    SqlDataAdapter adapter = new SqlDataAdapter("select * from emp", connect);
                    DataSet ds = new DataSet();
                    adapter.Fill(ds, "emp");
                    foreach (DataRow dr in ds.Tables["emp"].Rows)
                    {
                        Console.WriteLine($"Id:{dr["Id"]} \t Name={dr[1]} \t department={dr[2]}");
                    }
                }
            }
            catch (Exception ex)
            {
                throw new Exception(ex.Message);
            }
        }
        public void addnewemployee(employee employee)
        {
            try
            {
                using (SqlConnection connection = new SqlConnection(connectionstring))
                {
                    SqlDataAdapter adapter = new SqlDataAdapter("select * from emp", connection);
                    SqlCommandBuilder builder = new SqlCommandBuilder(adapter);
                    DataSet ds = new DataSet();
                    adapter.Fill(ds, "emp");
                    DataRow newrow = ds.Tables["emp"].NewRow();
                    newrow["id"] = employee.id;
                    newrow["NAme"] = employee.name;
                    newrow["Department"] = employee.Department;
                    ds.Tables["emp"].Rows.Add(newrow);
                    adapter.Update(ds, "emp");
                    Console.WriteLine("record inserted successfully");

                }
            }
            catch (Exception ex)
            {
                throw new Exception(ex.Message);
            }
        }
        public void updateemployee(employee employee)
        {
            try
            {
                using (SqlConnection connection = new SqlConnection(connectionstring))
                {
                    SqlDataAdapter adapter = new SqlDataAdapter("select * from emp", connection);
                    SqlCommandBuilder builder = new SqlCommandBuilder(adapter);
                    DataSet ds = new DataSet();
                    adapter.Fill(ds, "emp");
                    DataTable employeetable = ds.Tables["emp"];
                    employeetable.PrimaryKey = new DataColumn[] { employeetable.Columns["id"] };
                    DataRow row = employeetable.Rows.Find(employee.id);// adding a new row into dataTable
                    if (row != null)
                    {
                        //row["Id"] = emp.Id;
                        row["id"] = employee.id;
                        row["Name"] = employee.name;
                        row["Department"] = employee.Department;
                        adapter.Update(ds, "emp");
                    }
                    Console.WriteLine("record Updated successfully");

                }
            }
            catch (Exception ex)
            {
                throw new Exception(ex.Message);

            }
        }

            //---
            public void DeleteEmployee(int id)
        {
            try
            {
                using (SqlConnection connection = new SqlConnection(connectionstring))
                {
                    SqlDataAdapter adapter = new SqlDataAdapter("Select * from Emp", connection);
                    SqlCommandBuilder builder = new SqlCommandBuilder(adapter);
                    DataSet ds = new DataSet();
                    adapter.Fill(ds, "emp");
                    DataTable employeeTable = ds.Tables["emp"];
                    employeeTable.PrimaryKey = new DataColumn[] { employeeTable.Columns["id"] };
                    DataRow row = employeeTable.Rows.Find(id);// adding a new row into dataTable
                    if (row != null)
                    {
                        row.Delete();
                        adapter.Update(ds, "emp");
                        Console.WriteLine("Record Deleted successfully");
                    }
                    else
                    {
                        Console.WriteLine(" Employee Id was not found");
                    }

                }
            }
            catch (Exception ex)
            {

                throw new Exception(ex.Message);
            }
        

    }
    }
}

```