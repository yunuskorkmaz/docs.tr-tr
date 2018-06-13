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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="d7ee1-102">Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="d7ee1-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="d7ee1-103">Eşdeğişken arabirimi arabiriminde belirtilenlerden daha türetilmiş türler döndürülecek yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="d7ee1-104">Karşıtı arabirimi belirtilenlerden daha az türetilmiş türler arabiriminde parametrelerinin kabul etmek yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="d7ee1-105">.NET Framework 4'te birkaç varolan arabirimleri eşdeğişken hale geldi ve karşıtı.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="d7ee1-106">Bunlar <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="d7ee1-107">Genel koleksiyonlar türetilen türler için temel türleri çalışır yöntemleri yeniden kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="d7ee1-108">.NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (C#) varyans](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="d7ee1-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="d7ee1-109">Genel koleksiyonlar dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d7ee1-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="d7ee1-110">Aşağıdaki örnek Kovaryans desteği yararları gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="d7ee1-111">`PrintFullName` Yöntemi kabul koleksiyonu `IEnumerable<Person>` türünü bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="d7ee1-112">Ancak, onu bir koleksiyonu için tekrar kullanabilirsiniz `IEnumerable<Employee>` yazın, çünkü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="d7ee1-113">Genel koleksiyonları karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="d7ee1-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="d7ee1-114">Aşağıdaki örnekte, değişken karşıtı desteği yararları gösterilmektedir <xref:System.Collections.Generic.IComparer%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="d7ee1-115">`PersonComparer` Uygulayan sınıf `IComparer<Person>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="d7ee1-116">Ancak, bir dizi nesnelerin karşılaştırmak için bu sınıfı yeniden kullanabilirsiniz `Employee` yazın, çünkü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7ee1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7ee1-117">See Also</span></span>  
 [<span data-ttu-id="d7ee1-118">Genel arabirimler (C#) varyans</span><span class="sxs-lookup"><span data-stu-id="d7ee1-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
