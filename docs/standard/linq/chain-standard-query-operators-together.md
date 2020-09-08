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
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a>Standart sorgu işleçleri birlikte zinciri (C#) (LINQ to XML)

Standart sorgu işleçleri birlikte zincirlenebilir. Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işlecini (yan tümce tarafından çağrılır) birbirine bağlayabilirsiniz `where` ve geç bir biçimde çalışır; yani, hiçbir ara sonuç tarafından gerçekleştirilmediği anlamına gelir.

## <a name="example-interject-a-where-clause"></a>Örnek: ınterject a WHERE yan tümcesi

Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan önce çağrılır `ConvertCollectionToUpperCase` . <xref:System.Linq.Enumerable.Where%2A>Yöntemi, bu öğreticideki önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır `ConvertCollectionToUpperCase` `AppendString` .

Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> yöntemin kaynak koleksiyonu aracılığıyla yineleme, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır. Daha sonra ikinci öğeyi verir.

Bununla birlikte, temel düşünce aynıdır: ara koleksiyonlar olması gerekmediği takdirde bu şekilde gerçekleştirilmiş değildir.

Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçleri çağrılarına dönüştürülür ve aynı ilkeler geçerlidir.

Bu bölümdeki Office Open XML belgelerini sorgulayan tüm örnekler aynı ilkeyi kullanır. Ertelenmiş yürütme ve yavaş değerlendirme, LINQ ve LINQ to XML verimli bir şekilde kullanmak için anlamanız gereken temel kavramlardır.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

Bu, öğreticideki son makaledir [: sorguları birbirine bağlama (C#)](chain-queries-example.md) öğreticisi.
