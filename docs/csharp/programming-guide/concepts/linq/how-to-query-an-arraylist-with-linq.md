---
title: "Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama"
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: dca201a23b316cc16bc746ea920303814c8c7c87
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592927"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama
Gibi genel <xref:System.Collections.IEnumerable> olmayan koleksiyonları <xref:System.Collections.ArrayList>sorgulamak için LINQ kullanılırken, koleksiyondaki nesne türlerini yansıtmak için Aralık değişkeninin türünü açıkça bildirmeniz gerekir. Örneğin, bir <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa, [from yan tümcesi](../../../language-reference/keywords/from-clause.md) şuna benzemelidir:  
  
```  
var query = from Student s in arrList  
...  
```  
  
 Aralık değişkeninin türünü belirterek, <xref:System.Collections.ArrayList> içindeki her bir `Student`öğeyi öğesine vurarak.  
  
 Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması <xref:System.Linq.Enumerable.Cast%2A> yöntemi çağırma ile eşdeğerdir. <xref:System.Linq.Enumerable.Cast%2A>Belirtilen tür dönüştürme gerçekleştirilemiyorsa bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A>ve <xref:System.Linq.Enumerable.OfType%2A> genel<xref:System.Collections.IEnumerable> olmayan türlerde çalışan iki standart sorgu işleci yöntemi vardır. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üzerinde <xref:System.Collections.ArrayList>basit bir sorgu gösterir. Bu örnekte kod <xref:System.Collections.ArrayList.Add%2A> yöntemi çağırdığında nesne başlatıcılarının kullanıldığı, ancak bu bir gereksinim olmadığı unutulmamalıdır.  
  
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

- [LINQ to Objects (C#)](./linq-to-objects.md)
