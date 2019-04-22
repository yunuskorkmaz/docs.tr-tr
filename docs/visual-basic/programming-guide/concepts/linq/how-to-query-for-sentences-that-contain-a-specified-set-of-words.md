---
title: 'Nasıl yapılır: Belirli bir sözcükler (LINQ) (Visual Basic) kümesini içeren cümleleri sorgulama'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 9e48d44a1cd27b63d4bb5e34eb1e554a7b4a19b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839658"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Nasıl yapılır: Belirli bir sözcükler (LINQ) (Visual Basic) kümesini içeren cümleleri sorgulama
Bu örnek, eşleşen her biri belirli bir sözcükler kümesini içeren bir metin dosyasındaki cümleler nasıl gösterir. Bu örnekte, sabit kodlanmış arama terimlerini dizi olmasına karşın, dinamik olarak çalışma zamanında doldurulduğunu. Bu örnekte, "Tarihsel olarak," sözcüklerini içeren cümleleri sorguyu döndürür "veri" ve "tümleşik."  
  
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
  
 İlk metin cümleler bölme ve ardından her sözcüğün tutan bir dize dizisi cümleleri bölme sorgu çalışır. Her biri bu dizileri için <xref:System.Linq.Enumerable.Distinct%2A> yöntemi tüm yinelenen sözcükler kaldırır ve ardından sorgu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> sözcük dizisi işlemi ve `wordsToMatch` dizi. Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulundu ve asıl cümlenin döndürülür.  
  
 Çağrısında <xref:System.String.Split%2A>, noktalama işaretleri, ayırıcısı olarak bunları dizeden kaldırmak için kullanılır. Sahip olduğunuz bir dize "Daha önce" örneği için bunu değil ise, değil eşleşir "Daha önce" içinde `wordsToMatch` dizisi. Kaynak metni bulundu noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
