---
title: Ertelenmiş yürütme örneği-LINQ to XML
description: Ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 59784db895211aecbd263b5ee050734ecd16fa4b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553470"
---
# <a name="deferred-execution-example-linq-to-xml"></a>Ertelenmiş yürütme örneği (LINQ to XML)

Bu makalede, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediği gösterilmektedir.

## <a name="example-use-the-yield-return-construct-in-an-extension-method-to-defer-execution"></a>Örnek: `yield return` yürütmeyi ertelemek için bir genişletme yönteminde yapıyı kullanın

Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir. Örnek, üç dizeden oluşan bir dizi bildirir. Daha sonra tarafından döndürülen koleksiyon üzerinden yinelenir `ConvertCollectionToUpperCase` .

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

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

Tarafından döndürülen koleksiyonda yineleme yapıldığında `ConvertCollectionToUpperCase` , her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.

Döndürülen koleksiyondaki her öğe, içindeki döngüde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz `foreach` `Main` .

## <a name="see-also"></a>Ayrıca bkz.

- [Ertelenmiş yürütme ve geç değerlendirme](deferred-execution-lazy-evaluation.md)
- [Öğretici: birlikte sorgu zinciri (C#)](chain-queries-example.md)
