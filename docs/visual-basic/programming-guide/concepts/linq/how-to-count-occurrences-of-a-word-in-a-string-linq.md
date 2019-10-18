---
title: 'Nasıl yapılır: dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: 3a2ae52a3380e4a0d8df4adb580e84362e3f13f3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524170"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Nasıl yapılır: dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (Visual Basic)

Bu örnek, bir dizedeki belirli bir sözcüğün tekrarlamalarını saymak için bir LINQ sorgusunun nasıl kullanılacağını gösterir. Sayıyı tamamlamak için öncelikle <xref:System.String.Split%2A> yönteminin bir dizi sözcük oluşturmak için çağrıldığını unutmayın. @No__t_0 yönteminin performans maliyeti vardır. Dizedeki tek işlem kelimeleri saymaya ise bunun yerine <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemlerini kullanmayı düşünmelisiniz. Ancak, performans kritik bir sorun değilse veya tümceyi zaten böldüğünüz takdirde, diğer sorgu türlerini kullanmak için tümceyi daha önce ayırdıysanız, LINQ 'ı kullanarak sözcükleri veya tümceleri de saymanız mantıklıdır.

## <a name="example"></a>Örnek

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compiling-the-code"></a>Kod Derleniyor

System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
