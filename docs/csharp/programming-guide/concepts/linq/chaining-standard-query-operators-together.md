---
title: Standart sorgu Işleçlerini birlikte zincirleme (C#)
description: Bu örnek, standart sorgu işleçlerinin C# ' de nasıl bir araya gruplanmakta olduğunu gösterir. Sorgu, ara sonuçları etkilemez.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104074"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="484b6-104">Standart sorgu Işleçlerini birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="484b6-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="484b6-105">Bu, [öğreticideki son konudur: sorguları birbirine bağlama (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="484b6-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="484b6-106">Standart sorgu işleçleri de birlikte zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="484b6-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="484b6-107">Örneğin, işlecini birbirine bağlayabilirsiniz <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> ve aynı zamanda bir geç şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="484b6-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="484b6-108">Hiçbir ara sonuç tarafından gerçekleştirilmeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="484b6-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="484b6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="484b6-109">Example</span></span>  
 <span data-ttu-id="484b6-110">Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan önce çağrılır `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="484b6-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="484b6-111"><xref:System.Linq.Enumerable.Where%2A>Yöntemi, bu öğreticideki önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır `ConvertCollectionToUpperCase` `AppendString` .</span><span class="sxs-lookup"><span data-stu-id="484b6-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="484b6-112">Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> Yöntem kaynak koleksiyonu aracılığıyla yinelenir, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="484b6-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="484b6-113">Daha sonra ikinci öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="484b6-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="484b6-114">Bununla birlikte, temel düşünce aynıdır: ara koleksiyonlar olması gerekmediği müddetçe bu şekilde gerçekleştirilmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="484b6-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="484b6-115">Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçleri çağrılarına dönüştürülür ve aynı ilkeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="484b6-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="484b6-116">Bu bölümdeki Office Open XML belgelerini sorgulayan tüm örnekler aynı ilkeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="484b6-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="484b6-117">Ertelenmiş yürütme ve yavaş değerlendirme, LINQ (ve LINQ to XML) etkin bir şekilde kullanmak için anlamanız gereken temel kavramlardır.</span><span class="sxs-lookup"><span data-stu-id="484b6-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="484b6-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="484b6-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
