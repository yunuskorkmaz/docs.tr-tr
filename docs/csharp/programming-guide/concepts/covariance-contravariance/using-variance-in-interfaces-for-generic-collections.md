---
title: Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 53aaf49ee0802c0d207e0b0a29661cee7c628b4d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595209"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="ca41e-102">Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="ca41e-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="ca41e-103">Birlikte değişken arabirimi, yöntemlerinin arabirimde belirtilenden daha fazla türetilmiş tür döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca41e-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="ca41e-104">Değişken karşıtı bir arabirim, yöntemlerinin, arabirimde belirtilenden daha az türetilmiş türdeki parametreleri kabul etmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca41e-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="ca41e-105">.NET Framework 4 ' te, bazı mevcut arabirimler birlikte değişken ve değişken karşıtı hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca41e-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="ca41e-106">Bunlar ve <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IComparable%601>içerir.</span><span class="sxs-lookup"><span data-stu-id="ca41e-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="ca41e-107">Bu, türetilmiş türlerin koleksiyonları için genel temel tür koleksiyonlarıyla çalışan yöntemleri yeniden kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca41e-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="ca41e-108">.NET Framework değişken arabirimlerin listesi için bkz. [Genel Arabirimlerde VaryansC#()](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ca41e-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="ca41e-109">Genel koleksiyonları dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ca41e-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="ca41e-110">Aşağıdaki örnekte, <xref:System.Collections.Generic.IEnumerable%601> arabirimindeki Kovaryans desteğinin avantajları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca41e-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="ca41e-111">Yöntemi `PrintFullName` , `IEnumerable<Person>` türü bir koleksiyonu bir parametre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ca41e-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="ca41e-112">Ancak, devraldığından `IEnumerable<Employee>` `Employee` `Person`bir tür koleksiyonu için onu yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca41e-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="ca41e-113">Genel koleksiyonları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ca41e-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="ca41e-114">Aşağıdaki örnek, <xref:System.Collections.Generic.IComparer%601> arabirimindeki fark desteğinin avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="ca41e-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="ca41e-115">`PersonComparer` Sınıfı ,`IComparer<Person>` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="ca41e-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="ca41e-116">Ancak, devraldığından `Employee` `Employee` `Person`tür bir nesne dizisini karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca41e-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca41e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca41e-117">See also</span></span>

- [<span data-ttu-id="ca41e-118">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="ca41e-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
