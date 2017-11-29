---
title: "Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakter için"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83d83ee9035624a988a3446267e8fc8231e86582
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="3cebb-102">Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakter için</span><span class="sxs-lookup"><span data-stu-id="3cebb-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="3cebb-103">Çünkü <xref:System.String> sınıfı uygulayan genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir dize bir karakter dizisi sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="3cebb-104">Ancak, bu yaygın bir kullanımdır LINQ değildir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="3cebb-105">İşlem eşleştirme karmaşık desen için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3cebb-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cebb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cebb-106">Example</span></span>  
 <span data-ttu-id="3cebb-107">Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemek için bir dize sorgular.</span><span class="sxs-lookup"><span data-stu-id="3cebb-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="3cebb-108">"İlk kez yürütüldükten sonra sorguyu yeniden kullanılacağını" unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3cebb-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="3cebb-109">Bu, sorgu herhangi bir gerçek sonuç depolamaz çünkü mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3cebb-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cebb-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3cebb-110">Compiling the Code</span></span>  
 <span data-ttu-id="3cebb-111">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="3cebb-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cebb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cebb-112">See Also</span></span>  
 [<span data-ttu-id="3cebb-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="3cebb-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="3cebb-114">Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme</span><span class="sxs-lookup"><span data-stu-id="3cebb-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
