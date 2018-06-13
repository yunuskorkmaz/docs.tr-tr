---
title: 'Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama'
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: 8aaf90843fa85cf20a92a40644f085769404aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323241"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="d646c-102">Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="d646c-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="d646c-103">LINQ Sorgu genel olmayan için kullanırken <xref:System.Collections.IEnumerable> gibi koleksiyonları <xref:System.Collections.ArrayList>, koleksiyon içindeki nesneler belirli türünü yansıtacak şekilde Aralık değişkeninin türü açıkça belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d646c-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="d646c-104">Örneğin, bir <xref:System.Collections.ArrayList> , `Student` nesneleri, [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md) aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d646c-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../../csharp/language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```  
var query = from Student s in arrList  
...  
```  
  
 <span data-ttu-id="d646c-105">Aralık değişkeninin türü belirterek, her öğe atama <xref:System.Collections.ArrayList> için bir `Student`.</span><span class="sxs-lookup"><span data-stu-id="d646c-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="d646c-106">Açıkça belirtilmiş aralık değişkeni bir sorgu ifadesinde kullanımı için arama eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d646c-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="d646c-107"><xref:System.Linq.Enumerable.Cast%2A> Belirtilen dönüştürme gerçekleştirilemediği takdirde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d646c-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="d646c-108"><xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan üzerinde çalışmak için iki standart sorgu işleci yöntemlerdir <xref:System.Collections.IEnumerable> türleri.</span><span class="sxs-lookup"><span data-stu-id="d646c-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="d646c-109">Daha fazla bilgi için bkz: [LINQ Sorgu işlemlerinde tür ilişkileri](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d646c-109">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d646c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d646c-110">Example</span></span>  
 <span data-ttu-id="d646c-111">Aşağıdaki örnekte basit bir sorgu üzerinden gösterir. bir <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="d646c-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="d646c-112">Bu örnek kodu çağırdığında nesne başlatıcıları kullandığına dikkat edin <xref:System.Collections.ArrayList.Add%2A> yöntemi, ancak bu zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d646c-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d646c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d646c-113">See Also</span></span>  
 [<span data-ttu-id="d646c-114">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="d646c-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
