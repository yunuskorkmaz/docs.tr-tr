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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="b42cd-102">Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="b42cd-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="b42cd-103">Ortak değişken arabirimi, yöntemlerinin arabirimde belirtilenlerden daha fazla türemiş türleri döndürmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b42cd-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="b42cd-104">Karşıt arabirim, yöntemlerinin arabirimde belirtilenlerden daha az türdeki parametreleri kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b42cd-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="b42cd-105">.NET Framework 4'te, varolan birkaç arabirim bir arada ve zıt hale geldi.</span><span class="sxs-lookup"><span data-stu-id="b42cd-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="b42cd-106">Bunlar <xref:System.Collections.Generic.IEnumerable%601> arasında <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="b42cd-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="b42cd-107">Bu, türemiş tür koleksiyonları için temel türlerin genel koleksiyonlarıyla çalışan yöntemleri yeniden kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b42cd-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="b42cd-108">.NET Framework'deki varyant arabirimlerinin listesi için [Genel Arabirimlerde Varyans (C#)](./variance-in-generic-interfaces.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b42cd-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="b42cd-109">Genel Koleksiyonları Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b42cd-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="b42cd-110">Aşağıdaki örnek, <xref:System.Collections.Generic.IEnumerable%601> arabirimdeki covariance desteğinin faydalarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b42cd-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="b42cd-111">Yöntem, `PrintFullName` `IEnumerable<Person>` parametre olarak türün bir koleksiyonunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b42cd-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="b42cd-112">Ancak, `IEnumerable<Employee>` `Employee` devraldığı `Person`için türünün bir koleksiyon için yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42cd-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="b42cd-113">Genel Koleksiyonları Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b42cd-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="b42cd-114">Aşağıdaki örnekte, <xref:System.Collections.Generic.IComparer%601> arabirimdeki kontravariance desteğinin yararları gösterin.</span><span class="sxs-lookup"><span data-stu-id="b42cd-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="b42cd-115">`PersonComparer` sınıfı, `IComparer<Person>` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b42cd-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="b42cd-116">Ancak, bu sınıfı, `Employee` `Employee` devraldığı `Person`için türün nesnelerin ini karşılaştırmak için yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42cd-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b42cd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b42cd-117">See also</span></span>

- [<span data-ttu-id="b42cd-118">Genel Arabirimlerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="b42cd-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
