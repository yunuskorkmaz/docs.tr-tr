---
title: Func ve eylem genel temsilcileri için varyans kullanma (C#)
description: Kod içinde daha fazla esneklik sağlamak için Func ve eylem genel temsilcilerde kovaryans ve değişken varyans kullanma hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 613470d7870aa6a917d19904a92e56f0e61f1ed9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176350"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="2a511-103">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="2a511-103">Using Variance for Func and Action Generic Delegates (C#)</span></span>

<span data-ttu-id="2a511-104">Bu örnekler, ve ' de `Func` `Action` yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a511-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="2a511-105">Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="2a511-105">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="2a511-106">Birlikte değişken tür parametrelerine sahip temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="2a511-106">Using Delegates with Covariant Type Parameters</span></span>  

 <span data-ttu-id="2a511-107">Aşağıdaki örnekte, genel temsilcilerde kovaryans desteğinin avantajları gösterilmektedir `Func` .</span><span class="sxs-lookup"><span data-stu-id="2a511-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="2a511-108">`FindByTitle`Yöntemi, türünün bir parametresini alır `String` ve türünün bir nesnesini döndürür `Employee` .</span><span class="sxs-lookup"><span data-stu-id="2a511-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="2a511-109">Ancak, `Func<String, Person>` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .</span><span class="sxs-lookup"><span data-stu-id="2a511-109">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="2a511-110">Değişken karşıtı tür parametreleriyle temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="2a511-110">Using Delegates with Contravariant Type Parameters</span></span>  

 <span data-ttu-id="2a511-111">Aşağıdaki örnekte, genel Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir `Action` .</span><span class="sxs-lookup"><span data-stu-id="2a511-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="2a511-112">`AddToContacts`Yöntemi, türünün bir parametresini alır `Person` .</span><span class="sxs-lookup"><span data-stu-id="2a511-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="2a511-113">Ancak, `Action<Employee>` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .</span><span class="sxs-lookup"><span data-stu-id="2a511-113">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a511-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a511-114">See also</span></span>

- [<span data-ttu-id="2a511-115">Kovaryans ve değişken varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="2a511-115">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="2a511-116">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="2a511-116">Generics</span></span>](../../../../standard/generics/index.md)
