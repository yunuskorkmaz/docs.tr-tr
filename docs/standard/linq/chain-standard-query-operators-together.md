---
title: Standart sorgu işleçlerini birlikte zinciri (C#)-LINQ to XML
description: Sorgu işleçlerini birlikte nasıl zincirleyeceğinizi öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552907"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a><span data-ttu-id="25ac5-103">Standart sorgu işleçleri birlikte zinciri (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="25ac5-103">Chain standard query operators together (C#) (LINQ to XML)</span></span>

<span data-ttu-id="25ac5-104">Standart sorgu işleçleri birlikte zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="25ac5-104">The standard query operators can be chained together.</span></span> <span data-ttu-id="25ac5-105">Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işlecini (yan tümce tarafından çağrılır) birbirine bağlayabilirsiniz `where` ve geç bir biçimde çalışır; yani, hiçbir ara sonuç tarafından gerçekleştirilmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="25ac5-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator (invoked by the `where` clause), and it operates in a lazy fashion; that is, no intermediate results are materialized by it.</span></span>

## <a name="example-interject-a-where-clause"></a><span data-ttu-id="25ac5-106">Örnek: ınterject a WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="25ac5-106">Example: Interject a where clause</span></span>

<span data-ttu-id="25ac5-107">Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan önce çağrılır `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="25ac5-107">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="25ac5-108"><xref:System.Linq.Enumerable.Where%2A>Yöntemi, bu öğreticideki önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır `ConvertCollectionToUpperCase` `AppendString` .</span><span class="sxs-lookup"><span data-stu-id="25ac5-108">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>

<span data-ttu-id="25ac5-109">Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> yöntemin kaynak koleksiyonu aracılığıyla yineleme, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="25ac5-109">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item doesn't pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="25ac5-110">Daha sonra ikinci öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="25ac5-110">It then yields the second item.</span></span>

<span data-ttu-id="25ac5-111">Bununla birlikte, temel düşünce aynıdır: ara koleksiyonlar olması gerekmediği takdirde bu şekilde gerçekleştirilmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="25ac5-111">However, the basic idea is the same: intermediate collections aren't materialized unless they have to be.</span></span>

<span data-ttu-id="25ac5-112">Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçleri çağrılarına dönüştürülür ve aynı ilkeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25ac5-112">When query expressions are used, they're converted to calls to the standard query operators, and the same principles apply.</span></span>

<span data-ttu-id="25ac5-113">Bu bölümdeki Office Open XML belgelerini sorgulayan tüm örnekler aynı ilkeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="25ac5-113">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="25ac5-114">Ertelenmiş yürütme ve yavaş değerlendirme, LINQ ve LINQ to XML verimli bir şekilde kullanmak için anlamanız gereken temel kavramlardır.</span><span class="sxs-lookup"><span data-stu-id="25ac5-114">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand to use LINQ, and LINQ to XML, effectively.</span></span>

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

<span data-ttu-id="25ac5-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="25ac5-115">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="25ac5-116">Bu, öğreticideki son makaledir [: sorguları birbirine bağlama (C#)](chain-queries-example.md) öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="25ac5-116">This is the final article in the [Tutorial: Chaining Queries Together (C#)](chain-queries-example.md) tutorial.</span></span>
