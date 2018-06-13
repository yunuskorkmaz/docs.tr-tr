---
title: Ertelenmiş yürütme örneği (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 8613f2335e5b3cb2a012f5309307e081b9400709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335932"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="dbd9a-102">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="dbd9a-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="dbd9a-103">Geç değerlendirme, LINQ to XML sorgularını yürütme etkiler ve bu konuda nasıl ertelenmiş yürütme gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbd9a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbd9a-104">Example</span></span>  
 <span data-ttu-id="dbd9a-105">Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="dbd9a-106">Örnek üç bir dizeler dizisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-106">The example declares an array of three strings.</span></span> <span data-ttu-id="dbd9a-107">Ardından tarafından döndürülen koleksiyon üzerinden yineleme `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="dbd9a-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbd9a-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="dbd9a-109">Tarafından döndürülen koleksiyon üzerinden yineleme zaman fark `ConvertCollectionToUpperCase`, her öğe kaynak dize diziden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak dize diziden alınır.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="dbd9a-110">Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizisini büyük harfe dönüştürülmez olduğunu görebilirsiniz `foreach` içinde döngü `Main`.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="dbd9a-111">Bu öğreticide sonraki konu zincirleme sorguları birlikte gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dbd9a-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
-   [<span data-ttu-id="dbd9a-112">Zincirleme sorguları örnek (C#)</span><span class="sxs-lookup"><span data-stu-id="dbd9a-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="dbd9a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbd9a-113">See Also</span></span>  
 [<span data-ttu-id="dbd9a-114">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="dbd9a-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
