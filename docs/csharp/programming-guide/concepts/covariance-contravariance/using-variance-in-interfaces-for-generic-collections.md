---
title: Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 5f5531e17a530ed840108df2cf9bf829b2beb656
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241363"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)
Birlikte değişken arabirimi, yöntemlerinin arabirimde belirtilenden daha fazla türetilmiş tür döndürmesini sağlar. Değişken karşıtı bir arabirim, yöntemlerinin, arabirimde belirtilenden daha az türetilmiş türdeki parametreleri kabul etmesine olanak sağlar.  
  
 .NET Framework 4 ' te, bazı mevcut arabirimler birlikte değişken ve değişken karşıtı hale gelmiştir. Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve içerir <xref:System.IComparable%601> . Bu, türetilmiş türlerin koleksiyonları için genel temel tür koleksiyonlarıyla çalışan yöntemleri yeniden kullanmanıza olanak sağlar.  
  
 .NET 'teki değişken arabirimlerin bir listesi için bkz. [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Genel koleksiyonları dönüştürme  
 Aşağıdaki örnekte, arabirimindeki Kovaryans desteğinin avantajları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> . `PrintFullName`Yöntemi, türü bir koleksiyonu `IEnumerable<Person>` bir parametre olarak kabul eder. Ancak, devraldığından bir tür koleksiyonu için onu yeniden kullanabilirsiniz `IEnumerable<Employee>` `Employee` `Person` .  
  
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
 Aşağıdaki örnek, arabirimindeki fark desteğinin avantajlarından yararlanır <xref:System.Collections.Generic.IComparer%601> . `PersonComparer` sınıfı, `IComparer<Person>` arabirimini uygular. Ancak, devraldığından tür bir nesne dizisini karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` `Employee` `Person` .  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)
