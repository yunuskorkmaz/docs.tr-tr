---
title: 'Nasıl yapılır: (LINQ) (Visual Basic) bir dizedeki karakterleri sorgulama'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: fba5d8ca6c0c060c76b1ecf4f66434ce0884e733
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593310"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Nasıl yapılır: (LINQ) (Visual Basic) bir dizedeki karakterleri sorgulama
Çünkü <xref:System.String> sınıfın uyguladığı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, bir karakter dizisi herhangi bir dize sorgulanabilir. Ancak, bu yaygın bir LINQ kullanımı değildir. İşlem eşleştirme karmaşık deseni için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dize içerdiği sayısal basamak sayısını belirlemek için sorgular. "İlk kez yürütüldükten sonra sorguyu yeniden," unutmayın. Herhangi bir gerçek sonuç sorgunun kendisi depolamaz mümkün olmasıdır.  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
VB.NET konsol uygulama projesi oluşturmak bir `Imports` System.Linq ad alanı bildirimi.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Nasıl yapılır: (Visual Basic) Normal ifadelerle LINQ sorgularını birleştirme](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
