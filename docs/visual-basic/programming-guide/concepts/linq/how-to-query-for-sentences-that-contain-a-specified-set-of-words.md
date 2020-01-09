---
title: 'Nasıl yapılır: Belirli bir Sözcükler Kümesini İçeren Cümleleri Sorgulama (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 6595932fae9737a0ac482c952b29bfde429de76f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344157"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="82e52-102">Nasıl yapılır: belirli bir sözcükler kümesini içeren cümleleri sorgulama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82e52-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="82e52-103">Bu örnek, belirli bir sözcük kümesinin her biri için eşleşmeler içeren bir metin dosyasında Tümcelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="82e52-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="82e52-104">Bu örnekte, arama terimleri dizisi sabit kodlanmış olsa da, çalışma zamanında dinamik olarak doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="82e52-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="82e52-105">Bu örnekte sorgu, "tarihsel olarak", "Data" ve "Integrated" sözcüklerini içeren cümleleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="82e52-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="82e52-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="82e52-106">Example</span></span>

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

<span data-ttu-id="82e52-107">Sorgu önce metni cümlelere bölerek ve sonra cümleleri her bir sözcüğü tutan dizeler dizisine bölerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="82e52-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="82e52-108">Bu dizilerin her biri için <xref:System.Linq.Enumerable.Distinct%2A> yöntemi tüm yinelenen sözcükleri kaldırır ve sonra sorgu, Word dizisinde ve `wordsToMatch` dizisinde bir <xref:System.Linq.Enumerable.Intersect%2A> işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="82e52-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="82e52-109">Kesişimin sayısı `wordsToMatch` dizisinin sayısıyla aynıysa, sözcüklerde tüm sözcükler bulunur ve özgün tümce döndürülür.</span><span class="sxs-lookup"><span data-stu-id="82e52-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="82e52-110"><xref:System.String.Split%2A>çağrısında noktalama işaretleri, dizeden kaldırmak için ayırıcılar olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82e52-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="82e52-111">Bunu yapmadıysanız, örneğin, `wordsToMatch` dizide "tarihsel" olarak eşleşmeyen "tarihsel" bir dizeye sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82e52-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="82e52-112">Kaynak metinde bulunan noktalama türlerine bağlı olarak ek ayırıcılar kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="82e52-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="82e52-113">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="82e52-113">Compile the code</span></span>

<span data-ttu-id="82e52-114">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82e52-114">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="82e52-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82e52-115">See also</span></span>

- [<span data-ttu-id="82e52-116">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82e52-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
