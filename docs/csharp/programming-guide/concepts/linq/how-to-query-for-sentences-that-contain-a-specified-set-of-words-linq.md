---
title: 'Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 0c91b225527f9c6322da98e3331127652ef52df7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54747940"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)
Bu örnek, eşleşen her biri belirli bir sözcükler kümesini içeren bir metin dosyasındaki cümleler nasıl gösterir. Bu örnekte, sabit kodlanmış arama terimlerini dizi olmasına karşın, dinamik olarak çalışma zamanında doldurulduğunu. Bu örnekte, "Tarihsel olarak," sözcüklerini içeren cümleleri sorguyu döndürür "veri" ve "tümleşik."  
  
## <a name="example"></a>Örnek  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
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
  
 İlk metin cümleler bölme ve ardından her sözcüğün tutan bir dize dizisi cümleleri bölme sorgu çalışır. Her biri bu dizileri için <xref:System.Linq.Enumerable.Distinct%2A> yöntemi tüm yinelenen sözcükler kaldırır ve ardından sorgu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> sözcük dizisi işlemi ve `wordsToMatch` dizi. Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulundu ve asıl cümlenin döndürülür.  
  
 Çağrısında <xref:System.String.Split%2A>, noktalama işaretleri, ayırıcısı olarak bunları dizeden kaldırmak için kullanılır. Sahip olduğunuz bir dize "Daha önce" örneği için bunu değil ise, değil eşleşir "Daha önce" içinde `wordsToMatch` dizisi. Kaynak metni bulundu noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
