---
title: 'Nasıl yapılır: LINQ ile ArrayList Sorgulama'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: b7b75e017fb314b5e5998b743dbf922f34fd9b7c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396473"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)

Gibi genel olmayan koleksiyonları sorgulamak için LINQ kullanılırken <xref:System.Collections.IEnumerable> <xref:System.Collections.ArrayList> , koleksiyondaki nesne türlerini yansıtmak için Aralık değişkeninin türünü açıkça bildirmeniz gerekir. Örneğin, bir <xref:System.Collections.ArrayList> `Student` nesneleriniz varsa, [from yan tümcesi](../../../language-reference/queries/from-clause.md) şuna benzemelidir:

```vb
Dim query = From student As Student In arrList
'...
```

Aralık değişkeninin türünü belirterek, içindeki her bir öğeyi öğesine vurarak <xref:System.Collections.ArrayList> `Student` .

Bir sorgu ifadesinde açıkça yazılmış bir aralık değişkeninin kullanılması yöntemi çağırma ile eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> . <xref:System.Linq.Enumerable.Cast%2A>Belirtilen tür dönüştürme gerçekleştirilemiyorsa bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A>ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan türlerde çalışan Iki standart sorgu işleci yöntemi vardır <xref:System.Collections.IEnumerable> . Visual Basic, <xref:System.Linq.Enumerable.Cast%2A> belirli bir Aralık değişkeni türü sağlamak için veri kaynağındaki yöntemi açıkça çağırmanız gerekir. Daha fazla bilgi için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](type-relationships-in-query-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, üzerinde basit bir sorgu gösterir <xref:System.Collections.ArrayList> . Bu örnekte kod yöntemi çağırdığında nesne başlatıcılarının kullanıldığı <xref:System.Collections.ArrayList.Add%2A> , ancak bu bir gereksinim olmadığı unutulmamalıdır.

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

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
