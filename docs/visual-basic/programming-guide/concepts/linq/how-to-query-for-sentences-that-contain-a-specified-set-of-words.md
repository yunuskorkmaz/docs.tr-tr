---
title: "Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 523b1e681c97e14f1d0e49b82a426b0e0e54fa1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="23ca1-102">Nasıl yapılır: sözcükleri (LINQ) (Visual Basic) belirtilen bir kümesini içeren cümleleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="23ca1-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="23ca1-103">Bu örnek eşleşmeleri sözcüklerin belirtilen kümenin her bir metin dosyasına tümceler bulmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="23ca1-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="23ca1-104">Arama terimleri dizisi bu örnekte, sabit kodlanmış olsa da, bu da dinamik olarak çalışma zamanında doldurulmuş.</span><span class="sxs-lookup"><span data-stu-id="23ca1-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="23ca1-105">Bu örnekte, "Tarihsel olarak," sözcüklerini cümleleri sorgunun döndürdüğü "data" ve "tümleşik."</span><span class="sxs-lookup"><span data-stu-id="23ca1-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ca1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="23ca1-106">Example</span></span>  
  
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
  
 <span data-ttu-id="23ca1-107">Sorgu metni cümleleri ilk bölme ve sonra her sözcüğün tutan bir dizeler dizisi cümleleri bölme çalışır.</span><span class="sxs-lookup"><span data-stu-id="23ca1-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="23ca1-108">Her bu dizi <xref:System.Linq.Enumerable.Distinct%2A> yöntemi, tüm yinelenen sözcükler kaldırır ve ardından sorguyu gerçekleştiren bir <xref:System.Linq.Enumerable.Intersect%2A> işlemi word dizisinde ve `wordsToMatch` dizi.</span><span class="sxs-lookup"><span data-stu-id="23ca1-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="23ca1-109">Kesişimi sayısı sayısı ile aynı olup olmadığını `wordsToMatch` dizinin tüm sözcükleri sözcükleri bulunamadı ve özgün cümle döndürülür.</span><span class="sxs-lookup"><span data-stu-id="23ca1-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="23ca1-110">Çağrısında <xref:System.String.Split%2A>, noktalama işaretlerinin ayırıcı olarak dizeden kaldırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23ca1-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="23ca1-111">Bu, elinizde bir dize "Geçmişte" Örneğin yapmazsanız, eşleşmiyor "Geçmişte" olarak `wordsToMatch` dizi.</span><span class="sxs-lookup"><span data-stu-id="23ca1-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="23ca1-112">Kaynak metinlerinde bulunan noktalama türlerine bağlı olarak ek ayırıcıları kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="23ca1-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23ca1-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="23ca1-113">Compiling the Code</span></span>  
 <span data-ttu-id="23ca1-114">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="23ca1-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ca1-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23ca1-115">See Also</span></span>  
 [<span data-ttu-id="23ca1-116">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23ca1-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
