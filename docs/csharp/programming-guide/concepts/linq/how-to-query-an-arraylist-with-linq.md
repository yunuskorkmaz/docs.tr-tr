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
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="99a83-102">LINQ (C#) ile ArrayList nasıl sorgulanır?</span><span class="sxs-lookup"><span data-stu-id="99a83-102">How to query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="99a83-103">Gibi genel <xref:System.Collections.IEnumerable> olmayan koleksiyonları sorgulamak için <xref:System.Collections.ArrayList>LINQ kullanırken, aralık değişkeninin türünü koleksiyondaki nesnelerin belirli türünü yansıtacak şekilde açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99a83-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="99a83-104">Örneğin, bir <xref:System.Collections.ArrayList> nesneniz `Student` varsa, from yan [tümceniz](../../../language-reference/keywords/from-clause.md) şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="99a83-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="99a83-105">Aralık değişkeninin türünü belirterek, her bir <xref:System.Collections.ArrayList> öğeyi `Student`bir .'ye</span><span class="sxs-lookup"><span data-stu-id="99a83-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="99a83-106">Sorgu ifadesinde açıkça yazılan bir aralık değişkeninin kullanımı, <xref:System.Linq.Enumerable.Cast%2A> yöntemi çağırmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="99a83-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="99a83-107"><xref:System.Linq.Enumerable.Cast%2A>belirtilen döküm gerçekleştirilemiyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99a83-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="99a83-108"><xref:System.Linq.Enumerable.Cast%2A>ve <xref:System.Linq.Enumerable.OfType%2A> genel <xref:System.Collections.IEnumerable> olmayan türler üzerinde çalışan iki Standart Sorgu Operatörü yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="99a83-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="99a83-109">Daha fazla bilgi için [LINQ Sorgu İşlemlerinde Tür İlişkileri'ne](./type-relationships-in-linq-query-operations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="99a83-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a83-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="99a83-110">Example</span></span>  
 <span data-ttu-id="99a83-111">Aşağıdaki örnekte basit bir <xref:System.Collections.ArrayList>sorgu .</span><span class="sxs-lookup"><span data-stu-id="99a83-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="99a83-112">Bu örnekte, kod <xref:System.Collections.ArrayList.Add%2A> yöntemi aradığında nesne baş harflerini kullandığını, ancak bu bir gereklilik olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="99a83-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99a83-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99a83-113">See also</span></span>

- [<span data-ttu-id="99a83-114">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="99a83-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
