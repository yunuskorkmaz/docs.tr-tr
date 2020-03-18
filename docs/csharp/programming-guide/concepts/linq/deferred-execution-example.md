---
title: Ertelenmiş Yürütme Örneği (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204127"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="96456-102">Ertelenmiş Yürütme Örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="96456-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="96456-103">Bu konu, ertelenmiş yürütme ve tembel değerlendirmenin LINQ'nizin XML sorgularına yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="96456-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96456-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="96456-104">Example</span></span>  
 <span data-ttu-id="96456-105">Aşağıdaki örnekte, ertelenmiş yürütme kullanan bir uzantı yöntemi kullanırken yürütme sırasını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="96456-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="96456-106">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="96456-106">The example declares an array of three strings.</span></span> <span data-ttu-id="96456-107">Daha sonra tarafından `ConvertCollectionToUpperCase`döndürülen koleksiyon aracılığıyla iterates .</span><span class="sxs-lookup"><span data-stu-id="96456-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="96456-108">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="96456-108">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="96456-109">Döndürülen koleksiyonda `ConvertCollectionToUpperCase`yinelendiğinde, her öğekaynak dize dizisinden alınır ve bir sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="96456-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="96456-110">Döndürülen koleksiyondaki her öğe `foreach` döngü içinde `Main`işlenmeden önce dizeleri tüm dizi büyük harfe dönüştürülür olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96456-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="96456-111">Bu öğreticideki bir sonraki konu, sorguları birbirine zincirlemeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="96456-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="96456-112">Zincirleme Sorgular Örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="96456-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="96456-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96456-113">See also</span></span>

- [<span data-ttu-id="96456-114">Öğretici: Sorguları Birlikte Zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="96456-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
