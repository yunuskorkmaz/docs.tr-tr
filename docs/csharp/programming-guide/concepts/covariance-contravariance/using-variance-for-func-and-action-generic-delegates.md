---
title: Func ve Action Generic Delegeler için Varyans Kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 17f55d594ad4364fd29c8f6e41bd6ad2445b0986
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169798"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Func ve Action Generic Delegeler için Varyans Kullanma (C#)
Bu örnekler, yöntemlerin `Func` yeniden kullanılmasını sağlamak ve kodunuzda `Action` daha fazla esneklik sağlamak için genel temsilcilerde tutarlılık ve kontrayansın nasıl kullanılacağını gösterir.  
  
 Covariance ve contravariance hakkında daha fazla bilgi için, [Temsilciler (C#) Varyans](./variance-in-delegates.md)bakın.  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Eşdeğişken Türü Parametreleri olan Temsilcileri Kullanma  
 Aşağıdaki örnek, genel `Func` temsilcilerdeki covariance desteğinin faydalarını göstermektedir. Yöntem, `FindByTitle` türün bir `String` parametresini alır ve `Employee` türün bir nesnesini döndürür. Ancak, `Employee` devraldığı `Person`için bu `Func<String, Person>` yöntemi temsilciye atayabilirsiniz.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Karşıt Tür Parametreleri Olan Delegeleri Kullanma  
 Aşağıdaki örnek, genel `Action` temsilcilerdeki kontravariance desteğinin faydalarını göstermektedir. Yöntem, `AddToContacts` türün bir `Person` parametresini alır. Ancak, `Employee` devraldığı `Person`için bu `Action<Employee>` yöntemi temsilciye atayabilirsiniz.  
  
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

- [Covariance ve Contravariance (C#)](./index.md)
- [Genel Türler](../../../../standard/generics/index.md)
