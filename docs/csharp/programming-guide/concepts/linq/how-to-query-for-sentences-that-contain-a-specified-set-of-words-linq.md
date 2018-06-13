---
title: 'Nasıl yapılır: sözcükleri (LINQ) (C#) belirtilen bir kümesini içeren cümleleri sorgulama'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 736078ccf97ba3e61748932c3e48fb436b2c5564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319890"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Nasıl yapılır: sözcükleri (LINQ) (C#) belirtilen bir kümesini içeren cümleleri sorgulama
Bu örnek eşleşmeleri sözcüklerin belirtilen kümenin her bir metin dosyasına tümceler bulmak nasıl gösterir. Arama terimleri dizisi bu örnekte, sabit kodlanmış olsa da, bu da dinamik olarak çalışma zamanında doldurulmuş. Bu örnekte, "Tarihsel olarak," sözcüklerini cümleleri sorgunun döndürdüğü "data" ve "tümleşik."  
  
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
  
 Sorgu metni cümleleri ilk bölme ve sonra her sözcüğün tutan bir dizeler dizisi cümleleri bölme çalışır. Her bu dizi <xref:System.Linq.Enumerable.Distinct%2A> yöntemi, tüm yinelenen sözcükler kaldırır ve ardından sorguyu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> işlemi word dizisinde ve `wordsToMatch` dizi. Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulunamadı ve özgün cümle döndürülür.  
  
 Çağrısında <xref:System.String.Split%2A>, noktalama işaretlerinin ayırıcı olarak dizeden kaldırmak için kullanılır. Bu, elinizde bir dize "Geçmişte" Örneğin yapmazsanız, eşleşmiyor "Geçmişte" olarak `wordsToMatch` dizi. Kaynak metinlerinde bulunan noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
