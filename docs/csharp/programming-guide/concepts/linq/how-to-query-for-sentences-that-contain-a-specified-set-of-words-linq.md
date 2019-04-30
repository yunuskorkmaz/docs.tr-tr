---
title: 'Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)'
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 0c91b225527f9c6322da98e3331127652ef52df7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667846"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="94e3b-102">Nasıl yapılır: Belirli bir sözcükler (LINQ) kümesini içeren cümleleri sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="94e3b-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>
<span data-ttu-id="94e3b-103">Bu örnek, eşleşen her biri belirli bir sözcükler kümesini içeren bir metin dosyasındaki cümleler nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="94e3b-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="94e3b-104">Bu örnekte, sabit kodlanmış arama terimlerini dizi olmasına karşın, dinamik olarak çalışma zamanında doldurulduğunu.</span><span class="sxs-lookup"><span data-stu-id="94e3b-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="94e3b-105">Bu örnekte, "Tarihsel olarak," sözcüklerini içeren cümleleri sorguyu döndürür "veri" ve "tümleşik."</span><span class="sxs-lookup"><span data-stu-id="94e3b-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="94e3b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="94e3b-106">Example</span></span>  
  
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
  
 <span data-ttu-id="94e3b-107">İlk metin cümleler bölme ve ardından her sözcüğün tutan bir dize dizisi cümleleri bölme sorgu çalışır.</span><span class="sxs-lookup"><span data-stu-id="94e3b-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="94e3b-108">Her biri bu dizileri için <xref:System.Linq.Enumerable.Distinct%2A> yöntemi tüm yinelenen sözcükler kaldırır ve ardından sorgu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> sözcük dizisi işlemi ve `wordsToMatch` dizi.</span><span class="sxs-lookup"><span data-stu-id="94e3b-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="94e3b-109">Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulundu ve asıl cümlenin döndürülür.</span><span class="sxs-lookup"><span data-stu-id="94e3b-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="94e3b-110">Çağrısında <xref:System.String.Split%2A>, noktalama işaretleri, ayırıcısı olarak bunları dizeden kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94e3b-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="94e3b-111">Sahip olduğunuz bir dize "Daha önce" örneği için bunu değil ise, değil eşleşir "Daha önce" içinde `wordsToMatch` dizisi.</span><span class="sxs-lookup"><span data-stu-id="94e3b-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="94e3b-112">Kaynak metni bulundu noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="94e3b-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94e3b-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="94e3b-113">Compiling the Code</span></span>  
 <span data-ttu-id="94e3b-114">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="94e3b-114">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e3b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94e3b-115">See also</span></span>

- [<span data-ttu-id="94e3b-116">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="94e3b-116">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
