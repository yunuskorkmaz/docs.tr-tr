---
title: 'Nasıl yapılır: Bir Sözcüğün Bir Dizede Kaç Kez Geçtiğini Sayma (LINQ)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: 07742e7e99291e056e4c91a31b2e588e36a6e177
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348193"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="137d3-102">Nasıl yapılır: dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="137d3-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="137d3-103">Bu örnek, bir dizedeki belirli bir sözcüğün tekrarlamalarını saymak için bir LINQ sorgusunun nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="137d3-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="137d3-104">Sayıyı tamamlamak için öncelikle <xref:System.String.Split%2A> yönteminin bir dizi sözcük oluşturmak için çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="137d3-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="137d3-105"><xref:System.String.Split%2A> yönteminin performans maliyeti vardır.</span><span class="sxs-lookup"><span data-stu-id="137d3-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="137d3-106">Dizedeki tek işlem kelimeleri saymaya ise bunun yerine <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemlerini kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="137d3-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="137d3-107">Ancak, performans kritik bir sorun değilse veya tümceyi zaten böldüğünüz takdirde, diğer sorgu türlerini kullanmak için tümceyi daha önce ayırdıysanız, LINQ 'ı kullanarak sözcükleri veya tümceleri de saymanız mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="137d3-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="137d3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="137d3-108">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a><span data-ttu-id="137d3-109">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="137d3-109">Compile the code</span></span>

<span data-ttu-id="137d3-110">System. Linq ad alanı için `Imports` bildirimiyle bir Visual Basic konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="137d3-110">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="137d3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="137d3-111">See also</span></span>

- [<span data-ttu-id="137d3-112">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="137d3-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
