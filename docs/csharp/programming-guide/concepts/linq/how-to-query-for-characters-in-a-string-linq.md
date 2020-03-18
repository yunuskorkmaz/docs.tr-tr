---
title: Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345675"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="9d383-102">Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="9d383-102">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="9d383-103"><xref:System.String> Sınıf genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi uyguladığından, herhangi bir dize bir karakter dizisi olarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="9d383-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="9d383-104">Ancak, bu LINQ yaygın bir kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="9d383-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="9d383-105">Karmaşık desen eşleştirme işlemleri <xref:System.Text.RegularExpressions.Regex> için sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d383-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d383-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d383-106">Example</span></span>  
 <span data-ttu-id="9d383-107">Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemek için bir dize sorgular.</span><span class="sxs-lookup"><span data-stu-id="9d383-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="9d383-108">Sorgunun ilk kez yürütüldükten sonra "yeniden kullanıldığını" unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d383-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="9d383-109">Sorgunun kendisi herhangi bir gerçek sonuç depolamaz, çünkü bu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9d383-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d383-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9d383-110">Compiling the Code</span></span>  
 <span data-ttu-id="9d383-111">System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d383-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d383-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d383-112">See also</span></span>

- [<span data-ttu-id="9d383-113">LINQ ve Dizeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9d383-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="9d383-114">LINQ sorgularını normal ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="9d383-114">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
