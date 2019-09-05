---
title: "Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama"
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 51c42296b8acb6be1c9c4505f9af3d6fbaf248ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253445"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="8cbd4-102">Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama</span><span class="sxs-lookup"><span data-stu-id="8cbd4-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="8cbd4-103">Gibi genel <xref:System.Collections.IEnumerable> olmayan koleksiyonları <xref:System.Collections.ArrayList>sorgulamak için LINQ kullanılırken, koleksiyondaki nesne türlerini yansıtmak için Aralık değişkeninin türünü açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="8cbd4-104">Örneğin, bir <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa, [from yan tümcesi](../../../language-reference/keywords/from-clause.md) şuna benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="8cbd4-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp  
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="8cbd4-105">Aralık değişkeninin türünü belirterek, <xref:System.Collections.ArrayList> içindeki her bir `Student`öğeyi öğesine vurarak.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="8cbd4-106">Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması <xref:System.Linq.Enumerable.Cast%2A> yöntemi çağırma ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="8cbd4-107"><xref:System.Linq.Enumerable.Cast%2A>Belirtilen tür dönüştürme gerçekleştirilemiyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="8cbd4-108"><xref:System.Linq.Enumerable.Cast%2A>ve <xref:System.Linq.Enumerable.OfType%2A> genel<xref:System.Collections.IEnumerable> olmayan türlerde çalışan iki standart sorgu işleci yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="8cbd4-109">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8cbd4-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cbd4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8cbd4-110">Example</span></span>  
 <span data-ttu-id="8cbd4-111">Aşağıdaki örnek, üzerinde <xref:System.Collections.ArrayList>basit bir sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="8cbd4-112">Bu örnekte kod <xref:System.Collections.ArrayList.Add%2A> yöntemi çağırdığında nesne başlatıcılarının kullanıldığı, ancak bu bir gereksinim olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8cbd4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cbd4-113">See also</span></span>

- [<span data-ttu-id="8cbd4-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="8cbd4-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
