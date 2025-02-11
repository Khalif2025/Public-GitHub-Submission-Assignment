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
