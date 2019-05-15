---
title: 'Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) geçtiğini sayma (C#)'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 5855250661f5288203ae0be841bcfb3a49f8369a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585817"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="768f2-102">Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) geçtiğini sayma (C#)</span><span class="sxs-lookup"><span data-stu-id="768f2-102">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>
<span data-ttu-id="768f2-103">Bu örnek belirtilen bir sözcüğün bir dizede oluşumları saymak için LINQ sorgusu kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="768f2-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="768f2-104">Sayım gerçekleştirmeye unutmayın <xref:System.String.Split%2A> yöntemi bir kelimelerin dizi oluşturmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="768f2-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="768f2-105">Bir performans maliyetine yoktur <xref:System.String.Split%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="768f2-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="768f2-106">Sözcükleri saymak için dize yalnızca işlemi ise kullanmayı düşünmelisiniz <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemleri yerine.</span><span class="sxs-lookup"><span data-stu-id="768f2-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="768f2-107">Ancak, performans kritik bir sorunu değil ya da diğer sorgu türleri üzerinde gerçekleştirmek için önceden cümle ayırdıktan sonra sözcükler veya tümcecikler de saymak için LINQ kullanma mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="768f2-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="768f2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="768f2-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="768f2-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="768f2-109">Compiling the Code</span></span>  
 <span data-ttu-id="768f2-110">Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="768f2-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768f2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="768f2-111">See also</span></span>

- [<span data-ttu-id="768f2-112">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="768f2-112">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
