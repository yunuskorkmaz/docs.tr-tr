---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)"
title: 'Nasıl yapılır: LINQ ile ArrayList Sorgulama'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: df7c6e1cee6d8e37074ce209f3bea97a402d8dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428525"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="f85e3-103">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f85e3-103">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="f85e3-104">Gibi genel olmayan koleksiyonları sorgulamak için LINQ kullanılırken <xref:System.Collections.IEnumerable> <xref:System.Collections.ArrayList> , koleksiyondaki nesne türlerini yansıtmak için Aralık değişkeninin türünü açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f85e3-104">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="f85e3-105">Örneğin, bir <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa, [from yan tümcesi](../../../language-reference/queries/from-clause.md) şuna benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="f85e3-105">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="f85e3-106">Aralık değişkeninin türünü belirterek, içindeki her bir öğeyi öğesine vurarak <xref:System.Collections.ArrayList> `Student` .</span><span class="sxs-lookup"><span data-stu-id="f85e3-106">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="f85e3-107">Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması yöntemi çağırma ile eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> .</span><span class="sxs-lookup"><span data-stu-id="f85e3-107">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="f85e3-108"><xref:System.Linq.Enumerable.Cast%2A> Belirtilen tür dönüştürme gerçekleştirilemiyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f85e3-108"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="f85e3-109"><xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan türlerde çalışan Iki standart sorgu işleci yöntemi vardır <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="f85e3-109"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="f85e3-110">Visual Basic, <xref:System.Linq.Enumerable.Cast%2A> belirli bir Aralık değişkeni türü sağlamak için veri kaynağındaki yöntemi açıkça çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f85e3-110">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="f85e3-111">Daha fazla bilgi için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f85e3-111">For more information, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="f85e3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f85e3-112">Example</span></span>

<span data-ttu-id="f85e3-113">Aşağıdaki örnek, üzerinde basit bir sorgu gösterir <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="f85e3-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f85e3-114">Bu örnekte kod yöntemi çağırdığında nesne başlatıcılarının kullanıldığı <xref:System.Collections.ArrayList.Add%2A> , ancak bu bir gereksinim olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f85e3-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f85e3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f85e3-115">See also</span></span>

- [<span data-ttu-id="f85e3-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f85e3-116">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
