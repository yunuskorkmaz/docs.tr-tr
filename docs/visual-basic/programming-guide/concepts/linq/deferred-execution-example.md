---
title: Ertelenmiş Yürütme Örneği
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 863b018b6047d61f6fb4a5c1ac68151ed69d24a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410805"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="7bd14-102">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bd14-102">Deferred Execution Example (Visual Basic)</span></span>

<span data-ttu-id="7bd14-103">Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bd14-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="7bd14-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bd14-104">Example</span></span>

<span data-ttu-id="7bd14-105">Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bd14-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="7bd14-106">Örnek, üç dizeden oluşan bir dizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bd14-106">The example declares an array of three strings.</span></span> <span data-ttu-id="7bd14-107">Daha sonra tarafından döndürülen koleksiyon üzerinden yinelenir `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="7bd14-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>

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

<span data-ttu-id="7bd14-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7bd14-108">This example produces the following output:</span></span>

```console
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

<span data-ttu-id="7bd14-109">Tarafından döndürülen koleksiyonda yineleme yapıldığında `ConvertCollectionToUpperCase` , her öğe kaynak dize dizisinden alınır ve sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="7bd14-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>

<span data-ttu-id="7bd14-110">Döndürülen koleksiyondaki her öğe, içindeki döngüde işlenmeden önce, tüm dizeler dizisinin büyük harfe dönüştürülmediğine bakabilirsiniz `foreach` `Main` .</span><span class="sxs-lookup"><span data-stu-id="7bd14-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bd14-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd14-111">See also</span></span>

- [<span data-ttu-id="7bd14-112">Öğretici: ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bd14-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)
