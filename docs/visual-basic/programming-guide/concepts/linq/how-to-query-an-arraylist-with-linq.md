---
title: 'Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 56533c4453129a676ed6b97e9afcc008d6ce1137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642861"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama
LINQ Sorgu genel olmayan için kullanırken <xref:System.Collections.IEnumerable> gibi koleksiyonları <xref:System.Collections.ArrayList>, koleksiyon içindeki nesneler belirli türünü yansıtacak şekilde Aralık değişkeninin türü açıkça belirtmesi gerekir. Örneğin, bir <xref:System.Collections.ArrayList> , `Student` nesneleri, [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md) aşağıdaki gibi görünmelidir:  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 Aralık değişkeninin türü belirterek, her öğe atama <xref:System.Collections.ArrayList> için bir `Student`.  
  
 Açıkça belirtilmiş aralık değişkeni bir sorgu ifadesinde kullanımı için arama eşdeğerdir <xref:System.Linq.Enumerable.Cast%2A> yöntemi. <xref:System.Linq.Enumerable.Cast%2A> Belirtilen dönüştürme gerçekleştirilemediği takdirde bir özel durum oluşturur. <xref:System.Linq.Enumerable.Cast%2A> ve <xref:System.Linq.Enumerable.OfType%2A> genel olmayan üzerinde çalışmak için iki standart sorgu işleci yöntemlerdir <xref:System.Collections.IEnumerable> türleri. Visual Basic'te açıkça çağırmalısınız <xref:System.Linq.Enumerable.Cast%2A> belirli aralık değişkeni türü emin olmak için veri kaynağında yöntemi. Daha fazla bilgi için bkz:[(Visual Basic) sorgu işlemlerinde tür ilişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte basit bir sorgu üzerinden gösterir. bir <xref:System.Collections.ArrayList>. Bu örnek kodu çağırdığında nesne başlatıcıları kullandığına dikkat edin <xref:System.Collections.ArrayList.Add%2A> yöntemi, ancak bu zorunlu değildir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
