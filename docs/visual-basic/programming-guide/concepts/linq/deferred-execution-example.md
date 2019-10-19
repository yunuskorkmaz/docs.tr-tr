---
title: Ertelenmiş yürütme örneği (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: e0bb7f3d125cc48607a534e2c24cbf7083353945
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583326"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="41eab-102">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41eab-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="41eab-103">Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="41eab-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="41eab-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="41eab-104">Example</span></span>

<span data-ttu-id="41eab-105">Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41eab-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="41eab-106">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="41eab-106">The example declares an array of three strings.</span></span> <span data-ttu-id="41eab-107">Daha sonra `ConvertCollectionToUpperCase` tarafından döndürülen koleksiyon üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="41eab-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

<span data-ttu-id="41eab-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41eab-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="41eab-109">@No__t_0 tarafından döndürülen koleksiyon üzerinden yineleme yaparken, her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="41eab-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="41eab-110">Döndürülen koleksiyondaki her öğe, `Main` `foreach` döngüsünde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41eab-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="41eab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41eab-111">See also</span></span>

- [<span data-ttu-id="41eab-112">Öğretici: ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41eab-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
