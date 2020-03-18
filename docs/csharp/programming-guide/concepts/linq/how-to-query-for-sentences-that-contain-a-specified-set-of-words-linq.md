---
title: Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: df279f57d9965d796397cbcf7a0f3ba05bf9e5c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168862"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama
Bu örnek, belirtilen sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasındaki cümlelerin nasıl bulunup bulunulacağı gösterilmektedir. Bu örnekte arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir. Bu örnekte, sorgu "Geçmiş", "veri" ve "tümleşik" sözcüklerini içeren tümceleri döndürür.  
  
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
  
 Sorgu, önce metni cümlelere bölerek, sonra da cümleleri her sözcüğü tutan bir dizi dizeye bölerek çalışır. Bu dizilerin her biri <xref:System.Linq.Enumerable.Distinct%2A> için yöntem tüm yinelenen sözcükleri kaldırır <xref:System.Linq.Enumerable.Intersect%2A> ve sorgu sözcük `wordsToMatch` dizisi ve dizi üzerinde bir işlem gerçekleştirir. Kesişim sayısı `wordsToMatch` dizinin sayısıyla aynıysa, tüm sözcükler sözcüklerde bulunur ve özgün tümce döndürülür.  
  
 Çağrıda <xref:System.String.Split%2A>noktalama işaretleri, dizeden kaldırmak için ayırıcı olarak kullanılır. Bunu yapmadıysanız, örneğin `wordsToMatch` dizideki "Tarihsel" dizesini "Tarihsel olarak" eşleştirmez. Kaynak metinde bulunan noktalama işaretleritürlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
