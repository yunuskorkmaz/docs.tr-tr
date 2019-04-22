---
title: 'Nasıl yapılır: (Visual Basic) LINQ ile ArrayList sorgulama'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: ed440a7970d0ef1a49af36fa56b1c7ca74715e5f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837162"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="dd579-102">Nasıl yapılır: (Visual Basic) LINQ ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="dd579-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="dd579-103">LINQ Sorgu genel olmayan için kullanırken <xref:System.Collections.IEnumerable> koleksiyonlar gibi <xref:System.Collections.ArrayList>, koleksiyon içindeki nesneler belirli türünü yansıtacak şekilde Aralık değişkeninin türünü açıkça belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd579-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="dd579-104">Örneğin, bir <xref:System.Collections.ArrayList> , `Student` nesneleri, [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md) şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="dd579-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="dd579-105">Aralık değişkeninin türünü belirterek, her öğe atama <xref:System.Collections.ArrayList> için bir `Student`.</span><span class="sxs-lookup"><span data-stu-id="dd579-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="dd579-106">Bir açık olarak aralık değişkeni bir sorgu ifadesinde kullanımını çağırmakla eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd579-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="dd579-107"><xref:System.Linq.Enumerable.Cast%2A> Belirtilen dönüştürme gerçekleştirilemediği takdirde, özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd579-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="dd579-108"><xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan üzerinde çalışan iki standart sorgu işleci yöntemleri <xref:System.Collections.IEnumerable> türleri.</span><span class="sxs-lookup"><span data-stu-id="dd579-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="dd579-109">Visual Basic'te açıkça çağırmalısınız <xref:System.Linq.Enumerable.Cast%2A> veri kaynağındaki belirli bir aralık değişkeni türü emin olmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd579-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="dd579-110">Daha fazla bilgi için [(Visual Basic) sorgu işlemlerinde tür ilişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="dd579-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd579-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd579-111">Example</span></span>  
 <span data-ttu-id="dd579-112">Aşağıdaki örnek, üzerinden basit bir sorguyu gösterir. bir <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="dd579-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="dd579-113">Bu örnek kodu çağırdığında nesne başlatıcıları kullanır Not <xref:System.Collections.ArrayList.Add%2A> yöntemi, ancak bu zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="dd579-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd579-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd579-114">See also</span></span>

- [<span data-ttu-id="dd579-115">LINQ to Objects'in (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd579-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
