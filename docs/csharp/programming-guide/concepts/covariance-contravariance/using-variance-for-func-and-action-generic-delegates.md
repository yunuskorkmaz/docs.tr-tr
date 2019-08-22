---
title: Func ve eylem genel temsilcileri için varyans kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: bbfc41fb8ab3e7d800f1eb03098e02056e694872
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659916"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="0901a-102">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0901a-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="0901a-103">Bu örnekler, `Func` ve ' de yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha `Action` fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0901a-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="0901a-104">Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="0901a-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="0901a-105">Birlikte değişken tür parametrelerine sahip temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="0901a-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="0901a-106">Aşağıdaki örnekte, genel `Func` temsilcilerde kovaryans desteğinin avantajları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0901a-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="0901a-107">Yöntemi, `String` türünün bir parametresini alır ve `Employee` türünün bir nesnesini döndürür. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="0901a-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="0901a-108">Ancak, devraldığından `Func<String, Person>` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0901a-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="0901a-109">Değişken karşıtı tür parametreleriyle temsilciler kullanma</span><span class="sxs-lookup"><span data-stu-id="0901a-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="0901a-110">Aşağıdaki örnekte, genel `Action` Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0901a-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="0901a-111">Yöntemi, `Person` türünün bir parametresini alır. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="0901a-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="0901a-112">Ancak, devraldığından `Action<Employee>` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0901a-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0901a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0901a-113">See also</span></span>

- [<span data-ttu-id="0901a-114">Kovaryans ve değişken varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="0901a-114">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="0901a-115">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="0901a-115">Generics</span></span>](../../../../standard/generics/index.md)
