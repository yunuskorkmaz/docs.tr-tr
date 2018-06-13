---
title: Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 7f1c44ecc831a7eb35541a432bc776c512bd10a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340469"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma
Eşdeğişken arabirimi arabiriminde belirtilenlerden daha türetilmiş türler döndürülecek yöntemlerini sağlar. Karşıtı arabirimi belirtilenlerden daha az türetilmiş türler arabiriminde parametrelerinin kabul etmek yöntemlerini sağlar.  
  
 .NET Framework 4'te birkaç varolan arabirimleri eşdeğişken hale geldi ve karşıtı. Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601>. Genel koleksiyonlar türetilen türler için temel türleri çalışır yöntemleri yeniden kullanmanıza olanak sağlar.  
  
 .NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Genel koleksiyonlar dönüştürme  
 Aşağıdaki örnek Kovaryans desteği yararları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> arabirimi. `PrintFullName` Yöntemi kabul koleksiyonu `IEnumerable<Person>` türünü bir parametre olarak. Ancak, onu bir koleksiyonu için tekrar kullanabilirsiniz `IEnumerable<Employee>` yazın, çünkü `Employee` devralır `Person`.  
  
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
 Aşağıdaki örnekte, değişken karşıtı desteği yararları gösterilmektedir <xref:System.Collections.Generic.IComparer%601> arabirimi. `PersonComparer` Uygulayan sınıf `IComparer<Person>` arabirimi. Ancak, bir dizi nesnelerin karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` yazın, çünkü `Employee` devralır `Person`.  
  
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
 [Genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
