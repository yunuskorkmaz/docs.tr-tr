---
title: 'Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 7cf804bc86dc6f8378e62e01ba373bb82821de52
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740240"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama
LINQ Sorgu genel olmayan için kullanırken <xref:System.Collections.IEnumerable> koleksiyonlar gibi <xref:System.Collections.ArrayList>, koleksiyon içindeki nesneler belirli türünü yansıtacak şekilde Aralık değişkeninin türünü açıkça belirtmesi gerekir. Örneğin, bir <xref:System.Collections.ArrayList> , `Student` nesneleri, [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md) şöyle görünmelidir:  
  
```  
var query = from Student s in arrList  
...  
```  
  
 Aralık değişkeninin türünü belirterek, her öğe atama <xref:System.Collections.ArrayList> için bir `Student`.  
  
 Bir açık olarak aralık değişkeni bir sorgu ifadesinde kullanımını çağırmakla eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> yöntemi. <xref:System.Linq.Enumerable.Cast%2A> Belirtilen dönüştürme gerçekleştirilemediği takdirde, özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan üzerinde çalışan iki standart sorgu işleci yöntemleri <xref:System.Collections.IEnumerable> türleri. Daha fazla bilgi için [LINQ Sorgu işlemlerinde tür ilişkileri](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üzerinden basit bir sorguyu gösterir. bir <xref:System.Collections.ArrayList>. Bu örnek kodu çağırdığında nesne başlatıcıları kullanır Not <xref:System.Collections.ArrayList.Add%2A> yöntemi, ancak bu zorunlu değildir.  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:   
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
