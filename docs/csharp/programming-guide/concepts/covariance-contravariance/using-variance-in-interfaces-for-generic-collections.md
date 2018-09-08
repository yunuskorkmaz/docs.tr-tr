---
title: Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 66a1eac33d5f715f52bd83c43bac4452df41aabd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196952"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma
Birlikte değişen bir arabirimin yöntemlerinin dönüş arabiriminde belirtilenlerden daha türetilmiş türleri sağlar. Bir değişken karşıtı arabirimi belirtilenlerden daha az türetilmiş türler arabiriminde parametrelerini kabul edecek şekilde yöntemlerini sağlar.  
  
 .NET Framework 4'te çeşitli mevcut arabirimlerin birlikte değişen hale geldi ve değişken karşıtı. Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601>. Bu, türetilmiş türler için temel türleri genel koleksiyonlar ile çalışan yöntemlerini kullanmayı sağlar.  
  
 .NET Framework'teki değişken arabirimler listesi için bkz. [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Genel koleksiyonlar dönüştürme  
 Kovaryans destek avantajları aşağıdaki örnekte <xref:System.Collections.Generic.IEnumerable%601> arabirimi. `PrintFullName` Yöntemi koleksiyonunu kabul `IEnumerable<Person>` türü bir parametre olarak. Ancak, bir koleksiyonu için kullanabilirsiniz `IEnumerable<Employee>` türü için `Employee` devralan `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a>Genel koleksiyonları karşılaştırma  
 Aşağıdaki örnekte kontravaryans destek avantajlarını <xref:System.Collections.Generic.IComparer%601> arabirimi. `PersonComparer` Sınıfının Implements `IComparer<Person>` arabirimi. Ancak, bir dizi nesnelerini karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` türü için `Employee` devralan `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
