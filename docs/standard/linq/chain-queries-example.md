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
# <a name="chain-queries-example-c-linq-to-xml"></a>Zincir sorguları örneği (C#) (LINQ to XML)

Bu örnek, [ertelenmiş yürütme örneğinde](deferred-execution-example.md) örneği oluşturur ve her ikisi de ertelenmiş yürütme ve yavaş değerlendirme kullanan iki sorguyu zincirleyen ne olacağını gösterir.

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a>Örnek: `yield return` yürütmeyi ertelemek için kullanan ikinci bir genişletme yöntemi ekleyin

Bu örnekte, `AppendString` belirtilen bir dizeyi kaynak koleksiyondaki her dizeye bağlayan ve ardından değiştirilen dizeyi veren başka bir genişletme yöntemi tanıtılmıştır.

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

 Bu örnek aşağıdaki çıktıyı üretir:

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

Bu örnekte, her bir genişletme yönteminin, kaynak koleksiyondaki her öğe için tek bir kez çalıştığını görebilirsiniz.

Bu örnekte ne kadar net bir şekilde gruplandık, ancak koleksiyonları oluşturan sorguları birbirine zincirlediğimiz halde ara koleksiyonlar gerçekleştirilmiş değildir. Bunun yerine, her öğe bir geç yönteminden bir sonrakine geçirilir. Bu, ilk olarak bir dize dizisi alacak bir yaklaşımdan çok daha küçük bir bellek parmak izine neden olur, ardından büyük harfe dönüştürülmüş ikinci bir dize dizisi oluşturur ve son olarak her bir dizenin kendisine eklenmiş ünlem noktaları olan bir dizi dizeden oluşur.

Bu öğreticideki sonraki makalede ara materialization gösterilmektedir:

- [Ara gerçekleştirmesi (C#)](intermediate-materialization.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş yürütme ve geç değerlendirme](deferred-execution-lazy-evaluation.md)
