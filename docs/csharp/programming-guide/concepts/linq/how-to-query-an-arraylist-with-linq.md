---
title: LINQ (C#) ile ArrayList 'i sorgulama
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: b8edb90d33c92324d4f76c7e6977641fe4499d9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345702"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a>LINQ (C#) ile ArrayList 'i sorgulama
<xref:System.Collections.ArrayList>gibi genel olmayan <xref:System.Collections.IEnumerable> koleksiyonlarını sorgulamak için LINQ kullanılırken, koleksiyondaki nesne türlerini yansıtacak şekilde Aralık değişkeninin türünü açıkça bildirmeniz gerekir. Örneğin, `Student` nesneleri <xref:System.Collections.ArrayList> varsa, [from yan tümcesinden](../../../language-reference/keywords/from-clause.md) aşağıdaki gibi görünmelidir:  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 Aralık değişkeninin türünü belirterek, <xref:System.Collections.ArrayList> her öğeyi bir `Student`olarak vurun.  
  
 Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması <xref:System.Linq.Enumerable.Cast%2A> yöntemini çağırmaya eşdeğerdir. Belirtilen tür dönüştürme gerçekleştirilemiyorsa <xref:System.Linq.Enumerable.Cast%2A> bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A>, genel olmayan <xref:System.Collections.IEnumerable> türlerinde çalışan iki standart sorgu Işleci yöntemleridir. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Collections.ArrayList>üzerinde basit bir sorgu gösterir. Bu örnek, kod <xref:System.Collections.ArrayList.Add%2A> yöntemini çağırdığında nesne başlatıcıları kullanır, ancak bu bir gereklilik değildir.  
  
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
