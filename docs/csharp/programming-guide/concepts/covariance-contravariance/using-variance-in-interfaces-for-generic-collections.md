---
title: Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: b891ccde93e18baf5d5e814911666e9c6268e009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169746"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)
Ortak değişken arabirimi, yöntemlerinin arabirimde belirtilenlerden daha fazla türemiş türleri döndürmesine olanak tanır. Karşıt arabirim, yöntemlerinin arabirimde belirtilenlerden daha az türdeki parametreleri kabul etmesine olanak tanır.  
  
 .NET Framework 4'te, varolan birkaç arabirim bir arada ve zıt hale geldi. Bunlar <xref:System.Collections.Generic.IEnumerable%601> arasında <xref:System.IComparable%601>. Bu, türemiş tür koleksiyonları için temel türlerin genel koleksiyonlarıyla çalışan yöntemleri yeniden kullanmanıza olanak tanır.  
  
 .NET Framework'deki varyant arabirimlerinin listesi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)bölümüne bakın.  
  
## <a name="converting-generic-collections"></a>Genel Koleksiyonları Dönüştürme  
 Aşağıdaki örnek, <xref:System.Collections.Generic.IEnumerable%601> arabirimdeki covariance desteğinin faydalarını göstermektedir. Yöntem, `PrintFullName` `IEnumerable<Person>` parametre olarak türün bir koleksiyonunu kabul eder. Ancak, `IEnumerable<Employee>` `Employee` devraldığı `Person`için türünün bir koleksiyon için yeniden kullanabilirsiniz.  
  
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
  
## <a name="comparing-generic-collections"></a>Genel Koleksiyonları Karşılaştırma  
 Aşağıdaki örnekte, <xref:System.Collections.Generic.IComparer%601> arabirimdeki kontravariance desteğinin yararları gösterin. `PersonComparer` sınıfı, `IComparer<Person>` arabirimini uygular. Ancak, bu sınıfı, `Employee` `Employee` devraldığı `Person`için türün nesnelerin ini karşılaştırmak için yeniden kullanabilirsiniz.  
  
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
