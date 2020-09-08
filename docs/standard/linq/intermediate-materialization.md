---
title: Ara gerçekleştirmesi (C#)
description: Bazı standart sorgu işleçlerinin kullanımını bir sorgudaki koleksiyonların çalışmasının oluşturulmasına neden olabileceğini ve uygulamanızın bellek ve performans profilini büyük ölçüde değiştirmesini öğrenin.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 8dca4bb29886973762351049d06bcf5d3ba352db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552962"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="e46fe-103">Ara gerçekleştirmesi (C#)</span><span class="sxs-lookup"><span data-stu-id="e46fe-103">Intermediate materialization (C#)</span></span>

<span data-ttu-id="e46fe-104">Bazı durumlarda, Sorgularınızdaki koleksiyonların erken olarak başlatılmasına neden olacak şekilde uygulamanızın bellek ve performans profilini büyük ölçüde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e46fe-104">If you're not careful you can, in some situations, drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="e46fe-105">Bazı standart sorgu işleçleri, tek bir öğeyi oluşturmadan önce kaynak koleksiyonlarının çalışmasının oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e46fe-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="e46fe-106">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> ilk olarak tüm kaynak koleksiyonu boyunca yinelenir, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="e46fe-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="e46fe-107">Bu, sıralı bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; Bundan sonra her öğe pahalı değildir.</span><span class="sxs-lookup"><span data-stu-id="e46fe-107">This means that it's expensive to get the first item of an ordered collection; each item thereafter isn't expensive.</span></span> <span data-ttu-id="e46fe-108">Bu anlamlı olur: Bu sorgu işlecinin başka bir şekilde yapması imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e46fe-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a><span data-ttu-id="e46fe-109">Örnek: çağıran bir yöntem ekleyin `ToList` , bu, gerçekleştirmesi 'e neden olur</span><span class="sxs-lookup"><span data-stu-id="e46fe-109">Example: Add a method that calls `ToList`, causing materialization</span></span>

<span data-ttu-id="e46fe-110">Bu örnek, [zincir sorguları örneği (C#)](chain-queries-example.md)içindeki örneği değiştirir: `AppendString` Yöntem, <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinde yinelenirken, bu da materialization oluşturulmasına neden olacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e46fe-110">This example alters the example in [Chain queries example (C#)](chain-queries-example.md): the `AppendString` method is changed to call <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source, which causes materialization.</span></span>

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
        // the following statement materializes the source collection in a List<T>
        // before iterating through it
        foreach (string str in source.ToList())
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

 <span data-ttu-id="e46fe-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e46fe-111">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
ToUpper: source >def<
ToUpper: source >ghi<
AppendString: source >ABC<
Main: str >ABC!!!<

AppendString: source >DEF<
Main: str >DEF!!!<

AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="e46fe-112">Bu örnekte, çağrısının <xref:System.Linq.Enumerable.ToList%2A> `AppendString` ilk öğeyi bırakmadan önce tüm kaynağını numaralandırmasına neden olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e46fe-112">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="e46fe-113">Kaynak büyük bir diziyse, bu, uygulamanın bellek profilini önemli ölçüde değiştirecek.</span><span class="sxs-lookup"><span data-stu-id="e46fe-113">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>

<span data-ttu-id="e46fe-114">Standart sorgu işleçleri de Bu öğreticinin son makalesinde gösterildiği gibi birbirine zincirleme uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="e46fe-114">Standard query operators can also be chained together as shown in the final article in this tutorial:</span></span>

- [<span data-ttu-id="e46fe-115">Standart sorgu işleçleri birlikte zinciri (C#)</span><span class="sxs-lookup"><span data-stu-id="e46fe-115">Chain standard query operators together (C#)</span></span>](chain-standard-query-operators-together.md)

## <a name="see-also"></a><span data-ttu-id="e46fe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e46fe-116">See also</span></span>

- [<span data-ttu-id="e46fe-117">Ertelenmiş yürütme ve geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="e46fe-117">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
