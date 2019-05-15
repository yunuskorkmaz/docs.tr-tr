---
title: 'Nasıl yapılır: (LINQ) bir dizedeki karakterleri sorgulama (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: b31dfb4c9fb7f7efc439a1703f13aafca3053e6a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584447"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="1bea9-102">Nasıl yapılır: (LINQ) bir dizedeki karakterleri sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="1bea9-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="1bea9-103">Çünkü <xref:System.String> sınıfın uyguladığı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, bir karakter dizisi herhangi bir dize sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1bea9-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="1bea9-104">Ancak, bu yaygın bir LINQ kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="1bea9-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="1bea9-105">İşlem eşleştirme karmaşık deseni için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1bea9-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bea9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bea9-106">Example</span></span>  
 <span data-ttu-id="1bea9-107">Aşağıdaki örnek, bir dize içerdiği sayısal basamak sayısını belirlemek için sorgular.</span><span class="sxs-lookup"><span data-stu-id="1bea9-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="1bea9-108">"İlk kez yürütüldükten sonra sorguyu yeniden," unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1bea9-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="1bea9-109">Herhangi bir gerçek sonuç sorgunun kendisi depolamaz mümkün olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1bea9-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bea9-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1bea9-110">Compiling the Code</span></span>  
 <span data-ttu-id="1bea9-111">Oluşturma bir C# konsol uygulama projesi ile `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="1bea9-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bea9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bea9-112">See also</span></span>

- [<span data-ttu-id="1bea9-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="1bea9-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="1bea9-114">Nasıl yapılır: Normal ifadelerle LINQ sorgularını birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="1bea9-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
