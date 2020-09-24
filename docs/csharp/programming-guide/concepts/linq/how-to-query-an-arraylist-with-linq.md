---
title: LINQ ile ArrayList 'i sorgulama (C#)
description: Bu örnek, C# ' de bir ArrayList üzerinde sorgu yapmak için LINQ kullanır. Koleksiyondaki nesnelerin türünü yansıtmak için Aralık değişkeninin türünü bildirmeniz gerekir.
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 278c05cfc864ee4f53e1215a2acb739efd87f8b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154008"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="c7d32-104">LINQ ile ArrayList 'i sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="c7d32-104">How to query an ArrayList with LINQ (C#)</span></span>

<span data-ttu-id="c7d32-105">Gibi genel olmayan koleksiyonları sorgulamak için LINQ kullanılırken <xref:System.Collections.IEnumerable> <xref:System.Collections.ArrayList> , koleksiyondaki nesne türlerini yansıtmak için Aralık değişkeninin türünü açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7d32-105">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="c7d32-106">Örneğin, bir <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa, [from yan tümcesi](../../../language-reference/keywords/from-clause.md) şuna benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="c7d32-106">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="c7d32-107">Aralık değişkeninin türünü belirterek, içindeki her bir öğeyi öğesine vurarak <xref:System.Collections.ArrayList> `Student` .</span><span class="sxs-lookup"><span data-stu-id="c7d32-107">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="c7d32-108">Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması yöntemi çağırma ile eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> .</span><span class="sxs-lookup"><span data-stu-id="c7d32-108">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="c7d32-109"><xref:System.Linq.Enumerable.Cast%2A> Belirtilen tür dönüştürme gerçekleştirilemiyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7d32-109"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="c7d32-110"><xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan türlerde çalışan Iki standart sorgu işleci yöntemi vardır <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="c7d32-110"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="c7d32-111">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c7d32-111">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7d32-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7d32-112">Example</span></span>  

 <span data-ttu-id="c7d32-113">Aşağıdaki örnek, üzerinde basit bir sorgu gösterir <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="c7d32-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c7d32-114">Bu örnekte kod yöntemi çağırdığında nesne başlatıcılarının kullanıldığı <xref:System.Collections.ArrayList.Add%2A> , ancak bu bir gereksinim olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d32-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7d32-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7d32-115">See also</span></span>

- [<span data-ttu-id="c7d32-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="c7d32-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
