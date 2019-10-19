---
title: 'Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: f2102a8cb149fa9c7886826e509bf254fad5eb95
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582719"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (Visual Basic)

@No__t_0 sınıfı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini gerçekleştirdiğinden, herhangi bir dize bir karakter dizisi olarak sorgulanabilir. Ancak bu, LINQ 'in yaygın bir kullanımı değildir. Karmaşık kalıp eşleştirme işlemleri için <xref:System.Text.RegularExpressions.Regex> sınıfını kullanın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemede bir dizeyi sorgular. Sorgunun ilk kez yürütüldükten sonra "yeniden kullanılır" olduğunu unutmayın. Sorgunun kendisi gerçek sonuçları depolamadığından bu mümkündür.

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

System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Nasıl yapılır: LINQ sorgularını normal Ifadelerle birleştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
