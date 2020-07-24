---
title: Func ve eylem genel temsilcileri için varyans kullanma (C#)
description: Kod içinde daha fazla esneklik sağlamak için Func ve eylem genel temsilcilerde kovaryans ve değişken varyans kullanma hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: d7174b0f734d10ab69d0936cb5ca4aa2f4fafdf7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105714"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Func ve eylem genel temsilcileri için varyans kullanma (C#)
Bu örnekler, ve ' de `Func` `Action` yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.  
  
 Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Birlikte değişken tür parametrelerine sahip temsilciler kullanma  
 Aşağıdaki örnekte, genel temsilcilerde kovaryans desteğinin avantajları gösterilmektedir `Func` . `FindByTitle`Yöntemi, türünün bir parametresini alır `String` ve türünün bir nesnesini döndürür `Employee` . Ancak, `Func<String, Person>` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Değişken karşıtı tür parametreleriyle temsilciler kullanma  
 Aşağıdaki örnekte, genel Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir `Action` . `AddToContacts`Yöntemi, türünün bir parametresini alır `Person` . Ancak, `Action<Employee>` devraldığından bu yöntemi temsilciye atayabilirsiniz `Employee` `Person` .  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kovaryans ve değişken varyans (C#)](./index.md)
- [Genel Türler](../../../../standard/generics/index.md)
