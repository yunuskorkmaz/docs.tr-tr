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
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="87990-102">Nasıl yapılır: sözcükleri (LINQ) (C#) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="87990-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>
<span data-ttu-id="87990-103">Bu örnek eşleşmeleri sözcüklerin belirtilen kümenin her bir metin dosyasına tümceler bulmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="87990-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="87990-104">Arama terimleri dizisi bu örnekte, sabit kodlanmış olsa da, bu da dinamik olarak çalışma zamanında doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="87990-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="87990-105">Bu örnekte, "Tarihsel olarak," sözcüklerini cümleleri sorgunun döndürdüğü "data" ve "tümleşik."</span><span class="sxs-lookup"><span data-stu-id="87990-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="87990-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="87990-106">Example</span></span>  
  
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
  
 <span data-ttu-id="87990-107">Sorgu metni cümleleri ilk bölme ve sonra her sözcüğün tutan bir dizeler dizisi cümleleri bölme çalışır.</span><span class="sxs-lookup"><span data-stu-id="87990-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="87990-108">Her bu dizi <xref:System.Linq.Enumerable.Distinct%2A> yöntemi, tüm yinelenen sözcükler kaldırır ve ardından sorguyu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> işlemi word dizisinde ve `wordsToMatch` dizi.</span><span class="sxs-lookup"><span data-stu-id="87990-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="87990-109">Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulunamadı ve özgün cümle döndürülür.</span><span class="sxs-lookup"><span data-stu-id="87990-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="87990-110">Çağrısında <xref:System.String.Split%2A>, noktalama işaretlerinin ayırıcı olarak dizeden kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87990-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="87990-111">Bu, elinizde bir dize "Geçmişte" Örneğin yapmazsanız, eşleşmiyor "Geçmişte" olarak `wordsToMatch` dizi.</span><span class="sxs-lookup"><span data-stu-id="87990-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="87990-112">Kaynak metinlerinde bulunan noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="87990-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87990-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="87990-113">Compiling the Code</span></span>  
 <span data-ttu-id="87990-114">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="87990-114">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87990-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87990-115">See Also</span></span>  
 [<span data-ttu-id="87990-116">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="87990-116">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
