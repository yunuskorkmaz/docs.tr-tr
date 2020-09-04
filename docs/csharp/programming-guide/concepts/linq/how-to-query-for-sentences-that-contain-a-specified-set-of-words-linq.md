---
title: Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)
description: Çalışma zamanında doldurulabilen her bir sözcük kümesi için eşleşmeler içeren bir metin dosyasında tümceler bulmak Için C# ' de LINQ kullanmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: daf86d6641b82fb77ca237e8a190b4f60b9dea4d
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465656"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)
Bu örnek, belirli bir sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasında Tümcelerin nasıl bulunacağını gösterir. Bu örnekte, arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir. Bu örnekte sorgu, "tarihsel olarak", "Data" ve "Integrated" sözcüklerini içeren cümleleri döndürür.  
  
## <a name="example"></a>Örnek  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 Sorgu önce metni cümlelere bölerek ve sonra cümleleri her bir sözcüğü tutan dizeler dizisine bölerek işe yarar. Bu dizilerin her biri için yöntem, <xref:System.Linq.Enumerable.Distinct%2A> tüm yinelenen sözcükleri kaldırır ve sonra sorgu, <xref:System.Linq.Enumerable.Intersect%2A> Word dizisi ve dizi üzerinde bir işlem gerçekleştirir `wordsToMatch` . Kesişimin sayısı dizinin sayısıyla aynıysa `wordsToMatch` , sözcüklerde tüm sözcükler bulunur ve özgün tümce döndürülür.  
  
 Çağrısında <xref:System.String.Split%2A> , noktalama işaretleri dizeden kaldırmak için ayırıcılar olarak kullanılır. Bunu yapmadıysanız, örneğin, dizide "tarihsel" olarak eşleşmeyen "tarihsel" bir dizeye sahip olabilirsiniz `wordsToMatch` . Kaynak metinde bulunan noktalama türlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
