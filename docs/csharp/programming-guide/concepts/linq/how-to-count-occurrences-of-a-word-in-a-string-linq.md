---
title: Bir dizedeki bir sözcüğün oluşumları nasıl sayilir (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 9c3ac2e0d44d52e437586a4d105a022f75c1dc54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169331"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="39a6f-102">Bir dizedeki bir sözcüğün oluşumları nasıl sayilir (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="39a6f-102">How to count occurrences of a word in a string (LINQ) (C#)</span></span>
<span data-ttu-id="39a6f-103">Bu örnek, bir dize de belirtilen bir sözcüğün oluşumları saymak için linq sorgusu nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39a6f-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="39a6f-104">Sayımı gerçekleştirmek için önce <xref:System.String.Split%2A> bir sözcük dizisi oluşturmak için yöntemin çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39a6f-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="39a6f-105">Yöntemin <xref:System.String.Split%2A> bir performans maliyeti vardır.</span><span class="sxs-lookup"><span data-stu-id="39a6f-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="39a6f-106">Dizedeki tek işlem sözcükleri saymaksa, bunun <xref:System.Text.RegularExpressions.Regex.Matches%2A> <xref:System.String.IndexOf%2A> yerine yöntemleri kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="39a6f-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="39a6f-107">Ancak, performans kritik bir sorun değilse veya üzerinde başka tür de sorguları gerçekleştirmek için cümleyi zaten böldüyseniz, sözcükleri veya tümcecikleri de saymak için LINQ'yi kullanmak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="39a6f-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39a6f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="39a6f-108">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="39a6f-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="39a6f-109">Compiling the Code</span></span>  
 <span data-ttu-id="39a6f-110">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="39a6f-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a6f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39a6f-111">See also</span></span>

- [<span data-ttu-id="39a6f-112">LINQ ve Dizeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="39a6f-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
