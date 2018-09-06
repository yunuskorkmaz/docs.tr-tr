---
title: 'Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakterleri'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: c6e5fb14e0be277f53511aaddd362f2f203531e8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741191"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="a81f0-102">Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakterleri</span><span class="sxs-lookup"><span data-stu-id="a81f0-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="a81f0-103">Çünkü <xref:System.String> sınıfın uyguladığı genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, bir karakter dizisi herhangi bir dize sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="a81f0-104">Ancak, bu yaygın bir LINQ kullanımı değildir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="a81f0-105">İşlem eşleştirme karmaşık deseni için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a81f0-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81f0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a81f0-106">Example</span></span>  
 <span data-ttu-id="a81f0-107">Aşağıdaki örnek, bir dize içerdiği sayısal basamak sayısını belirlemek için sorgular.</span><span class="sxs-lookup"><span data-stu-id="a81f0-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="a81f0-108">"İlk kez yürütüldükten sonra sorguyu yeniden," unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a81f0-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="a81f0-109">Herhangi bir gerçek sonuç sorgunun kendisi depolamaz mümkün olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a81f0-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a81f0-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a81f0-110">Compiling the Code</span></span>  
 <span data-ttu-id="a81f0-111">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="a81f0-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81f0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a81f0-112">See Also</span></span>

- [<span data-ttu-id="a81f0-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="a81f0-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
- [<span data-ttu-id="a81f0-114">Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="a81f0-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
