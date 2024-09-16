```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }

    // Thêm phương thức ToString() để in thông tin học sinh dễ dàng hơn
    public override string ToString()
    {
        return $"Id: {Id}, Name: {Name}, Age: {Age}";
    }
}

public class School
{
    public static void Main()
    {
        // Khởi tạo danh sách học sinh
        List<Student> students = new List<Student>
        {
            new Student { Id = 1, Name = "Minh", Age = 21 },
            new Student { Id = 2, Name = "Phuc", Age = 15 },
            new Student { Id = 3, Name = "Duy", Age = 17 },
            new Student { Id = 4, Name = "An", Age = 20 },
            new Student { Id = 5, Name = "Nghia", Age = 25 }
        };

        // a. In toàn bộ danh sách học sinh
        PrintAllStudents(students);

        // b. Tìm và in ra danh sách các học sinh có tuổi từ 15 đến 18
        PrintStudentsByAgeRange(students, 15, 18);

        // c. Tìm và in ra học sinh có tên bắt đầu bằng chữ "A"
        PrintStudentsByNamePrefix(students, "A");

        // d. Tính tổng tuổi của tất cả học sinh
        PrintTotalAge(students);

        // e. Tìm và in ra học sinh có tuổi lớn nhất
        PrintOldestStudent(students);

        // f. Sắp xếp danh sách học sinh theo tuổi tăng dần và in ra danh sách sau khi sắp xếp
        PrintSortedStudentsByAge(students);
    }

    private static void PrintAllStudents(List<Student> students)
    {
        Console.WriteLine("Danh sachh toan bo hoc sinh:");
        foreach (var student in students)
        {
            Console.WriteLine(student);
        }
        Console.WriteLine();
    }

    private static void PrintStudentsByAgeRange(List<Student> students, int minAge, int maxAge)
    {
        var filteredStudents = students.Where(s => s.Age >= minAge && s.Age <= maxAge).ToList();
        Console.WriteLine($"Danh sach hoc sinh co tuoi tu {minAge} toi {maxAge}:");
        foreach (var student in filteredStudents)
        {
            Console.WriteLine(student);
        }
        Console.WriteLine();
    }

    private static void PrintStudentsByNamePrefix(List<Student> students, string prefix)
    {
        var filteredStudents = students.Where(s => s.Name.StartsWith(prefix)).ToList();
        Console.WriteLine($"Danh sach hoc sinh bat dau bang chu '{prefix}':");
        foreach (var student in filteredStudents)
        {
            Console.WriteLine(student);
        }
        Console.WriteLine();
    }

    private static void PrintTotalAge(List<Student> students)
    {
        var totalAge = students.Sum(s => s.Age);
        Console.WriteLine($"Tong tuoi cua tat ca hoc sinh: {totalAge}");
        Console.WriteLine();
    }

    private static void PrintOldestStudent(List<Student> students)
    {
        var oldestStudent = students.OrderByDescending(s => s.Age).First();
        Console.WriteLine("Hoc sinh co tuoi lon nhat:");
        Console.WriteLine(oldestStudent);
        Console.WriteLine();
    }

    private static void PrintSortedStudentsByAge(List<Student> students)
    {
        var sortedStudents = students.OrderBy(s => s.Age).ToList();
        Console.WriteLine("Sap xep hoc sinh theo tuoi tang dan:");
        foreach (var student in sortedStudents)
        {
            Console.WriteLine(student);
        }
        Console.WriteLine();
    }
}
