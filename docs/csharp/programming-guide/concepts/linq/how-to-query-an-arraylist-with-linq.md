---
title: LINQ (C#) ile ArrayList nasıl sorgulanır?
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: fa185ba3793b628b0d65e1f513a70ec68f6f2425
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168940"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>LINQ (C#) ile ArrayList nasıl sorgulanır?
Gibi genel <xref:System.Collections.IEnumerable> olmayan koleksiyonları sorgulamak için <xref:System.Collections.ArrayList>LINQ kullanırken, aralık değişkeninin türünü koleksiyondaki nesnelerin belirli türünü yansıtacak şekilde açıkça bildirmeniz gerekir. Örneğin, bir <xref:System.Collections.ArrayList> nesneniz `Student` varsa, from yan [tümceniz](../../../language-reference/keywords/from-clause.md) şu şekilde görünmelidir:  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 Aralık değişkeninin türünü belirterek, her bir <xref:System.Collections.ArrayList> öğeyi `Student`bir .'ye  
  
 Sorgu ifadesinde açıkça yazılan bir aralık değişkeninin kullanımı, <xref:System.Linq.Enumerable.Cast%2A> yöntemi çağırmaya eşdeğerdir. <xref:System.Linq.Enumerable.Cast%2A>belirtilen döküm gerçekleştirilemiyorsa bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A>ve <xref:System.Linq.Enumerable.OfType%2A> genel <xref:System.Collections.IEnumerable> olmayan türler üzerinde çalışan iki Standart Sorgu Operatörü yöntemidir. Daha fazla bilgi için [LINQ Sorgu İşlemlerinde Tür İlişkileri'ne](./type-relationships-in-linq-query-operations.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte basit bir <xref:System.Collections.ArrayList>sorgu . Bu örnekte, kod <xref:System.Collections.ArrayList.Add%2A> yöntemi aradığında nesne baş harflerini kullandığını, ancak bu bir gereklilik olmadığını unutmayın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesnelere LINQ (C#)](./linq-to-objects.md)
