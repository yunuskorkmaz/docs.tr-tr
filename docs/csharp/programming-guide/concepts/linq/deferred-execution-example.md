---
title: Ertelenmiş yürütme örneği (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: a934645d0d7ad807e1524031ca3f023f7b11c5b4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594550"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="1b2fd-102">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="1b2fd-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="1b2fd-103">Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b2fd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b2fd-104">Example</span></span>  
 <span data-ttu-id="1b2fd-105">Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="1b2fd-106">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-106">The example declares an array of three strings.</span></span> <span data-ttu-id="1b2fd-107">Daha sonra tarafından `ConvertCollectionToUpperCase`döndürülen koleksiyon üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="1b2fd-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1b2fd-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="1b2fd-109">Tarafından `ConvertCollectionToUpperCase`döndürülen koleksiyonda yineleme yapıldığında, her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="1b2fd-110">Döndürülen koleksiyondaki her öğe, içindeki `foreach` `Main`döngüde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="1b2fd-111">Bu öğreticideki sonraki konu, zincirleme sorguları birlikte gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b2fd-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="1b2fd-112">Zincirleme sorguları örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="1b2fd-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b2fd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b2fd-113">See also</span></span>

- [<span data-ttu-id="1b2fd-114">Öğretici: Sorguları birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="1b2fd-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
