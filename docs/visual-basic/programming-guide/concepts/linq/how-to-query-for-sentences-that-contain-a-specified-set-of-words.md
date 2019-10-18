---
title: 'Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 81863706afc4f09abf114d7efbaaa02b1ee56084
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524138"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)

Bu örnek, belirli bir sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasında Tümcelerin nasıl bulunacağını gösterir. Bu örnekte, arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir. Bu örnekte sorgu, "tarihsel olarak", "Data" ve "Integrated" sözcüklerini içeren cümleleri döndürür.

## <a name="example"></a>Örnek

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

Sorgu önce metni cümlelere bölerek ve sonra cümleleri her bir sözcüğü tutan dizeler dizisine bölerek işe yarar. Bu dizilerin her biri için <xref:System.Linq.Enumerable.Distinct%2A> yöntemi tüm yinelenen sözcükleri kaldırır ve sonra sorgu, Word dizisinde ve `wordsToMatch` dizisinde bir <xref:System.Linq.Enumerable.Intersect%2A> işlemi gerçekleştirir. Kesişimin sayısı `wordsToMatch` dizisinin sayısıyla aynıysa, sözcüklerde tüm sözcükler bulunur ve özgün tümce döndürülür.

@No__t_0 çağrısında noktalama işaretleri, dizeden kaldırmak için ayırıcılar olarak kullanılır. Bunu yapmadıysanız, örneğin, `wordsToMatch` dizide "tarihsel" olarak eşleşmeyen "tarihsel" bir dizeye sahip olabilirsiniz. Kaynak metinde bulunan noktalama türlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.

## <a name="compiling-the-code"></a>Kod Derleniyor

System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
