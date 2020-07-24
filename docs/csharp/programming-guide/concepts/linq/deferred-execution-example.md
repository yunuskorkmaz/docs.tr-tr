---
title: Ertelenmiş yürütme örneği (C#)
description: Ertelenmiş yürütme ve yavaş değerlendirmenin C# ' de LINQ to XML sorgularının yürütülmesini nasıl etkilediğini görün.
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 65ba4cc150f2fc9d8f44aee352987ea0eeaab0a5
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103957"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="aa456-103">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="aa456-103">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="aa456-104">Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa456-104">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa456-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa456-105">Example</span></span>  
 <span data-ttu-id="aa456-106">Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa456-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="aa456-107">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa456-107">The example declares an array of three strings.</span></span> <span data-ttu-id="aa456-108">Daha sonra tarafından döndürülen koleksiyon üzerinden yinelenir `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="aa456-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="aa456-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa456-109">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="aa456-110">Tarafından döndürülen koleksiyonda yineleme yapıldığında `ConvertCollectionToUpperCase` , her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="aa456-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="aa456-111">Döndürülen koleksiyondaki her öğe, içindeki döngüde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz `foreach` `Main` .</span><span class="sxs-lookup"><span data-stu-id="aa456-111">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="aa456-112">Bu öğreticideki sonraki konu, zincirleme sorguları birlikte gösterir:</span><span class="sxs-lookup"><span data-stu-id="aa456-112">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="aa456-113">Zincirleme sorguları örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="aa456-113">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa456-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa456-114">See also</span></span>

- [<span data-ttu-id="aa456-115">Öğretici: sorguları birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="aa456-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
