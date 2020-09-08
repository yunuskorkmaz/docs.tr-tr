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
# <a name="intermediate-materialization-c"></a>Ara gerçekleştirmesi (C#)

Bazı durumlarda, Sorgularınızdaki koleksiyonların erken olarak başlatılmasına neden olacak şekilde uygulamanızın bellek ve performans profilini büyük ölçüde değiştirin. Bazı standart sorgu işleçleri, tek bir öğeyi oluşturmadan önce kaynak koleksiyonlarının çalışmasının oluşturulmasına neden olur. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> ilk olarak tüm kaynak koleksiyonu boyunca yinelenir, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir. Bu, sıralı bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; Bundan sonra her öğe pahalı değildir. Bu anlamlı olur: Bu sorgu işlecinin başka bir şekilde yapması imkansız olabilir.

## <a name="example-add-a-method-that-calls-tolist-causing-materialization"></a>Örnek: çağıran bir yöntem ekleyin `ToList` , bu, gerçekleştirmesi 'e neden olur

Bu örnek, [zincir sorguları örneği (C#)](chain-queries-example.md)içindeki örneği değiştirir: `AppendString` Yöntem, <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinde yinelenirken, bu da materialization oluşturulmasına neden olacak şekilde değiştirilir.

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

 Bu örnek aşağıdaki çıktıyı üretir:

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

Bu örnekte, çağrısının <xref:System.Linq.Enumerable.ToList%2A> `AppendString` ilk öğeyi bırakmadan önce tüm kaynağını numaralandırmasına neden olduğunu görebilirsiniz. Kaynak büyük bir diziyse, bu, uygulamanın bellek profilini önemli ölçüde değiştirecek.

Standart sorgu işleçleri de Bu öğreticinin son makalesinde gösterildiği gibi birbirine zincirleme uygulanabilir:

- [Standart sorgu işleçleri birlikte zinciri (C#)](chain-standard-query-operators-together.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş yürütme ve geç değerlendirme](deferred-execution-lazy-evaluation.md)
