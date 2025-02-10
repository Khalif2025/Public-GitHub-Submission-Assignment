Install-Package Microsoft.EntityFrameworkCore
Install-Package Microsoft.EntityFrameworkCore.SqlServer
Install-Package Microsoft.EntityFrameworkCore.Tools

 

using System;

public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }
}

 

using Microsoft.EntityFrameworkCore;

public class StudentContext : DbContext
{
    public DbSet<Student> Students { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer("Server=(localdb)\\mssqllocaldb;Database=StudentDB;Trusted_Connection=True;");
    }
}

using System;

class Program
{
    static void Main()
    {
        using (var context = new StudentContext())
        {
            // Ensure database is created
            context.Database.EnsureCreated();

            // Add a new student
            var student = new Student { Name = "John Doe", Age = 20 };
            context.Students.Add(student);
            context.SaveChanges();

            Console.WriteLine("Student added successfully!");
        }
    }
}

git init
git add .
git commit -m "Initial commit - Code-First EF Core Console App"

git remote add origin <your-repository-url>
git branch -M main
git push -u origin main

