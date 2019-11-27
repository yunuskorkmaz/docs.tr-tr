---
title: 'Nasıl yapılır: Bir Dizedeki Karakterleri Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 9da6d5abd6155a7af5ec59e17693e8acae7e7b73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347716"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Nasıl yapılır: bir dizedeki karakterleri sorgulama (LINQ) (Visual Basic)

<xref:System.String> sınıfı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini gerçekleştirdiğinden, herhangi bir dize bir karakter dizisi olarak sorgulanabilir. Ancak bu, LINQ 'in yaygın bir kullanımı değildir. Karmaşık kalıp eşleştirme işlemleri için <xref:System.Text.RegularExpressions.Regex> sınıfını kullanın.

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

## <a name="compiling-the-code"></a>Kod Derleme

System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
- [LINQ sorgularını normal ifadelerle birleştirme (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)
