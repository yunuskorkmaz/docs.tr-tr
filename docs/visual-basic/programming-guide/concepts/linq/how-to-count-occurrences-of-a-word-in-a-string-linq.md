---
title: 'Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) (Visual Basic) oluşum sayısı'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820327"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="07c10-102">Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) (Visual Basic) oluşum sayısı</span><span class="sxs-lookup"><span data-stu-id="07c10-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="07c10-103">Bu örnek belirtilen bir sözcüğün bir dizede oluşumları saymak için LINQ sorgusu kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="07c10-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="07c10-104">Sayım gerçekleştirmeye unutmayın <xref:System.String.Split%2A> yöntemi bir kelimelerin dizi oluşturmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="07c10-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="07c10-105">Bir performans maliyetine yoktur <xref:System.String.Split%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07c10-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="07c10-106">Sözcükleri saymak için dize yalnızca işlemi ise kullanmayı düşünmelisiniz <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemleri yerine.</span><span class="sxs-lookup"><span data-stu-id="07c10-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="07c10-107">Ancak, performans kritik bir sorunu değil ya da diğer sorgu türleri üzerinde gerçekleştirmek için önceden cümle ayırdıktan sonra sözcükler veya tümcecikler de saymak için LINQ kullanma mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="07c10-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c10-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="07c10-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="07c10-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="07c10-109">Compiling the Code</span></span>  
 <span data-ttu-id="07c10-110">.NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="07c10-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c10-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07c10-111">See also</span></span>

- [<span data-ttu-id="07c10-112">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07c10-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
