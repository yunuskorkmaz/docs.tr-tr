---
title: 'Nasıl yapılır: Dizedeki karakterleri sorgulama (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 1212ebcf264aab756eca1acb81ae617c2218a065
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592883"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="4656a-102">Nasıl yapılır: Dizedeki karakterleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4656a-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="4656a-103"><xref:System.String> Sınıfı genel<xref:System.Collections.Generic.IEnumerable%601> arabirimi uyguladığından, herhangi bir dize bir karakter dizisi olarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4656a-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="4656a-104">Ancak bu, LINQ 'in yaygın bir kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="4656a-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="4656a-105">Karmaşık kalıp eşleştirme işlemleri için <xref:System.Text.RegularExpressions.Regex> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4656a-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4656a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4656a-106">Example</span></span>  
 <span data-ttu-id="4656a-107">Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemede bir dizeyi sorgular.</span><span class="sxs-lookup"><span data-stu-id="4656a-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="4656a-108">Sorgunun ilk kez yürütüldükten sonra "yeniden kullanılır" olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4656a-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="4656a-109">Sorgunun kendisi gerçek sonuçları depolamadığından bu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4656a-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4656a-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4656a-110">Compiling the Code</span></span>  
 <span data-ttu-id="4656a-111">System. C# LINQ ve System.IO ad alanları `using` için yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4656a-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4656a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4656a-112">See also</span></span>

- [<span data-ttu-id="4656a-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="4656a-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="4656a-114">Nasıl yapılır: LINQ sorgularını normal Ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="4656a-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
