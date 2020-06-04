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
# <a name="deferred-execution-example-visual-basic"></a>Ertelenmiş yürütme örneği (Visual Basic)

Bu konu, ertelenmiş yürütmenin ve yavaş değerlendirmenin LINQ to XML sorgularının yürütülmesini nasıl etkilediğini gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, ertelenmiş yürütmeyi kullanan bir genişletme yöntemi kullanılırken yürütme sırasını gösterir. Örnek, üç dizeden oluşan bir dizi bildirir. Daha sonra tarafından döndürülen koleksiyon üzerinden yinelenir `ConvertCollectionToUpperCase` .

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

```console
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

- [Öğretici: ertelenmiş yürütme (Visual Basic)](tutorial-deferred-execution.md)
