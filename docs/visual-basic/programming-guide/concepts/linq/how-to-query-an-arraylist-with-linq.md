---
title: "Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 5b05fa2ed5c9b3b701571ef4760600caac7193d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524154"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)

LINQ to <xref:System.Collections.ArrayList> gibi genel olmayan <xref:System.Collections.IEnumerable> koleksiyonlarını sorgulamak için kullandığınızda, koleksiyondaki nesne türlerini yansıtacak şekilde Aralık değişkeninin türünü açıkça bildirmeniz gerekir. Örneğin, <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa [from yan tümcesinden](../../../../visual-basic/language-reference/queries/from-clause.md) aşağıdaki gibi görünmelidir:

```vb
Dim query = From student As Student In arrList
'...
```

Aralık değişkeninin türünü belirterek, <xref:System.Collections.ArrayList> ' daki her öğeyi bir `Student` ' e dönüştürmektir.

Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması <xref:System.Linq.Enumerable.Cast%2A> yöntemini çağırmaya eşdeğerdir. Belirtilen tür dönüştürme gerçekleştirilemiyorsa <xref:System.Linq.Enumerable.Cast%2A> bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A>, genel olmayan <xref:System.Collections.IEnumerable> türlerinde çalışan iki standart sorgu Işleci yöntemleridir. Visual Basic, belirli bir Aralık değişkeni türünü sağlamak için veri kaynağındaki <xref:System.Linq.Enumerable.Cast%2A> yöntemini açıkça çağırmanız gerekir. Daha fazla bilgi için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Collections.ArrayList> üzerinde basit bir sorgu gösterir. Bu örnek, kod <xref:System.Collections.ArrayList.Add%2A> yöntemini çağırdığında nesne başlatıcıları kullanır, ancak bu bir gereklilik değildir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
