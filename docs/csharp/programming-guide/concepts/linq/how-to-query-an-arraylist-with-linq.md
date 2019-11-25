---
title: "Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama"
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: c22cd6ef22b5ca182266c1e8db10151e07567fc6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969819"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="d3bbb-102">Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama</span><span class="sxs-lookup"><span data-stu-id="d3bbb-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="d3bbb-103">LINQ to <xref:System.Collections.ArrayList> gibi genel olmayan <xref:System.Collections.IEnumerable> koleksiyonlarını sorgulamak için kullandığınızda, koleksiyondaki nesne türlerini yansıtacak şekilde Aralık değişkeninin türünü açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="d3bbb-104">Örneğin, `Student` nesneleri <xref:System.Collections.ArrayList> varsa, [from yan tümcesinden](../../../language-reference/keywords/from-clause.md) aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d3bbb-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="d3bbb-105">Aralık değişkeninin türünü belirterek, <xref:System.Collections.ArrayList> ' daki her öğeyi bir `Student` ' e dönüştürmektir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="d3bbb-106">Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması <xref:System.Linq.Enumerable.Cast%2A> yöntemini çağırmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="d3bbb-107">Belirtilen tür dönüştürme gerçekleştirilemiyorsa <xref:System.Linq.Enumerable.Cast%2A> bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="d3bbb-108"><xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A>, genel olmayan <xref:System.Collections.IEnumerable> türlerinde çalışan iki standart sorgu Işleci yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="d3bbb-109">Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d3bbb-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3bbb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3bbb-110">Example</span></span>  
 <span data-ttu-id="d3bbb-111">Aşağıdaki örnek, <xref:System.Collections.ArrayList> üzerinde basit bir sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="d3bbb-112">Bu örnek, kod <xref:System.Collections.ArrayList.Add%2A> yöntemini çağırdığında nesne başlatıcıları kullanır, ancak bu bir gereklilik değildir.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3bbb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3bbb-113">See also</span></span>

- [<span data-ttu-id="d3bbb-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="d3bbb-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
