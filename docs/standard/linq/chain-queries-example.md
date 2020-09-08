---
title: Zincir sorguları örneği (C#)-LINQ to XML
description: Her ikisinin de ertelenmiş yürütme ve yavaş değerlendirme kullanan iki sorgu üzerinde zincir haline geldiklerinde ne olacağını öğrenin.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553493"
---
# <a name="chain-queries-example-c-linq-to-xml"></a><span data-ttu-id="5a83c-103">Zincir sorguları örneği (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5a83c-103">Chain queries example (C#) (LINQ to XML)</span></span>

<span data-ttu-id="5a83c-104">Bu örnek, [ertelenmiş yürütme örneğinde](deferred-execution-example.md) örneği oluşturur ve her ikisi de ertelenmiş yürütme ve yavaş değerlendirme kullanan iki sorguyu zincirleyen ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a83c-104">This example builds on the example in [Deferred execution example](deferred-execution-example.md) and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a><span data-ttu-id="5a83c-105">Örnek: `yield return` yürütmeyi ertelemek için kullanan ikinci bir genişletme yöntemi ekleyin</span><span class="sxs-lookup"><span data-stu-id="5a83c-105">Example: Add a second extension method that uses `yield return` to defer execution</span></span>

<span data-ttu-id="5a83c-106">Bu örnekte, `AppendString` belirtilen bir dizeyi kaynak koleksiyondaki her dizeye bağlayan ve ardından değiştirilen dizeyi veren başka bir genişletme yöntemi tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a83c-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the changed string.</span></span>

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

 <span data-ttu-id="5a83c-107">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5a83c-107">This example produces the following output:</span></span>

```output
ToUpper: source >abc<
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

<span data-ttu-id="5a83c-108">Bu örnekte, her bir genişletme yönteminin, kaynak koleksiyondaki her öğe için tek bir kez çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a83c-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>

<span data-ttu-id="5a83c-109">Bu örnekte ne kadar net bir şekilde gruplandık, ancak koleksiyonları oluşturan sorguları birbirine zincirlediğimiz halde ara koleksiyonlar gerçekleştirilmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="5a83c-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="5a83c-110">Bunun yerine, her öğe bir geç yönteminden bir sonrakine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5a83c-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="5a83c-111">Bu, ilk olarak bir dize dizisi alacak bir yaklaşımdan çok daha küçük bir bellek parmak izine neden olur, ardından büyük harfe dönüştürülmüş ikinci bir dize dizisi oluşturur ve son olarak her bir dizenin kendisine eklenmiş ünlem noktaları olan bir dizi dizeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a83c-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>

<span data-ttu-id="5a83c-112">Bu öğreticideki sonraki makalede ara materialization gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5a83c-112">The next article in this tutorial illustrates intermediate materialization:</span></span>

- [<span data-ttu-id="5a83c-113">Ara gerçekleştirmesi (C#)</span><span class="sxs-lookup"><span data-stu-id="5a83c-113">Intermediate materialization (C#)</span></span>](intermediate-materialization.md)

## <a name="see-also"></a><span data-ttu-id="5a83c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a83c-114">See also</span></span>

- [<span data-ttu-id="5a83c-115">Ertelenmiş yürütme ve geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="5a83c-115">Deferred execution and lazy evaluation</span></span>](deferred-execution-lazy-evaluation.md)
