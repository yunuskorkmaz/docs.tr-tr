---
title: İşlev ve eylem genel temsilcileri (C#) için varyans kullanma
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: f517eea07588bb01ef903c8311126eab872bd735
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540604"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>İşlev ve eylem genel temsilcileri (C#) için varyans kullanma
Bu örnekler Kovaryans ve kontravaryans nasıl kazandırabileceğinizi `Func` ve `Action` yöntemleri kullanılmasını etkinleştirin ve kodunuzu daha fazla esneklik sağlamak için genel temsilciler.  
  
 Kovaryans ve kontravaryans hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Birlikte değişken tür parametreleri ile kullanma  
 Kovaryans genel destek avantajları aşağıdaki örnekte `Func` temsilciler. `FindByTitle` Yöntemi, bir parametre alır `String` yazın ve bir nesne döndürür `Employee` türü. Ancak, bu yönteme atayabilirsiniz `Func<String, Person>` çünkü temsilci `Employee` devralan `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Değişken karşıtı tür parametreleri ile kullanma  
 Aşağıdaki örnekte genel kontravaryans destek avantajlarını `Action` temsilciler. `AddToContacts` Yöntemi, bir parametre alır `Person` türü. Ancak, bu yönteme atayabilirsiniz `Action<Employee>` çünkü temsilci `Employee` devralan `Person`.  
  
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

- [Kovaryans ve kontravaryans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Genel Türler](~/docs/standard/generics/index.md)
