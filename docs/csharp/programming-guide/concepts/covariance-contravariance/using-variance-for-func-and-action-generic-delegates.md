---
title: Func ve eylem genel temsilcileri için varyans kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 2e2c5c80c54ff6788653f63a5bda85598e73824c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595244"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Func ve eylem genel temsilcileri için varyans kullanma (C#)
Bu örnekler, `Func` ve ' de yöntemlerin yeniden kullanımını etkinleştirmek ve kodunuzda daha `Action` fazla esneklik sağlamak için ve genel temsilcilerde kovaryans ve değişken varyans kullanımını gösterir.  
  
 Kovaryans ve değişken varyans hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Birlikte değişken tür parametrelerine sahip temsilciler kullanma  
 Aşağıdaki örnekte, genel `Func` temsilcilerde kovaryans desteğinin avantajları gösterilmektedir. Yöntemi, `String` türünün bir parametresini alır ve `Employee` türünün bir nesnesini döndürür. `FindByTitle` Ancak, devraldığından `Func<String, Person>` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.  
  
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
 Aşağıdaki örnekte, genel `Action` Temsilcilerde değişken varyans desteğinin avantajları gösterilmektedir. Yöntemi, `Person` türünün bir parametresini alır. `AddToContacts` Ancak, devraldığından `Action<Employee>` `Employee` `Person`bu yöntemi temsilciye atayabilirsiniz.  
  
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
- [Genel Türler](~/docs/standard/generics/index.md)
